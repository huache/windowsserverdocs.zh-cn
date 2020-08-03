---
title: 从 DirectAccess 迁移到 Always On VPN
description: 从 DirectAccess 迁移到 Always On VPN 需要一个特定的进程来迁移客户端，这有助于最大程度地减少执行迁移步骤时出现的争用情况。
manager: dougkim
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: eeca4cf7-90f0-485d-843c-76c5885c54b0
ms.author: lizross
author: eross-msft
ms.date: 06/07/2018
ms.openlocfilehash: 68184fe43fd027ea24bd0e77623002ec88368e86
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517692"
---
# <a name="migrate-to-always-on-vpn-and-decommission-directaccess"></a>迁移到始终启用 VPN 并解除 DirectAccess 授权

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows 10

&#171; [**上一步：** 规划 DIRECTACCESS 以 Always On VPN 迁移](da-always-on-migration-planning.md)<br>

从 DirectAccess 迁移到 Always On VPN 需要一个特定的进程来迁移客户端，这有助于最大程度地减少执行迁移步骤时出现的争用情况。 从较高层次来看，迁移过程包括以下四个主要步骤：

1.  **部署并行 VPN 基础结构。** 确定要在部署中包括的迁移阶段和功能后，会将 VPN 基础结构与现有的 DirectAccess 基础结构并行部署。

2.  **将证书和配置部署到客户端。**  VPN 基础结构准备就绪后，创建所需的证书并将其发布到客户端。 当客户端收到证书后，你将部署 VPN_Profile.ps1 配置脚本。 或者，你可以使用 Intune 来配置 VPN 客户端。 使用 Microsoft Endpoint Configuration Manager 或 Microsoft Intune 来监视是否成功部署了 VPN 配置。

3.  [!INCLUDE [remove-da-security-group-shortdesc-include](../includes/remove-da-security-group-shortdesc-include.md)]

4.  [!INCLUDE [decommission-da-shortdesc-include](../includes/decommission-da-shortdesc-include.md)]

在开始从 DirectAccess 到 Always On VPN 的迁移过程之前，请确保已计划迁移。  如果尚未计划迁移，请参阅[规划 DirectAccess 以便 ALWAYS ON VPN 迁移](da-always-on-migration-planning.md)。

>[!TIP]
>本部分不是 Always On VPN 的分步部署指南，而是旨在补充[Windows Server 和 windows 10 的 ALWAYS ON VPN 部署](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md)，并提供特定于迁移的部署指南。

## <a name="deploy-a-side-by-side-vpn-infrastructure"></a>部署并排 VPN 基础结构

与现有的 DirectAccess 基础结构并行部署 VPN 基础结构。  有关分步详细信息，请参阅[Always On 适用于 Windows Server 和 windows 10 的 VPN 部署](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md)，以便安装和配置 Always On vpn 基础结构。

并行部署由以下高级任务组成：

1.  创建 VPN 用户、VPN 服务器和 NPS 服务器组。

2.  创建并发布所需的证书模板。

3.  注册服务器证书。

4.  安装和配置 Always On VPN 的远程访问服务。

5.  安装和配置 NPS。

6.  为 Always On VPN 配置 DNS 和防火墙规则。

下图提供了有关 DirectAccess 到 Always On VPN 迁移中的基础结构更改的视觉参考。

![DirectAccess 到 Always On VPN 迁移中的基础结构更改示意图](../../media/DA-to-AlwaysOnVPN/6b64f322f945f837f22a32bf87a228f8.png)

## <a name="deploy-certificates-and-vpn-configuration-script-to-the-clients"></a>将证书和 VPN 配置脚本部署到客户端

尽管[部署 ALWAYS ON vpn](../vpn/always-on-vpn/deploy/always-on-vpn-deploy-deployment.md)部分中的 VPN 客户端配置很大，但完成从 DirectAccess 到 Always On VPN 的迁移需要执行两个额外的步骤。

你必须确保在颁发证书_之后_ **VPN_Profile.ps1** ，以便 VPN 客户端不会在不尝试连接的情况下尝试连接。 为此，你将执行一个脚本，该脚本仅将已在证书中注册的用户添加到你用于部署 Always On VPN 配置的 VPN 部署就绪组。

