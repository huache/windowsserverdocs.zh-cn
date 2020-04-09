---
ms.assetid: 663a2482-33d1-4c19-8607-2e24eef89fcb
title: 使用 WID 的联合服务器场
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 4704928213de4ed1ed71630fe6a49b54f2019af5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853110"
---
# <a name="federation-server-farm-using-wid"></a>使用 WID 的联合服务器场

Active Directory 联合身份验证服务 \(AD FS\) 的默认拓扑是一个联合服务器场，该场使用 Windows 内部数据库 \(WID\)，其中包含最多五个托管组织联合身份验证服务的联合服务器。 在此拓扑中，AD FS 使用 WID 作为已加入到该场中的所有联合服务器的 AD FS 配置数据库的存储。 该场针对场中的每台服务器，在此配置数据库中复制和维护联合身份验证服务数据。  
  
在场中创建第一台联合服务器的操作也将创建一项新的联合身份验证服务。 当你使用 WID 作为 AD FS 配置数据库时，你在场中创建的第一台联合服务器称为 "*主联合服务器*"。 这意味着此计算机配置了 AD FS 配置数据库的读取\/写入副本。  
  
你为此场配置的所有其他联合服务器称为 "*辅助联合*服务器\-"，因为它们必须将主联合服务器上所做的任何更改复制到它们本地存储的 AD FS 配置数据库的副本。  
  
> [!NOTE]  
> 建议在负载\-平衡配置中至少使用两台联合服务器。  
  
## <a name="deployment-considerations"></a>部署注意事项  
本部分介绍有关与此部署拓扑相关的目标受众、权益和限制的各种注意事项。  
  
### <a name="who-should-use-this-topology"></a>谁应该使用此拓扑？  
  
-   对于已配置的信任关系100或更少的组织，需要向物理连接到企业网络的计算机 \(登录到物理连接到企业网络\) 使用单一登录\-\(SSO\) 访问联合应用程序或服务  
  
-   希望向其内部用户提供对 Microsoft Online Services 或 Microsoft Office 365 的 SSO 访问的组织  
  
-   需要冗余、可缩放服务的小型组织  
  
> [!NOTE]  
> 具有更大数据库的组织应考虑使用 SQL Server 部署拓扑中的[联合服务器场](Federation-Server-Farm-Using-SQL-Server.md)，本节稍后将对此进行介绍。 具有从网络外部登录的用户的组织应考虑使用使用[WID 和代理拓扑的联合服务器场，](Federation-Server-Farm-Using-WID-and-Proxies.md)或者使用 SQL Server 拓扑的[联合服务器场](Federation-Server-Farm-Using-SQL-Server.md)。  
  
### <a name="what-are-the-benefits-of-using-this-topology"></a>使用此拓扑的好处是什么？  
  
-   为内部用户提供 SSO 访问  
  
-   数据和联合身份验证服务冗余 \(每个联合服务器会将更改复制到相同场中的其他联合服务器\)  
  
-   可以通过添加最多五台联合服务器来向外扩展场  
  
-   WID 包含在 Windows 中;因此，无需购买 SQL Server  
  
### <a name="what-are-the-limitations-of-using-this-topology"></a>使用此拓扑的限制是什么？  
  
-   WID 场限制为五台联合服务器。 有关详细信息，请参阅 [AD FS 部署拓扑注意事项](AD-FS-Deployment-Topology-Considerations.md)。  
  
-   WID 场不支持令牌重播检测或项目解析 \(安全断言标记语言 \(SAML\) 协议\)的一部分。  
  
## <a name="server-placement-and-network-layout-recommendations"></a>服务器布局和网络布局建议  
当你准备好开始在网络中部署此拓扑时，你应该计划将企业网络中的所有联合服务器置于网络负载平衡之后 \(NLB\) 主机，可以使用专用群集域名系统 \(DNS\) 名称和群集 IP 地址为 NLB 群集配置这些服务器。  
  
> [!NOTE]  
> 此群集 DNS 名称必须与联合身份验证服务名称相匹配，例如 fs.fabrikam.com。  
  
NLB 主机可以使用在此 NLB 群集中定义的设置，将客户端请求分配给各个联合服务器。 下图显示了虚构的 Fabrikam，Inc. 公司如何使用两台\-计算机联合服务器场 \(fs1 和 fs2\)，并将 DNS 服务器和单个 NLB 主机连接到公司网络，来设置其部署的第一阶段。  
  
![使用 WID 的服务器场](media/FarmWID.gif)  
  
> [!NOTE]  
> 如果此单个 NLB 主机上出现故障，用户将无法访问联合应用程序或服务。 如果你的业务要求不允许存在单点故障，则应添加其他 NLB 主机。  
  
有关如何配置网络环境以用于联合服务器的详细信息，请参阅 AD FS 设计指南中[联合服务器的名称解析要求](Name-Resolution-Requirements-for-Federation-Servers.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
