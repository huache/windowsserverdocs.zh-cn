---
ms.assetid: ef91f1d8-2991-4d90-b687-5fa189737c88
title: AD FS 服务器容量规划
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 984579813a843e6c39bd85bb9aa07cdddfcfc067
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858630"
---
# <a name="planning-for-ad-fs-server-capacity"></a>AD FS 服务器容量规划


  
> [!NOTE]  
> 本主题中提供的内容不反映运行 Windows Server 2012 的服务器上执行的实际测试。 本主题将在所需的测试已执行后立即进行更新。  
  
针对 Active Directory 联合身份验证服务 \(AD FS\) 的容量规划是预测联合身份验证服务的高峰使用期和规划或缩放的过程，\-服务器部署来满足这些负载要求。  
  
本部分介绍联合服务器和联合服务器代理角色的部署指南，并且基于 Microsoft 的 AD FS 产品团队执行的实验室测试。 此内容的目的是帮助你：  
  
-   仔细估计组织特定 AD FS 部署的硬件需求，如 AD FS 服务器的数量。  
  
-   准确投影请求中签名\-的预期高峰使用情况、规划增长，并确保 AD FS 部署能够处理预期的高峰使用情况。  
  
在继续阅读此容量规划内容之前，我们建议你先按照以下两个表中所示的顺序完成任务。 在第一个表中，我们提供了建议任务的链接，这些任务将有助于为此容量规划讨论提供相关的上下文。  
  
