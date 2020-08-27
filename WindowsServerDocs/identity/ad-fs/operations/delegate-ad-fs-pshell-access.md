---
title: 向非管理员用户委派 AD FS Powershell Commandlet 访问权限
description: 本文档 descirbes 了如何将权限委派给 AD FS PowerShell cmdlt 的非管理员。
author: billmath
ms.author: billmath
manager: daveba
ms.reviewer: zhvolosh
ms.date: 01/31/2019
ms.topic: article
ms.openlocfilehash: 836a40ffa9df8fa308d1005fbac3a9e087488949
ms.sourcegitcommit: 52a8d5d7e969eaa07fd3a45ed6d3cb5a5173b6d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "88970624"
---
# <a name="delegate-ad-fs-powershell-commandlet-access-to-non-admin-users"></a>向非管理员用户委派 AD FS Powershell Commandlet 访问权限
默认情况下，通过 PowerShell AD FS 管理只能由 AD FS 管理员完成。 对于许多大型组织而言，处理其他角色（如技术支持人员）时，这可能不是可行的操作模型。

通过足够的管理 (JEA) ，客户现在可以将特定 commandlet 委托给不同的人员组。
这种用例的一个很好的示例是，在审查用户之后，支持咨询台人员查询 AD FS 帐户锁定状态并在 AD FS 中重置帐户锁定状态。 在这种情况下，需要委派的 commandlet 是：
- `Get-ADFSAccountActivity`
- `Set-ADFSAccountActivity`
- `Reset-ADFSAccountLockout`

本文档的其余部分使用本示例。 但是，可以对此进行自定义，以允许委托设置信赖方的属性，并将其交给组织内的应用程序所有者。


##  <a name="create-the-required-groups-necessary-to-grant-users-permissions"></a>创建向用户授予权限所需的必要组
1. 创建 [组托管服务帐户](../../../security/group-managed-service-accounts/group-managed-service-accounts-overview.md)。 GMSA 帐户用于允许 JEA 用户访问作为其他计算机或 web 服务的网络资源。 它提供域标识，可用于针对域中任何计算机上的资源进行身份验证。 稍后会在安装过程中向 gMSA 帐户授予必要的管理权限。 在此示例中，我们调用了帐户 **gMSAContoso**。
2. 创建一个 Active Directory 组，该用户需要被授予委派命令的权限。 在此示例中，将向技术支持人员授予读取、更新和重置 ADFS 锁定状态的权限。 在整个示例中，我们将此组称为 **JEAContoso**。

### <a name="install-the-gmsa-account-on-the-adfs-server"></a>在 ADFS 服务器上安装 gMSA 帐户：
创建对 ADFS 服务器具有管理权限的服务帐户。 只要安装了 AD RSAT 包，就可以在域控制器上或远程执行此文件。服务帐户必须在与 ADFS 服务器相同的林中创建。
将示例值修改为你的场配置。

```powershell
 # This command should only be run if this is the first time gMSA accounts are enabled in the forest
Add-KdsRootKey -EffectiveTime ((get-date).addhours(-10)) 

# Run this on every node that you want to have JEA configured on
$adfsServer = Get-ADComputer server01.contoso.com

# Run targeted at domain controller
$serviceaccount = New-ADServiceAccount gMSAcontoso -DNSHostName <FQDN of the domain containing the KDS key> - PrincipalsAllowedToRetrieveManagedPassword $adfsServer –passthru

# Run this on every node
Add-ADComputerServiceAccount -Identity server01.contoso.com -ServiceAccount $ServiceAccount
```

在 ADFS 服务器上安装 gMSA 帐户。这需要在场中的每个 ADFS 节点上运行。

```powershell
Install-ADServiceAccount gMSAcontoso
```

### <a name="grant-the-gmsa-account-admin-rights"></a>授予 gMSA 帐户管理员权限
如果场使用委派管理，请通过将 gMSA 帐户添加到具有委派管理权限的现有组来授予该帐户管理员权限。

如果场未使用委派的管理，则通过使其成为所有 ADFS 服务器上的本地管理组来授予 gMSA 帐户管理员权限。


### <a name="create-the-jea-role-file"></a>创建 JEA 角色文件

在 AD FS 服务器上，在记事本文件中创建 JEA 角色。 [JEA 角色功能](https://docs.microsoft.com/powershell/scripting/learn/remoting/jea/role-capabilities)中提供了有关创建角色的说明。

在此示例中委托的 commandlet 为 `Reset-AdfsAccountLockout, Get-ADFSAccountActivity, and Set-ADFSAccountActivity` 。

JEA 角色委托访问 "ADFSAccountLockout"、"ADFSAccountActivity" 和 "ADFSAccountActivity" commandlet：

```powershell
@{
GUID = 'b35d3985-9063-4de5-81f8-241be1f56b52'
ModulesToImport = 'adfs'
VisibleCmdlets = 'Reset-AdfsAccountLockout', 'Get-ADFSAccountActivity', 'Set-ADFSAccountActivity'
}
```


### <a name="create-the-jea-session-configuration-file"></a>创建 JEA 会话配置文件
按照说明创建 [JEA 会话配置](https://docs.microsoft.com/powershell/scripting/learn/remoting/jea/session-configurations) 文件。 配置文件确定谁可以使用 JEA 终结点，以及他们有权访问哪些功能。

角色功能由平面名称引用 (filename，不包含角色功能文件的扩展) 。 如果系统上有多个具有相同平面名称的角色功能，则 PowerShell 会使用其隐式搜索顺序来选择有效的角色功能文件。 它不会授予对具有相同名称的所有角色功能文件的访问权限。

若要使用路径指定角色功能文件，请使用 `RoleCapabilityFiles` 参数。 对于子文件夹，JEA 将查找包含子文件夹的有效 Powershell 模块 `RoleCapabilities` ，其中 `RoleCapabilityFiles` 应将参数修改为 `RoleCapabilities` 。

会话配置文件示例：

```powershell
@{
SchemaVersion = '2.0.0.0'
GUID = '54c8d41b-6425-46ac-a2eb-8c0184d9c6e6'
SessionType = 'RestrictedRemoteServer'
GroupManagedServiceAccount =  'CONTOSO\gMSAcontoso'
RoleDefinitions = @{ JEAcontoso = @{ RoleCapabilityFiles = 'C:\Program Files\WindowsPowershell\Modules\AccountActivityJEA\RoleCapabilities\JEAAccountActivityResetRole.psrc' } }
}
```

保存会话配置文件。

如果已使用文本编辑器手动编辑 .pssc 文件来确保语法正确，强烈建议 [测试会话配置文件](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) 。 如果会话配置文件未通过此测试，则未在系统上成功注册它。

### <a name="install-the-jea-session-configuration-on-the-ad-fs-server"></a>在 AD FS 服务器上安装 JEA 会话配置

在 AD FS 服务器上安装 JEA 会话配置

```powershell
Register-PSSessionConfiguration -Path .\JEASessionConfig.pssc -name "AccountActivityAdministration" -force
```
## <a name="operational-instructions"></a>操作说明
设置后，可以使用 JEA 日志记录和审核来确定正确的用户是否有权访问 JEA 终结点。

使用委派的命令：

```powershell
Enter-pssession -ComputerName server01.contoso.com -ConfigurationName "AccountActivityAdministration" -Credential <User Using JEA>
Get-AdfsAccountActivity <User>


```
