---
ms.assetid: 46725afe-8652-4cd7-928c-93b98f7fbae3
title: 创建不具有域管理员权限的 AD FS 场
description: 使用 Install-adfsfarm cmdlet 和脚本通过委派的管理员凭据创建 AD FS 场
author: billmath
ms.author: billmath
manager: daveba
ms.date: 04/01/2020
ms.topic: article
ms.openlocfilehash: 7dff0b19b4d8783dcd43344c6152be9d2c36441d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972184"
---
# <a name="creating-an-ad-fs-farm-without-domain-admin-privileges"></a>创建不具有域管理员权限的 AD FS 场

>适用于： Windows Server 2019 和2016

## <a name="overview"></a>概述
从 Windows Server 2016 中的 AD FS 开始，你可以在联合服务器上以本地管理员身份运行 cmdlet Install-adfsfarm，前提是你的域管理员已准备好 Active Directory。  本文中的脚本可用于准备 AD。  步骤如下：

1) 作为域管理员，运行脚本 (或手动创建 Active Directory 对象和权限) 。
2) 脚本将返回一个 AdminConfiguration 对象，该对象包含新创建的 AD 对象的 DN
3) 在联合服务器上，在以本地管理员身份登录的情况下执行 Install-adfsfarm cmdlet，并将该对象从上述 #2 传递为 AdminConfiguration 参数

## <a name="assumptions"></a>假设
- Contoso\localadmin 是联合服务器上的非域管理员内置管理员
- Contoso\FsSvcAcct 是将成为 AD FS 服务帐户的域帐户
- Contoso\FsGmsaAcct $ 是将成为 AD FS 服务帐户的 gMSA 帐户
- $svcCred 是 AD FS 服务帐户的凭据
- $localAdminCred 是联合服务器上的本地 (非 DA) 管理员帐户的凭据

## <a name="using-a-domain-account-as-ad-fs-service-account"></a>使用域帐户作为 AD FS 服务帐户
### <a name="prepare-ad"></a>准备 AD
以域管理员身份运行以下
```
PS:\>$adminConfig=(.\New-AdfsDkmContainer.ps1 -ServiceAccount contoso\fssvcacct -AdfsAdministratorAccount contoso\localadmin)
```
### <a name="sample-output"></a>示例输出
```
$adminconfig.DkmContainerDN
CN=9530440c-bc84-4fe6-a3f9-8d60162a7bcf,CN=ADFS,CN=Microsoft,CN=Program Data,DC=contoso,DC=com
```
### <a name="create-the-ad-fs-farm"></a>创建 AD FS 场
在联合服务器上作为本地管理员，在提升的 PowerShell 命令窗口中执行以下命令。

首先，如果联合服务器管理员未使用与上述域管理员相同的 PowerShell 会话，请使用上述的输出重新创建 Adminconfig.ps1 对象。
```
PS:\>$adminConfig = @{"DKMContainerDn"="CN=9530440c-bc84-4fe6-a3f9-8d60162a7bcf,CN=ADFS,CN=Microsoft,CN=Program Data,DC=contoso,DC=com"}
```

接下来，创建场：
```
PS:\>$svcCred = (get-credential)
PS:\>$localAdminCred = (get-credential)
PS:\>Install-AdfsFarm -CertificateThumbprint 270D041785C579D75C1C981DA0F9C36ECFDB65E0 -FederationServiceName "fs.contoso.com" -ServiceAccountCredential $svcCred -Credential $localAdminCred -OverwriteConfiguration -AdminConfiguration $adminConfig -Verbose
```
## <a name="using-a-gmsa-as-the-ad-fs-service-account"></a>使用 gMSA 作为 AD FS 服务帐户
### <a name="prepare-ad"></a>准备 AD
```
PS:\>$adminConfig=(.\New-AdfsDkmContainer.ps1 -ServiceAccount contoso\FsGmsaAcct$ -AdfsAdministratorAccount contoso\localadmin)
```

### <a name="sample-output"></a>示例输出
```
$adminconfig.DkmContainerDN
CN=8065f653-af9d-42ff-aec8-56e02be4d5f3,CN=ADFS,CN=Microsoft,CN=Program Data,DC=contoso,DC=com
```

### <a name="create-the-ad-fs-farm"></a>创建 AD FS 场
在联合服务器上作为本地管理员，在提升的 PowerShell 命令窗口中执行以下命令。

