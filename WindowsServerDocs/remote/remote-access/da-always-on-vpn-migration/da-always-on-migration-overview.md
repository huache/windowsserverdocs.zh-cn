---
title: VPN 迁移 Always On 远程访问概述
description: Always On 的 VPN 可解决 Windows Vpn 和 DirectAccess 之间之前的缺口，以及如何从 DirectAccess 迁移到 Always On VPN。
manager: dougkim
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: eeca4cf7-90f0-485d-843c-76c5885c54b0
ms.author: lizross
author: eross-msft
ms.date: 05/29/2018
ms.openlocfilehash: bd4d0d4d3b165a4e89a00cd2975ace20687aed7d
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314986"
---
# <a name="overview-of-the-directaccess-to-always-on-vpn-migration"></a>DirectAccess 到始终启用 VPN 迁移概述 

>适用于: Windows Server (半年频道)、Windows Server 2016、Windows 10

&#187;[**下一步：** 规划 DIRECTACCESS 以便 Always On VPN 迁移](da-always-on-migration-planning.md)

在以前版本的 Windows VPN 体系结构中，平台限制使得难以提供替换 DirectAccess 所需的关键功能，如用户登录前启动的自动连接。 但 Always On VPN 已减轻了这些限制或扩展了 DirectAccess 功能之外的 VPN 功能。 Always On VPN 将解决 Windows Vpn 和 DirectAccess 之间的以前的差距。

DirectAccess 到 Always On VPN 迁移过程包括四个主要组件和高级流程：


1.  **规划 Always On VPN 迁移。** 规划有助于识别用户阶段分离的目标客户端，以及基础结构和功能。

    1.  [!INCLUDE [build-migration-rings-shortdesc-include](../includes/build-migration-rings-shortdesc-include.md)]

    2.  [!INCLUDE [review-feature-mapping-shortdesc-include](../includes/review-feature-mapping-shortdesc-include.md)] 

    3.  [!INCLUDE [review-the-enhancements-shortdesc-include](../includes/review-the-enhancements-shortdesc-include.md)] 

    4.  [!INCLUDE [review-the-technology-overview-shortdesc-include](../includes/review-the-technology-overview-shortdesc-include.md)]

2.  **部署并行 VPN 基础结构。** 确定要在部署中包括的迁移阶段和功能后，将 Always On VPN 基础结构与现有 DirectAccess 基础结构并行部署。  

3.  **将证书和配置部署到客户端。**  VPN 基础结构准备就绪后，创建所需的证书并将其发布到客户端。 当客户端收到证书后，你将部署 VPN_Profile ps1 配置脚本。 或者，你可以使用 Intune 来配置 VPN 客户端。 使用 Microsoft Endpoint Configuration Manager 或 Microsoft Intune 来监视是否成功部署了 VPN 配置。

4.  **删除和解除授权。** 在将所有用户迁移到脱离 DirectAccess 后，正确解除环境的授权。

    1.  [!INCLUDE [remove-da-from-client-shortdesc-include](../includes/remove-da-from-client-shortdesc-include.md)]

    2.  [!INCLUDE [decommission-da-shortdesc-include](../includes/decommission-da-shortdesc-include.md)]


## <a name="directaccess-deployment-scenario"></a>DirectAccess 部署方案

在此部署方案中，你将使用简单的 DirectAccess 部署方案作为本指南的迁移的起点。 在迁移到 Always On VPN 之前，无需匹配此部署方案，但对于许多组织而言，这一简单的设置是其当前 DirectAccess 部署的准确表示。 下表提供了此安装程序的基本功能列表。

存在许多 DirectAccess 部署方案和选项，因此您的实现可能与此处描述的不同。 如果是这样，请参阅[DirectAccess 与 ALWAYS ON VPN 之间的功能映射](../vpn/vpn-map-da.md)，以确定当前添加项的 Always On VPN 功能集映射，然后将这些功能添加到配置。 此外，还可以参考[ALWAYS ON vpn 增强功能](../vpn/always-on-vpn/always-on-vpn-enhancements.md)，将选项添加到 Always On VPN 部署。

>[!NOTE] 
>对于未加入域的设备，还需要考虑其他注意事项，如证书注册。 有关详细信息，请参阅[Always On 适用于 Windows Server 和 windows 10 的 VPN 部署](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md)。

### <a name="deployment-scenario-feature-list"></a>部署方案功能列表

| DirectAccess 功能 | 典型方案 |
|-----|----|
| 部署方案                   | 部署用于客户端访问和远程管理的完整 DirectAccess                                               |
| 网络适配器                      | 2                                                                                                              |
| 用户身份验证                   | Active Directory 凭据                                                                                   |
| 使用计算机证书             | 是                                                                                                            |
| 安全组                       | 是                                                                                                            |
| 单个 DirectAccess 服务器            | 是                                                                                                            |
| 网络拓扑                      | 具有两个网络适配器的边缘防火墙后面的网络地址转换（NAT）                            |
| 访问模式                           | 结束到边缘                                                                                                    |
| 隧道                             | 拆分隧道                                                                                                   |
| 身份验证                        | 具有计算机证书和 Kerberos 的标准公钥基础结构（PKI）身份验证（不是 KerbProxy） |
| 协议                             | IP over HTTPS （ip-https）                                                                                       |
| 网络位置服务器（NLS）开箱即用 | 是                                                                                                            |

## <a name="always-on-vpn-deployment-scenario"></a>Always On VPN 部署方案

在此部署方案中，重点介绍如何将简单的 DirectAccess 环境迁移到简单的 Always On VPN 环境，该环境是 DirectAccess 替代解决方案。 下表提供了此简单解决方案中使用的功能。 有关 Always On VPN 客户端的其他增强功能的详细信息，请参阅[ALWAYS ON vpn 增强](../vpn/always-on-vpn/always-on-vpn-enhancements.md)。

### <a name="always-on-vpn-features-used-in-the-simple-environment"></a>简单环境中使用的 Always On VPN 功能

| VPN 功能 | 部署方案配置 |
|-----|-----|
| 连接类型 | Native Internet 密钥交换版本2（IKEv2） |
| 网络适配器   | 2        |
| 用户身份验证  | Active Directory 凭据            |
| 使用计算机证书        | 是                          |
| 路由 | 拆分隧道 |
| 名称解析 | 域名信息列表和域名系统（DNS）后缀 |
| 触发器 | Alwayson 和受信任的网络检测 |
| 身份验证  | 受保护的可扩展身份验证协议-通过受信任的平台模块的传输层安全性（PEAP-TLS）-受保护的用户证书 |

## <a name="next-step"></a>下一步

[规划 DirectAccess 以便 ALWAYS ON VPN 迁移](da-always-on-migration-planning.md)。 迁移的主要目的是让用户在整个过程中保持与办公室的远程连接。

---