>[!NOTE]
>Microsoft 建议你在执行此过程之前，先对其进行测试，然后再执行任何用户迁移环。

1.  **创建并发布 VPN 证书，并启用自动注册组策略对象（GPO）。** 对于传统的基于证书的 Windows 10 VPN 部署，会向设备或用户颁发证书，使其能够对连接进行身份验证。 为自动注册创建并发布新的身份验证证书时，必须使用配置为 VPN 用户组的自动注册设置来创建和部署 GPO。 有关配置证书和自动注册的步骤，请参阅[配置服务器基础结构](../vpn/always-on-vpn/deploy/vpn-deploy-server-infrastructure.md)。

2.  **将用户添加到 VPN 用户组。** 添加任何迁移到 VPN 用户组的用户。 这些用户在迁移后会在该安全组中保留，以便以后可以接收任何证书更新。 继续向此组添加用户，直到将每个用户从 DirectAccess 移动到 Always On VPN。

3.  **确定已接收 VPN 身份验证证书的用户。** 正在从 DirectAccess 迁移，因此你将需要添加一个方法，用于确定客户端何时接收到所需的证书并准备好接收 VPN 配置信息。 运行**GetUsersWithCert.ps1**脚本，将当前颁发了 nonrevoked 证书的用户从指定的模板名称添加到指定的 AD DS 安全组。 例如，在运行**GetUsersWithCert.ps1**脚本后，任何从 Vpn 身份验证证书模板颁发了有效证书的用户都会添加到 Vpn 部署就绪组。

    >[!NOTE]
    >如果你没有方法来确定客户端何时接收到所需的证书，你可以在向用户颁发证书之前部署 VPN 配置，导致 VPN 连接失败。 若要避免这种情况，请在证书颁发机构或按计划运行**GetUsersWithCert.ps1**脚本，以将接收到该证书的用户同步到 VPN 部署就绪组。 然后，你将使用该安全组来定位 Microsoft 终结点 Configuration Manager 或 Intune 中的 VPN 配置部署，这确保了托管客户端在收到证书之前不会接收到 VPN 配置。

    ### <a name="getuserswithcertps1"></a>GetUsersWithCert.ps1

    ```powershell
    Import-module ActiveDirectory
    Import-Module AdcsAdministration

    $TemplateName = 'VPNUserAuthentication'##Certificate Template Name (not the friendly name)
    $GroupName = 'VPN Deployment Ready' ##Group you will add the users to
    $CSServerName = 'localhost\corp-dc-ca' ##CA Server Information

    $users= @()
    $TemplateID = (get-CATemplate | Where-Object {$_.Name -like $TemplateName} | Select-Object oid).oid
    $View = New-Object -ComObject CertificateAuthority.View
    $NULL = $View.OpenConnection($CSServerName)
    $View.SetResultColumnCount(3)
    $i1 = $View.GetColumnIndex($false, "User Principal Name")
    $i2 = $View.GetColumnIndex($false, "Certificate Template")
    $i3 = $View.GetColumnIndex($false, "Revocation Date")
    $i1, $i2, $i3 | %{$View.SetResultColumn($_) }
    $Row= $View.OpenView()

    while ($Row.Next() -ne -1){
    $Cert = New-Object PsObject
    $Col = $Row.EnumCertViewColumn()
    [void]$Col.Next()
    do {
    $Cert | Add-Member -MemberType NoteProperty $($Col.GetDisplayName()) -Value $($Col.GetValue(1)) -Force
          }
    until ($Col.Next() -eq -1)
    $col = ''

    if($cert."Certificate Template" -eq $TemplateID -and $cert."Revocation Date" -eq $NULL){
       $users= $users+= $cert."User Principal Name"
    $temp = $cert."User Principal Name"
    $user = get-aduser -Filter {UserPrincipalName -eq $temp} –Property UserPrincipalName
    Add-ADGroupMember $GroupName $user
       }
      }
    ```

