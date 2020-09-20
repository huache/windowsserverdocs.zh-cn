---
title: 向 Windows 10 设备创建基于 OMA-DM 的 VPNv2 配置文件
description: '可以使用以下两种方法之一创建基于 OMA 的 VPNv2 配置文件。 '
ms.topic: article
ms.date: 07/13/2018
ms.author: v-tea
author: Teresa-MOTIV
ms.localizationpriority: medium
ms.reviewer: deverette
ms.openlocfilehash: c5619baa5123d0cd611cb9371cd3944fdd91fb3c
ms.sourcegitcommit: 877d6db73d9520e3a23738d6528016235493cff3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90779261"
---
# <a name="step-75-create-oma-dm-based-vpnv2-profiles-to-windows-10-devices"></a>步骤 7.5： 创建基于 OMA 的 VPNv2 配置文件到 Windows 10 设备

>适用于： Windows Server (半年通道) ，Windows Server 2016，Windows Server 2012 R2，Windows 10

- [**上一个：** 步骤7.4。将条件性访问根证书部署到本地 AD](vpn-deploy-cond-access-root-cert-to-on-premise-ad.md)
- [**下一步：** 了解 VPN 的条件性访问的工作原理](/windows/access-protection/vpn/vpn-conditional-access)

在此步骤中，你可以使用 Intune 创建基于 OMA 的 VPNv2 配置文件来部署 VPN 设备配置策略。 如果要使用 Microsoft Endpoint Configuration Manager 或 PowerShell 脚本创建 VPNv2 配置文件，请参阅 [VPNV2 CSP 设置](/windows/client-management/mdm/vpnv2-csp) 了解更多详细信息。

## <a name="managed-deployment-using-intune"></a>使用 Intune 的托管部署

本部分所述的所有内容都是使用条件性访问进行 VPN 工作所需的最低要求。 它不涵盖拆分隧道，使用 WIP，创建自定义 Intune 设备配置配置文件以获取 AutoVPN 的工作或 SSO。 将下面的设置集成到你之前在步骤5中创建的 VPN 配置文件 [。配置 Windows 10 客户端 Always On VPN 连接](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)。在此示例中，我们将它们集成到 [使用 Intune 策略配置 VPN 客户端](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune) 。

**先决条件**

已使用 Intune 将 Windows 10 客户端计算机配置为使用 VPN 连接。


**方法**

1. 在 Azure 门户中，选择 " **intune**  >  **设备配置**" "配置  >  **文件**"，然后选择前面在[使用 Intune 配置 VPN 客户端](always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune)中创建的 vpn 配置文件。

2. 在策略编辑器中，选择 "**属性**" "设置" "  >  **Settings**  >  **基本 VPN**"。 扩展现有的 **EAP Xml** 以包含一个筛选器，该筛选器为 VPN 客户端提供从用户的证书存储中检索 AAD 条件访问证书所需的逻辑，而不是让该客户端使用发现的第一个证书。

    >[!NOTE]
    >如果不这样做，VPN 客户端可以检索从本地证书颁发机构颁发的用户证书，导致 VPN 连接失败。

    ![Intune 门户](../../media/Always-On-Vpn/intune-eap-xml.png)

3. 找到以结尾的部分 **\</AcceptServerName>\</EapType>** ，并在这两个值之间插入以下字符串，为 VPN 客户端提供选择 AAD 条件访问证书的逻辑：

    ```XML
    <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled="true"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions>
    ```

4. 选择 " **条件性访问** " 边栏选项卡，并将 **此 VPN 连接的条件性访问** 切换为 " **启用**"。

   启用此设置将更改 VPNv2 配置文件 XML 中的** \<DeviceCompliance> \<Enabled> true \</Enabled> **设置。

    ![Always On VPN 的条件性访问-属性](../../media/Always-On-Vpn/vpn-conditional-access-azure-ad.png)

5. 选择“确定”。

6. 选择 " **分配**"，在 "包含" 下选择 " **选择要包括的组**"。

7. 选择接收此策略的 **VPN 用户** 组，然后选择 " **保存**"。

    ![自动 VPN 用户的 CAP-分配](../../media/Always-On-Vpn/cap-for-auto-vpn-users-assignments.png)

## <a name="force-mdm-policy-sync-on-the-client"></a>在客户端上强制执行 MDM 策略同步

如果未在客户端设备上显示 VPN 配置文件，则在 "设置 \\ 网络 & Internet VPN" 下， \\ 你可以强制 MDM 策略进行同步。

1. 以 **VPN 用户** 组成员的身份登录到已加入域的客户端计算机。

2. 在 "开始" 菜单上输入 " **帐户**"，然后按 enter。

3. 在左侧导航窗格中，选择 " **访问工作单位或学校**"。

4. 在 "访问工作单位或学校" 下，选择 " **已连接到 < \domain"> MDM**，然后选择 " **信息**"。

5. 选择 " **同步** "，并验证 vpn 配置文件显示在 "设置 \\ 网络 & Internet VPN" 下 \\ 。


## <a name="next-steps"></a>后续步骤

你已完成将 VPN 配置文件配置为使用 Azure AD 条件访问。

|若希望...  |然后查看 .。。  |
|---------|---------|
|了解有关条件性访问如何与 Vpn 一起工作的详细信息  |[VPN 和条件性访问](/windows/access-protection/vpn/vpn-conditional-access)：本页提供有关条件性访问如何与 vpn 一起工作的详细信息。      |
|了解有关高级 VPN 功能的详细信息  |[高级 VPN 功能](always-on-vpn/deploy/always-on-vpn-adv-options.md#advanced-vpn-features)：本页提供有关以下内容的指导：如何启用 VPN 流量筛选器、如何使用应用程序触发器配置自动 vpn 连接，以及如何将 NPS 配置为仅允许使用 Azure AD 颁发的证书的客户端进行 VPN 连接。        |


## <a name="related-topics"></a>相关主题

- [VPNV2 csp](/windows/client-management/mdm/vpnv2-csp)：本主题提供 VPNv2 CSP 的概述。 VPNv2 配置服务提供程序允许 (MDM) 服务器的移动设备管理配置设备的 VPN 配置文件。

- [配置 Windows 10 客户端 ALWAYS ON VPN 连接](./always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md)：本主题提供了有关 ProfileXML 选项和架构的信息，以及如何创建 ProfileXML VPN。 设置服务器基础结构后，你必须将 Windows 10 客户端计算机配置为使用 VPN 连接与该基础结构进行通信。

- [使用 Intune 配置 VPN 客户端](./always-on-vpn/deploy/vpn-deploy-client-vpn-connections.md#configure-the-vpn-client-by-using-intune)：本主题提供有关如何将 Windows 10 远程访问部署 Always On VPN 配置文件的信息。 Intune 现在使用 Azure AD 组。 如果 Azure AD Connect 将 VPN 用户组从本地同步到 Azure AD，则无需使用 Intune 配置 VPN 客户端。