首先，如果联合服务器管理员未使用与上述域管理员相同的 PowerShell 会话，请使用上述的输出重新创建 Adminconfig.ps1 对象。
```
PS:\>$adminConfig = @{"DKMContainerDn"="CN=8065f653-af9d-42ff-aec8-56e02be4d5f3,CN=ADFS,CN=Microsoft,CN=Program Data,DC=contoso,DC=com"}
```

接下来，创建场：请注意，需要为本地计算机帐户和 ADFS 管理员帐户授予对 gMSA 的 "检索密码" 和 "委派到帐户" 权限。
```
PS:\>$localadminobj = get-aduser "localadmin"
PS:\>$adfsnodecomputeracct = get-adcomputer "contoso_adfs_node"
PS:\>Set-ADServiceAccount -Identity fsgmsaacct -PrincipalsAllowedToRetrieveManagedPassword @( add=$localadmin.sid.value, $computeracct.sid.value) -PrincipalsAllowedToDelegateToAccount @( add=$localadmin.sid.value, $computeracct.sid.value)
PS:\>$localAdminCred = (get-credential)
PS:\>Install-AdfsFarm -CertificateThumbprint 270D041785C579D75C1C981DA0F9C36ECFDB65E0 -FederationServiceName "fs.contoso.com" -Credential $localAdminCred -GroupServiceAccountIdentifier "contoso\fsgmsaacct$" -OverwriteConfiguration -AdminConfiguration $adminConfig
```

## <a name="script-for-preparing-ad"></a>用于准备 AD 的脚本
下面的 PowerShell 脚本可用于完成上述示例

