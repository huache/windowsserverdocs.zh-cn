---
ms.assetid: f0464182-56a2-4bfa-a8c8-7e39c1bd62d3
title: 使用 WID 和代理的联合服务器场
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: bb8ad6a7325e56d9cc548b23fb0876c76ba9c113
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519926"
---
# <a name="federation-server-farm-using-wid-and-proxies"></a>使用 WID 和代理的联合服务器场

Active Directory 联合身份验证服务（AD FS）的此部署拓扑与具有 Windows 内部数据库（WID）拓扑的联合服务器场完全相同，但它将代理计算机添加到外围网络以支持外部用户。 这些代理将来自企业网络外部的客户端身份验证请求重定向到联合服务器场。 在以前版本的 AD FS 中，这些代理被称为联合服务器代理。

> [!IMPORTANT]
> 在 Windows Server 2012 R2 的 Active Directory 联合身份验证服务（AD FS）中，联合服务器代理的角色由称为 Web 应用程序代理的新远程访问角色服务处理。 若要使你的 AD FS 可以从企业网络外部进行访问（这是在旧版 AD FS 中部署联合服务器代理的目的，如 AD FS 2.0 和 Windows Server 2012 中的 AD FS），可以在 Windows Server 2012 R2 中为 AD FS 部署一个或多个 web 应用程序代理。
>
> 在 AD FS 的上下文中，Web 应用程序代理充当 AD FS 联合服务器代理。 除此之外，Web 应用程序代理为企业网络内部的 Web 应用程序提供反向代理功能，使任意设备上的用户都能够从企业网络外部访问这些 Web 应用程序。 有关 Web 应用程序代理角色服务的详细信息，请参阅“Web 应用程序代理概述”。
>
> 若要规划 Web 应用程序代理的部署，可以查看以下主题中的信息：
>
> - [规划 Web 应用程序代理基础结构（WAP）](/previous-versions/orphan-topics/ws.11/dn383648(v=ws.11))
> - [规划 Web 应用程序代理服务器](/previous-versions/orphan-topics/ws.11/dn383647(v=ws.11))

## <a name="deployment-considerations"></a>部署注意事项
本部分介绍有关与此部署拓扑相关的目标受众、权益和限制的各种注意事项。

### <a name="who-should-use-this-topology"></a>谁应该使用此拓扑？

- 具有100或更少配置信任关系的组织，需要为其内部用户和外部用户（登录到实际位于公司网络外部的计算机）提供对联合应用程序或服务的单一登录（SSO）访问权限

- 需要为内部用户和外部用户提供对 Microsoft Office 365 的 SSO 访问的组织

- 具有外部用户并且需要冗余、可缩放服务的小型组织

### <a name="what-are-the-benefits-of-using-this-topology"></a>使用此拓扑的好处是什么？

- [使用 WID 拓扑为联合服务器场](Federation-Server-Farm-Using-WID.md)列出的优点，以及为外部用户提供其他访问权限的好处

### <a name="what-are-the-limitations-of-using-this-topology"></a>使用此拓扑的限制是什么？

- [使用 WID 拓扑为联合服务器场](Federation-Server-Farm-Using-WID.md)列出的限制相同

    | 1-100 RP 信任 | 超过 100 RP 信任 |
    |--|--|
    | **1-30 AD FS 节点：** 支持 WID | **1-30 AD FS 节点：** 不支持使用 WID-SQL 必需 |
    | 超过**30 个 AD FS 节点：** 不支持使用 WID-SQL 必需 | 超过**30 个 AD FS 节点：** 不支持使用 WID-SQL 必需 |

## <a name="server-placement-and-network-layout-recommendations"></a>服务器布局和网络布局建议
若要部署此拓扑，除了添加两个 web 应用程序代理外，还必须确保外围网络还可以提供对域名系统（DNS）服务器和第二个网络负载平衡（NLB）主机的访问权限。 第二个 NLB 主机必须配置一个 NLB 群集，该群集使用可通过 Internet 访问的群集 IP 地址，并且它必须与你在公司网络（fs.fabrikam.com）上配置的以前的 NLB 群集使用相同的群集 DNS 名称设置。 还应为 web 应用程序代理配置可通过 Internet 访问的 IP 地址。

下图显示了先前介绍的包含 WID 拓扑的现有联合服务器场以及虚构的 Fabrikam，Inc.，公司如何提供对外围 DNS 服务器的访问，如何添加具有相同群集 DNS 名称（fs.fabrikam.com）的第二个 NLB 主机，并将两个 web 应用程序代理（wap1 和 wap2）添加到外围网络。

![WID 场和代理](media/WIDFarmADFSBlue.gif)

有关如何配置网络环境以用于联合服务器或 web 应用程序代理的详细信息，请参阅[AD FS 要求](AD-FS-Requirements.md)和[规划 Web 应用程序代理基础结构（WAP）](/previous-versions/orphan-topics/ws.11/dn383648(v=ws.11))中的 "名称解析要求" 部分。

## <a name="see-also"></a>另请参阅
[规划 AD FS 部署拓扑](Plan-Your-AD-FS-Deployment-Topology.md) 
[Windows Server 2012 R2 中 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)