|建议的任务|说明|参考|  
|--------------------|---------------|-------------|  
|了解部署 AD FS 联合服务器和联合服务器代理的要求|查看部署联合服务器和联合服务器代理所需的重要硬件和软件要求。|[附录 A：查看 AD FS 要求](Appendix-A--Reviewing-AD-FS-Requirements.md)|  
|选择将在你的组织中部署 AD FS 配置数据库的类型|在开始使用此部分中的容量规划数据之前，首先必须确定要部署的 AD FS 配置数据库类型，是 Windows 内部数据库 \(WID\) 或结构化查询语言 \(SQL\) 数据库。|[The Role of the AD FS Configuration Database](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)；<p>[AD FS 部署拓扑注意事项](AD-FS-Deployment-Topology-Considerations.md)|  
|确定可用于新的 AD FS 配置数据库选择的拓扑布局的类型。|一旦你已决定要在部署中使用的 AD FS 配置数据库的类型，你将需要考虑在生产环境中哪种部署拓扑最匹配将需要放置联合服务器和联合服务器代理的位置。|[确定 AD FS 部署拓扑](Determine-Your-AD-FS-Deployment-Topology.md)|  
|了解关键 AD FS 相关容量规划术语|查看在整个 AD FS 容量规划讨论中使用的常见容量规划术语的定义。|请参阅本主题中标题为 [AD FS 容量规划术语](Planning-for-AD-FS-Server-Capacity.md#bk_terms)的部分|  
  
在查看完上一个表中的内容后，现在就可以完成下一个表中的必备任务。  
  
|必备任务|说明|参考|  
|---------------------|---------------|-------------|  
|下载 AD FS 容量规划大小调整电子表格|AD FS 容量规划大小调整电子表格可以帮助你确定 AD FS 联合服务器场部署所需的联合服务器的数目。 下面为下一项任务提供的链接中提供了有关如何使用该电子表格的说明。|[AD FS 容量规划电子表格](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacityPlanning.xlsx)|  
|收集有关在 \(SSO 上需要单一登录\-的用户数的数据\) 访问目标声明\-感知应用程序以及与此访问相关联的预期高峰使用时间段|所收集的此用户数据将用于 AD FS 容量规划大小调整电子表格的上下文中所需的输入值。|[估计组织的联合服务器的数目](Planning-for-Federation-Server-Capacity.md#bk_estimatefs)|  
|Windows Server 2016 AD FS 容量规划电子表格|已更新 Windows Server 2016 计划工作表|[AD FS Windows Server 2016 容量规划](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx)  
  
## <a name="ad-fs-capacity-planning-terms"></a><a name="bk_terms"></a>AD FS 容量规划术语  
下表描述了 "AD FS 设计指南" 的 "容量规划" 一节中经常使用的重要术语。 有关 AD FS 术语的更完整列表，请参阅[了解关键 AD FS 概念](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)。  
  
|术语|Definition|  
|--------|--------------|  
|并发用户|预期将在给定时间段内（通常为高峰活动期间）向服务提交请求的用户的估计数目。|  
|活动用户|在系统上处于活动状态（但不一定在给定时间段内提交请求）的用户的大致平均数。|  
|已定义的用户|理论上的最大用户数，通常基于已经在系统中定义帐户的用户数。|  
|每秒请求数|\(在谈论系统上的负载时，由客户端提交的请求数\) 或由服务器处理的请求数，\(在谈论服务器吞吐量时\)。 此指标用于规划服务器处理器和内存容量。|  
|目标服务器的响应速度和使用率|绑定可接受的服务器性能范围的成功度量标准。 通常情况下，如果响应速度低于目标或利用率超过目标，则系统将被视为过载，并需要更多的容量。|  
|Windows Internal Database \(WID\)|默认 AD FS 配置数据库，该数据库可用作特定 AD FS 部署中 SQL Server 的替代方法。|  
  
## <a name="configuration-environment-used-during-ad-fs-testing"></a>AD FS 测试过程中使用的配置环境  
本部分介绍 AD FS 产品团队用于执行其测试的配置环境。 在联合服务器的测试中，该团队使用了以下计算机硬件、软件和网络配置来收集性能和可伸缩性数据：  
  
-   双四核2.27 千兆赫 \(GHz\) \(8 个核心\)  
  
-   16\-GB RAM  
  
-   Windows Server 2008 R2（企业版）  
  
-   千兆位网络  
  
> [!NOTE]  
> 尽管在测试期间在联合服务器上使用了 16 GB 的 RAM，但更适中的内存大小（例如每个联合服务器有 4 GB 的 RAM）可用于大多数 AD FS 的部署。 此 AD FS 容量规划内容中提供的建议以及 AD FS 容量规划电子表格所提供的结果，都基于假设每个联合服务器将对大多数 AD FS 生产环境使用大约 4 Gb 的 RAM。  
  
产品团队使用了以下配置为联合服务器代理测试收集性能和可伸缩性数据：  
  
-   双四核 2.24 GHz \(4 核心\)  
  
-   4\-GB RAM  
  
-   Windows Server 2008 R2（企业版）  
  
-   千兆位网络  
  
> [!NOTE]  
> AD FS 服务器的容量建议可能千差万别，具体取决于为要在给定环境中使用的硬件和网络配置选择的规格。 作为参考，此内容中提供的大小调整指南将基于前面所述的计算机上 80% 的利用率目标。  
  
## <a name="measure-ad-fs-server-capacity"></a>测量 AD FS 服务器容量  
通常，可影响服务器的性能和可伸缩性的硬件组件包括 CPU、内存、磁盘和网络适配器。 幸运的是，每个 AD FS 组件都需要很少的内存和磁盘空间需求。 网络连接是一个明显的要求。 因此，在联合服务器和联合服务器代理上执行的负载测试将集中用于测量服务器容量的两个主要方面：  
  
-   **每秒最大 AD FS 请求数：** 在联合服务器上每秒处理的请求中的签名\-数量。 此测量值可帮助你确定有多少个用户可以同时登录到给定的服务器。 你可以将此测量值与 CPU 消耗测量值结合使用以了解此测量值对性能的影响。  
  
-   **CPU 消耗：** 测量的 CPU 容量百分比。 此测量值可帮助你确定基于每秒请求中传入的签名\-数发生的总体 CPU 负载。  
  
## <a name="continue-reading-more-about-ad-fs-capacity-planning"></a>继续阅读有关 AD FS 容量规划的详细信息  
完成必备任务并熟悉相关术语和硬件要求后，你可以使用以下额外的容量规划内容来帮助你确定部署所需的 AD FS 服务器的建议数量：  
  
-   [联合服务器容量规划](Planning-for-Federation-Server-Capacity.md)  
  
-   [联合服务器代理容量规划](Planning-for-Federation-Server-Proxy-Capacity.md)  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
