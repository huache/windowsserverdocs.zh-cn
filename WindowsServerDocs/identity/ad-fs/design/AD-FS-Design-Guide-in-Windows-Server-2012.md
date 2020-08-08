---
ms.assetid: bb16e39d-566d-436c-b957-394c06d556db
title: Windows Server 2012 中的 AD FS 设计指南
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: c9089a3eac4d0ba6f4961f97fcb87b4e9a1a8c91
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87949911"
---
# <a name="ad-fs-legacy-design-guide-in-windows-server"></a>Windows Server 中的 AD FS 旧版设计指南



> [!NOTE]
> 有关如何在 Windows Server 2012 R2 中部署 AD FS 的信息，请参阅[Windows server 2012 r2 AD FS 部署指南](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)。

你可以使用 &reg; \( 联合身份验证服务 \) 提供程序角色中的 Windows Server 2012 操作系统 Active Directory 联合身份验证服务 AD FS &reg; 将用户无缝地验证到任何 \- 基于 Web 的服务或位于资源伙伴组织中的应用程序，而无需管理员在两个组织的网络之间创建或维护外部信任或林信任，而不需要用户第二次登录。 在访问另一个网络中的资源时对一个网络进行身份验证的过程（无需用户重复登录操作的负担）称为 "单一登录 \- \( SSO" \) 。

## <a name="about-this-guide"></a>关于本指南
本指南提供了一些建议，以帮助你根据组织的要求（在 \( 本指南中也称为部署目标） \) 和你想要创建的特定设计来计划新的 AD FS 部署。 本指南供基础结构专家或系统架构师使用。 当你计划 AD FS 部署时，它将重点介绍你的主要决策点。 阅读本指南之前，应充分了解 AD FS 在功能级别上的工作方式。 你还应充分了解将反映在 AD FS 设计中的组织要求。

本指南介绍了一套基于三个主要 AD FS 设计的部署目标，并可帮助你确定适用于你的环境的最佳设计。 你可以使用这些部署目标来形成以下综合性 AD FS 设计或满足你的环境需要的自定义设计：

-   联合 Web SSO 支持企业 \- 到 \- 企业 \( B2B \) 方案，并支持具有独立林的业务部门之间的协作

-   用于支持客户访问企业 \- 对 \- 消费者 \( B2C \) 方案的应用程序的 Web SSO

对于每个设计，你可以找到用于收集所需的有关你的环境的数据。 然后，你可以使用这些指南来规划和设计你的 AD FS 部署。 阅读本指南并完成收集、记录和映射你的组织的要求后，你将获得使用[Windows Server 2012 AD FS 部署指南](../../ad-fs/deployment/Windows-Server-2012-AD-FS-Deployment-Guide.md)中的指导开始部署 AD FS 所需的信息。

## <a name="in-this-guide"></a>本指南包含的内容

-   [标识 AD FS 部署目标](Identifying-Your-AD-FS-Deployment-Goals.md)

-   [将部署目标映射到 AD FS 设计](Mapping-Your-Deployment-Goals-to-an-AD-FS-Design.md)

-   [确定 AD FS 部署拓扑](Determine-Your-AD-FS-Deployment-Topology.md)

-   [规划部署](Planning-Your-Deployment.md)

-   [规划联合服务器的位置](Planning-Federation-Server-Placement.md)

-   [规划联合服务器代理的位置](Planning-Federation-Server-Proxy-Placement.md)

-   [AD FS 服务器容量规划](Planning-for-AD-FS-Server-Capacity.md)

-   [附录 A：查看 AD FS 要求](Appendix-A--Reviewing-AD-FS-Requirements.md)


