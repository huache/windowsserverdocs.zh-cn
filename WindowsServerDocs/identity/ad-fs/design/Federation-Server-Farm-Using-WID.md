---
ms.assetid: f775cbda-a75d-439d-9aa7-82f3bc8dc932
title: 使用 WID 的联合服务器场
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: c91b24313f3bb11592da1dcd25e8e9330fcfd250
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87945354"
---
# <a name="legacy-ad-fs-federation-server-farm-using-wid"></a>旧 AD FS 使用 WID 的联合服务器场

Active Directory 联合身份验证服务 AD FS 的默认拓扑 \( \) 是使用 Windows 内部数据库 WID 的联合服务器场 \( \) 。 在此拓扑中，AD FS 使用 WID 作为已加入到该场中的所有联合服务器的 AD FS 配置数据库的存储。 该场针对场中的每台服务器，在此配置数据库中复制和维护联合身份验证服务数据。 Windows Server 2012 R2 中的 AD FS 允许具有100或更少信赖方信任的组织使用 WID 和最多30个服务器来配置联合服务器场。

在场中创建第一台联合服务器的操作也将创建一项新的联合身份验证服务。 当你使用 WID 作为 AD FS 配置数据库时，你在场中创建的第一台联合服务器称为 "*主联合服务器*"。 这意味着此计算机配置了 \/ AD FS 配置数据库的读写副本。

你为此场配置的所有其他联合服务器称为 "*辅助联合*服务器"，因为它们必须将主联合服务器上所做的任何更改复制到 \- 它们本地存储的 AD FS 配置数据库的只读副本。

> [!IMPORTANT]
> 建议在负载平衡配置中至少使用两台联合服务器 \- 。

## <a name="deployment-considerations"></a>部署注意事项
本部分介绍有关与此部署拓扑相关的目标受众、权益和限制的各种注意事项。

### <a name="who-should-use-this-topology"></a>谁应该使用此拓扑？

- 具有100或更少配置的信任关系的组织，需要为其内部用户提供 \( 登录到物理连接到公司网络的计算机的内部用户， \) 并通过单一登录 \- \( SSO \) 访问联合应用程序或服务

- 希望向其内部用户提供对 Microsoft Online Services 或 Microsoft Office 365 的 SSO 访问的组织

- 需要冗余、可缩放服务的小型组织

> [!NOTE]
> 具有更大数据库的组织应考虑使用 SQL Server 部署拓扑中的[联合服务器场](Federation-Server-Farm-Using-SQL-Server.md)。 具有从网络外部登录的用户的组织应考虑使用使用[WID 和代理拓扑的联合服务器场，](Federation-Server-Farm-Using-WID-and-Proxies.md)或者使用 SQL Server 拓扑的[联合服务器场](Federation-Server-Farm-Using-SQL-Server.md)。

### <a name="what-are-the-benefits-of-using-this-topology"></a>使用此拓扑的好处是什么？

- 为内部用户提供 SSO 访问

- 数据和联合身份验证服务冗余 \( 每个联合服务器会将更改复制到相同场中的其他联合服务器\)

- WID 包含在 Windows 中;因此，无需购买 SQL Server

### <a name="what-are-the-limitations-of-using-this-topology"></a>使用此拓扑的限制是什么？

- 如果有100个或更少的信赖方信任，则 WID 场的限制为30个联合服务器。

- WID 场不支持令牌重播检测或 \( 安全断言标记语言 SAML 协议的项目解析部分 \( \) \) 。

下表简要介绍了如何使用 WID 场。 使用它来规划你的实现。

| 1-100 个 RP 信任 | 100 个以上的 RP 信任 |
|--|--|
| **1-30 AD FS 节点：** WID 受支持 | **1-30 AD FS 节点：** 不支持使用 WID - 需要 SQL |
| **超过 30 个 AD FS 节点：** 不支持使用 WID - 需要 SQL | **超过 30 个 AD FS 节点：** 不支持使用 WID - 需要 SQL |


## <a name="server-placement-and-network-layout-recommendations"></a>服务器布局和网络布局建议
当你准备好开始在网络中部署此拓扑时，你应该计划将企业网络中的所有联合服务器置于网络负载平衡 NLB 主机之后， \( \) 可以为具有专用群集域名系统 \( DNS \) 名称和群集 IP 地址的 nlb 群集配置这些服务器。

> [!NOTE]
> 此群集 DNS 名称必须与联合身份验证服务名称相匹配，例如 fs.fabrikam.com。

NLB 主机可以使用在此 NLB 群集中定义的设置，将客户端请求分配给各个联合服务器。 下图显示了虚构的 Fabrikam，Inc. 公司如何使用两 \- 台计算机联合服务器场 fs1 和 fs2 与 WID 一起设置其部署的第一阶段，以及如何将 \( \) DNS 服务器和单个 NLB 主机连接到公司网络。

![使用 WID 的服务器场](media/FarmWID.gif)

> [!NOTE]
> 如果此单个 NLB 主机上出现故障，用户将无法访问联合应用程序或服务。 如果你的业务要求不允许存在单点故障，则应添加其他 NLB 主机。

有关如何配置网络环境以用于联合服务器的详细信息，请参阅[AD FS 要求](AD-FS-Requirements.md)中的名称解析要求部分。

## <a name="see-also"></a>另请参阅
[规划 AD FS 部署拓扑](Plan-Your-AD-FS-Deployment-Topology.md) 
[Windows Server 2012 R2 中 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)