```
[CmdletBinding(SupportsShouldProcess=$true)]
param (
   [Parameter(Mandatory=$True)]
   [string]$ServiceAccount,
   [Parameter(Mandatory=$True)]
   [string]$AdfsAdministratorAccount
)

$ServiceAccountSplit = $ServiceAccount.Split("\");
if ($ServiceAccountSplit.Length -ne 2)
{
    Write-error "Specify the ServiceAccount identifier in 'domain\username' format"
    exit 1
}

$AdfsAdministratorAccountSplit = $AdfsAdministratorAccount.Split("\");
if ($AdfsAdministratorAccountSplit.Length -ne 2)
{
    Write-error "Specify the AdfsAdministratorAccount identifier in 'domain\username' format"
    exit 1
}

#######################################
## Verify AD module is installed
#######################################
$m = "ActiveDirectory"
if (Get-Module | Where-Object {$_.Name -eq $m})
{
    write-verbose "Module $m is already imported."
}
else
{
    if (Get-Module -ListAvailable | Where-Object {$_.Name -eq $m})
    {
        Import-Module $m -Verbose
    }
    else
    {
        write-error "Module $m was not imported, install the Active Directory RSAT package and retry."
        exit 1
    }
}

push-location ad:

#######################################
## Generate random DKM container name
## The OU Name is a randomly generated Guid
#######################################
[string]$guid = [Guid]::NewGuid()
write-verbose ("OU Name" + $guid)

$ouName = $guid
$initialPath = "CN=Microsoft,CN=Program Data," + (Get-ADDomain).DistinguishedName
$ouPath = "CN=ADFS," + $initialPath
$ou = "CN=" + $ouName + "," + $ouPath

#######################################
## Create DKM container and assign default ACE which allows adfs admin read access
#######################################

if ($pscmdlet.ShouldProcess("$ou", "Creating DKM container and assinging access"))
{
    Write-Verbose ("Creating organizational unit with DN: " + $ou)

    if ($AdfsAdministratorAccount.EndsWith("$"))
    {
        write-verbose "ADFS administrator account passed with $ suffix indicating a computer account"
        $userNameSplit = $AdfsAdministratorAccount.Split("\");
        $strSID = (Get-ADServiceAccount -Identity $userNameSplit[1]).SID
    }
    else
    {
        write-verbose "ADFS administrator account is a standard AD user"
        $objUser = New-Object System.Security.Principal.NTAccount($AdfsAdministratorAccount)
        $strSID = $objUser.Translate([System.Security.Principal.SecurityIdentifier])
    }

    if ($null -eq (Get-ADObject -Filter {distinguishedName -eq $ouPath}))
    {
        Write-Verbose ("First creating initial path " + $ouPath)
        New-ADObject -Name "ADFS" -Type Container -Path $initialPath
    }

    $acl = get-acl -Path $ouPath
    [System.DirectoryServices.ActiveDirectorySecurityInheritance]$adSecInEnum = [System.DirectoryServices.ActiveDirectorySecurityInheritance]::All
    $ace1 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"GenericRead","Allow",$adSecInEnum

    $acl.AddAccessRule($ace1)
    set-acl -Path $ouPath -AclObject $acl

    New-ADObject -Name $ouName -Type Container -Path $ouPath
}


#######################################
## Grant the following permission to the service account
# Read
# Create Child
# Write Owner
# Delete Tree
# Write DACL
# Write Property
#######################################
if ($ServiceAccount.EndsWith("$"))
{
    write-verbose "service account passed with $ suffix indicating a gMSA"
    $userNameSplit = $ServiceAccount.Split("\");
    $strSID = (Get-ADServiceAccount -Identity $userNameSplit[1]).SID
}
else
{
    write-verbose "service account is a standard AD user"
    $objUser = New-Object System.Security.Principal.NTAccount($ServiceAccount)
    $strSID = $objUser.Translate([System.Security.Principal.SecurityIdentifier])
}

if ($pscmdlet.ShouldProcess("$strSID", "Granting GenericRead, CreateChild, WriteOwner, DeleteTree, WriteDacl and WriteProperty"))
{
    [System.DirectoryServices.ActiveDirectorySecurityInheritance]$adSecInEnum = [System.DirectoryServices.ActiveDirectorySecurityInheritance]::All
    $ace1 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"GenericRead","Allow",$adSecInEnum
    $ace2 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"CreateChild","Allow",$adSecInEnum
    $ace3 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"WriteOwner","Allow",$adSecInEnum
    $ace4 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"DeleteTree","Allow",$adSecInEnum
    $ace5 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"WriteDacl","Allow",$adSecInEnum
    $ace6 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"WriteProperty","Allow",$adSecInEnum

    $acl = get-acl -Path $ou

    $acl.AddAccessRule($ace1)
    $acl.AddAccessRule($ace2)
    $acl.AddAccessRule($ace3)
    $acl.AddAccessRule($ace4)
    $acl.AddAccessRule($ace5)
    $acl.AddAccessRule($ace6)

    $acl.SetOwner($strSID)

    set-acl -Path $ou -AclObject $acl
}

#######################################
## Grant the following permission to the adfs admin account
# Read
# Create Child
# Write Owner
# Delete Tree
# Write DACL
# Write Property
#######################################

if ($AdfsAdministratorAccount.EndsWith("$"))
{
    write-verbose "ADFS administrator account passed with $ suffix indicating a gMSA"
    $userNameSplit = $AdfsAdministratorAccount.Split("\");
    $strSID = (Get-ADServiceAccount -Identity $userNameSplit[1]).SID
}
else
{
    write-verbose "ADFS administrator account is a standard AD user"
    $objUser = New-Object System.Security.Principal.NTAccount($AdfsAdministratorAccount)
    $strSID = $objUser.Translate([System.Security.Principal.SecurityIdentifier])
}

if ($pscmdlet.ShouldProcess("$strSID", "Granting GenericRead, CreateChild, WriteOwner, DeleteTree, WriteDacl and WriteProperty"))
{
    [System.DirectoryServices.ActiveDirectorySecurityInheritance]$adSecInEnum = [System.DirectoryServices.ActiveDirectorySecurityInheritance]::All
    $ace1 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"GenericRead","Allow",$adSecInEnum
    $ace2 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"CreateChild","Allow",$adSecInEnum
    $ace3 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"WriteOwner","Allow",$adSecInEnum
    $ace4 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"DeleteTree","Allow",$adSecInEnum
    $ace5 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"WriteDacl","Allow",$adSecInEnum
    $ace6 = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $strSID,"WriteProperty","Allow",$adSecInEnum

    $acl = get-acl -Path $ou

    $acl.AddAccessRule($ace1)
    $acl.AddAccessRule($ace2)
    $acl.AddAccessRule($ace3)
    $acl.AddAccessRule($ace4)
    $acl.AddAccessRule($ace5)
    $acl.AddAccessRule($ace6)

    $acl.SetOwner($strSID)

    set-acl -Path $ou -AclObject $acl

    $adminConfig = @{"DKMContainerDn"=$ou}

    Write-Output $adminConfig
}

pop-location

```
