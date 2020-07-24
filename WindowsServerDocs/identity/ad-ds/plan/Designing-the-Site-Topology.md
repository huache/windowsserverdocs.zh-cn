---
ms.assetid: eeb919de-e21e-48d8-8186-e42adec6933f
title: 设计站点拓扑
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 23c80ffa3137f5609abdba9abea08ea62d305573
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86963789"
---
# <a name="designing-the-site-topology"></a>设计站点拓扑

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

目录服务站点拓扑是物理网络的逻辑表示形式。 为 Active Directory 域服务（AD DS）设计站点拓扑涉及到规划域控制器放置以及设计站点、子网、站点链接和站点链接桥，以确保有效路由查询和复制流量。  
  
设计站点拓扑有助于有效地路由客户端查询并 Active Directory 复制流量。 设计良好的站点拓扑有助于组织实现以下优势：  
  
-   最大程度地降低复制 Active Directory 数据的成本。  
  
-   最大程度地减少维护站点拓扑所需的管理工作量。  
  
-   计划复制，使具有慢速或拨号网络链接的位置在非高峰时段复制 Active Directory 的数据。  
  
-   优化客户端计算机查找最接近的资源（例如域控制器和分布式文件系统（DFS）服务器）的功能。 这有助于减少跨慢速广域网（WAN）链接的网络流量，改进登录和注销过程，并加速文件下载操作。  
  
在开始设计站点拓扑之前，必须了解物理网络结构。 此外，必须首先为每个林设计 Active Directory 逻辑结构，包括管理层次结构、林计划和域计划。 还必须完成 AD DS 的域名系统（DNS）基础结构设计。 有关设计 Active Directory 逻辑结构和 DNS 基础结构的详细信息，请参阅[设计 Windows Server 2008 的逻辑结构 AD DS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770806(v=ws.10))。  
  
完成站点拓扑设计后，必须验证你的域控制器符合 Windows Server 2008 Standard、Windows Server 2008 Enterprise 和 Windows Server 2008 Datacenter 的硬件要求。  
  
## <a name="in-this-guide"></a>本指南包含的内容  
  
-   [了解 Active Directory 站点拓扑](../../ad-ds/plan/Understanding-Active-Directory-Site-Topology.md)  
  
-   [收集网络信息](../../ad-ds/plan/Collecting-Network-Information.md)  
  
-   [规划域控制器放置](../../ad-ds/plan/Planning-Domain-Controller-Placement.md)  
  
-   [创建站点设计](../../ad-ds/plan/Creating-a-Site-Design.md)  
  
-   [创建站点链接设计](../../ad-ds/plan/Creating-a-Site-Link-Design.md)  
  
-   [创建站点链接桥设计](../../ad-ds/plan/Creating-a-Site-Link-Bridge-Design.md)  
  
-   [查找 Windows Server 2008 Active Directory 站点拓扑设计的其他资源](../../ad-ds/plan/Finding-Additional-Resources-for-Windows-Server-2008-Active-Directory-Site-Topology-Design.md)  
  
