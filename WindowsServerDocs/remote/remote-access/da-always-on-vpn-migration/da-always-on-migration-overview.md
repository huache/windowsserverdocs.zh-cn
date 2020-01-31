---
title: VPN 迁移 Always On 远程访问概述
description: Always On 的 VPN 可解决 Windows Vpn 和 DirectAccess 之间之前的缺口，以及如何从 DirectAccess 迁移到 Always On VPN。
manager: dougkim
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: eeca4cf7-90f0-485d-843c-76c5885c54b0
ms.author: pashort
author: shortpatti
ms.date: 05/29/2018
ms.openlocfilehash: d3ea6f0e29803b8a709f31811f77678bf03201a8
ms.sourcegitcommit: 07c9d4ea72528401314e2789e3bc2e688fc96001
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76822572"
---
# <a name="overview-of-the-directaccess-to-always-on-vpn-migration"></a>DirectAccess 到始终启用 VPN 迁移概述 

>适用于: Windows Server (半年频道)、Windows Server 2016、Windows 10

&#187;[**下一步：** 规划 DIRECTACCESS 以便 Always On VPN 迁移](da-always-on-migration-planning.md)

在以前版本的 Windows VPN 体系结构中，平台限制使得难以提供替换 DirectAccess 所需的关键功能，如用户登录前启动的自动连接。 但 Always On VPN 已减轻了这些限制或扩展了 DirectAccess 功能之外的 VPN 功能。 Always On VPN 将解决 Windows Vpn 和 DirectAccess 之间的以前的差距。

DirectAccess 到 Always On VPN 迁移过程包括四个主要组件和高级流程：


1.  **Plan the Always On VPN migration.** Planning helps identify target clients for user phase separation as well as infrastructure and functionality.

    1.  [!INCLUDE [build-migration-rings-shortdesc-include](../includes/build-migration-rings-shortdesc-include.md)]

    2.  [!INCLUDE [review-feature-mapping-shortdesc-include](../includes/review-feature-mapping-shortdesc-include.md)] 

    3.  [!INCLUDE [review-the-enhancements-shortdesc-include](../includes/review-the-enhancements-shortdesc-include.md)] 

    4.  [!INCLUDE [review-the-technology-overview-shortdesc-include](../includes/review-the-technology-overview-shortdesc-include.md)]

2.  **Deploy a side-by-side VPN infrastructure.** After you have determined your migration phases and the features you want to include in your deployment, you deploy the Always On VPN infrastructure side by side with the existing DirectAccess infrastructure.  

3.  **Deploy certificates and configuration to the clients.**  Once the VPN infrastructure is ready, you create and publish the required certificates to the client. When the clients have received the certificates, you deploy the VPN_Profile.ps1 configuration script. Alternatively, you can use Intune to configure the VPN client. Use Microsoft Endpoint Configuration Manager or Microsoft Intune to monitor for successful VPN configuration deployments.

4.  **Remove and decommission.** Properly decommission the environment after you have migrated everyone off DirectAccess.

    1.  [!INCLUDE [remove-da-from-client-shortdesc-include](../includes/remove-da-from-client-shortdesc-include.md)]

    2.  [!INCLUDE [decommission-da-shortdesc-include](../includes/decommission-da-shortdesc-include.md)]


## <a name="directaccess-deployment-scenario"></a>DirectAccess deployment scenario

In this deployment scenario, you use a simple DirectAccess deployment scenario as a starting point for the migration this guide presents. You do not need to match this deployment scenario before migrating to Always On VPN, but for many organizations, this simple setup is an accurate representation of their current DirectAccess deployment. The table below provides a list of basic features for this setup.

Many DirectAccess deployment scenarios and options exist, so your implementation is likely to be different from the one described here. If so, refer to [Feature mapping between DirectAccess and Always On VPN](../vpn/vpn-map-da.md) to determine the Always On VPN feature set mapping for your current additions, and then add those features to your configuration. Also, you can refer to the [Always On VPN enhancements](../vpn/always-on-vpn/always-on-vpn-enhancements.md) to add options to your Always On VPN deployment.

>[!NOTE] 
>For nondomain-joined devices, there are additional considerations, such as certificate enrollment. For details, see [Always On VPN Deployment for Windows Server and Windows 10](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md).

### <a name="deployment-scenario-feature-list"></a>Deployment scenario feature list

| DirectAccess feature | Typical scenario |
|-----|----|
| 部署方案                   | Deploy full DirectAccess for client access and remote management                                               |
| 网络适配器                      | 2                                                                                                              |
| 用户身份验证                   | Active Directory 凭据                                                                                   |
| Use computer certificates             | “是”                                                                                                            |
| 安全组                       | “是”                                                                                                            |
| Single DirectAccess server            | “是”                                                                                                            |
| 网络拓扑                      | Network address translation (NAT) behind an edge firewall with two network adapters                            |
| Access mode                           | End to edge                                                                                                    |
| 隧道                             | Split tunnel                                                                                                   |
| 身份验证                        | Standard public key infrastructure (PKI) authentication with machine certificate plus Kerberos (not KerbProxy) |
| 协议                             | IP over HTTPS (IP-HTTPS)                                                                                       |
| Network location server (NLS) off-box | “是”                                                                                                            |

## <a name="always-on-vpn-deployment-scenario"></a>Always On VPN deployment scenario

In this deployment scenario, you focus on migrating a simple DirectAccess environment to a simple Always On VPN environment, which is the DirectAccess replacement solution. The following table provides the features used in this simple solution. For more detailed information about additional enhancements to the Always On VPN client, see [Always On VPN enhancements](../vpn/always-on-vpn/always-on-vpn-enhancements.md).

### <a name="always-on-vpn-features-used-in-the-simple-environment"></a>Always On VPN features used in the simple environment

| VPN feature | Deployment scenario configuration |
|-----|-----|
| 连接类型 | Native Internet Key Exchange version 2 (IKEv2) |
| 网络适配器   | 2        |
| 用户身份验证  | Active Directory 凭据            |
| Use computer certificates        | “是”                          |
| 路由 | Split Tunneling |
| 名称解析 | Domain name information list and Domain Name System (DNS) suffix |
| Triggering | Always on and trusted network detection |
| 身份验证  | Protected Extensible Authentication Protocol-Transport Layer Security (PEAP-TLS) with Trusted Platform Module–protected user certificates |

## <a name="next-step"></a>下一步

[Plan the DirectAccess to Always On VPN migration](da-always-on-migration-planning.md). The primary goal of the migration is for users to maintain remote connectivity to the office throughout the process.

---