4. 部署 Always On 的 VPN 配置。 颁发 VPN 身份验证证书，并运行**GetUsersWithCert.ps1**脚本时，用户将添加到 VPN 部署就绪安全组。


| 如果你使用的是 .。。  | 则... |
| ---- | ---- |
| Configuration Manager | 基于该安全组的成员身份创建一个用户集合。<br><br>!["条件属性" 对话框](../../media/DA-to-AlwaysOnVPN/b38723b3ffcfacd697b83dd41a177f66.png)|
| Intune | 只需在同步后直接以安全组为目标。 |

每次运行**GetUsersWithCert.ps1**配置脚本时，还必须运行 AD DS 发现规则来更新 Configuration Manager 中的安全组成员身份。 此外，请确保部署集合的成员身份更新经常发生（与脚本和发现规则对齐）。

有关使用 Configuration Manager 或 Intune 将 Always On VPN 部署到 Windows 客户端的其他信息，请参阅[Always On 适用于 Windows Server 和 windows 10 的 Vpn 部署](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md)。 但是，请务必合并这些特定于迁移的任务。

>[!NOTE]
>将这些特定于迁移的任务合并到简单 Always On VPN 部署与从 DirectAccess 迁移到 Always On VPN 之间存在重要差异。 务必正确定义集合，使其面向安全组，而不是使用 "部署指南" 中的方法。


## <a name="remove-devices-from-the-directaccess-security-group"></a>从 DirectAccess 安全组中删除设备

当用户收到身份验证证书和**VPN_Profile.ps1**配置脚本时，你会在 Configuration Manager 或 Intune 中看到对应的成功 VPN 配置脚本部署。 在每次部署后，从 DirectAccess 安全组中删除该用户的设备，以便以后可以删除 DirectAccess。 Intune 和 Configuration Manager 都包含用户设备分配信息，以帮助你确定每个用户的设备。

>[!NOTE]
>如果要通过组织单位（Ou）而不是计算机组来应用 DirectAccess Gpo，请将用户的计算机对象移出 OU。

## <a name="decommission-the-directaccess-infrastructure"></a>停止 DirectAccess 基础结构

完成将所有 DirectAccess 客户端迁移到 Always On VPN 之后，可以解除 DirectAccess 基础结构的授权，并从组策略中删除 DirectAccess 设置。 Microsoft 建议执行以下步骤，以正常从环境中删除 DirectAccess：

1. **删除配置设置。** 通过打开远程访问管理控制台并选择 "删除配置设置" 来删除创建的 "远程访问" Gpo 和远程访问组策略设置，如下图所示。 如果在删除配置之前删除组，可能会出现错误。

    ![从环境中删除 DirectAccess 的过程](../../media/DA-to-AlwaysOnVPN/dbdc3d80e8dc1b8665f7b15d7d2ee1f6.png)

2. **从 DirectAccess 安全组中删除设备。** 用户成功迁移后，将从 DirectAccess 安全组中删除其设备。 从环境中删除 DirectAccess 之前，请检查 DirectAccess 安全组是否为空。 如果安全组仍包含成员，请不要删除它。 如果删除包含成员的安全组，则会有风险，使员工无需从其设备进行远程访问。 使用 Microsoft 端点 Configuration Manager 或 Microsoft Intune 来确定设备分配信息，并发现哪个设备属于每个用户。

3. **清理 DNS。** 请确保从内部 DNS 服务器和与 DirectAccess 相关的公共 DNS 服务器（例如，DA.contoso.com、DAGateway.contoso.com）中删除任何记录。

4. **停止 DirectAccess 服务器。** 成功删除配置设置和 DNS 记录后，便可以删除 DirectAccess 服务器。 为此，请删除中的角色服务器管理器或解除服务器授权，并将其从 AD DS 中删除。

5. **删除 Active Directory 证书服务中的所有 DirectAccess 证书。** 如果你使用计算机证书进行 DirectAccess 实现，请从证书颁发机构控制台中的 "证书模板" 文件夹中删除已发布的模板。

## <a name="next-step"></a>后续步骤

已完成从 DirectAccess 到 Always On VPN 的迁移。
