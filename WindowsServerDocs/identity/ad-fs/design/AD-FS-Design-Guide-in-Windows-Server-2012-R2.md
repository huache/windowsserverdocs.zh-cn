---
ms.assetid: a8558c9d-0606-4881-93b2-f2d2716b18e7
title: Windows Server 2012 R2 中的 AD FS 设计指南
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 6ec9826ce2015197d96a182864807646a6b8115d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87940403"
---
# <a name="ad-fs-design-guide-in-windows-server"></a>Windows Server 中 AD FS 设计指南

Active Directory 联合身份验证服务 \( AD FS \) \- \( \) 为想要 \- 在受保护 AD FS 的企业内、联合伙伴组织中或云中访问应用程序的最终用户提供简化、安全的联合身份验证和 Web 单一登录 SSO 功能。

在 Windows Server &reg; 2012 R2 中，AD FS 包括一个联合身份验证服务角色服务，该服务可充当标识提供者对 \( 信任 AD FS 的应用程序 \) 或作为联合身份验证提供程序使用其他标识提供程序的令牌的应用程序提供安全令牌 \( ，并为信任 AD FS 的应用程序提供安全令牌 \) 。

现在由一个称为 Web 应用程序代理的新远程访问角色服务来提供对在 Windows Server 2012 R2 中受 AD FS 保护的应用程序和服务的 Extranet 访问。 这与以前的 Windows Server 版本不同，在那些版本中，此功能由 AD FS 联合服务器代理进行处理。 Web 应用程序代理是一种服务器角色，旨在为 AD FS \- 相关 extranet 方案和其他 extranet 方案提供访问权限。 有关 Web 应用程序代理的详细信息，请参阅[Web 应用程序代理操作实例指南](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280944(v=ws.11))。

## <a name="about-this-guide"></a>关于本指南
本指南提供了一些建议，以帮助你根据组织的要求规划 AD FS 的新部署。 本指南供基础结构专家或系统架构师使用。 当你计划 AD FS 部署时，它将重点介绍你的主要决策点。 阅读本指南之前，应充分了解 AD FS 在功能级别上的工作方式。 有关详细信息，请参阅 [Understanding Key AD FS Concepts](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)。

## <a name="in-this-guide"></a>本指南包含的内容

-   [标识 AD FS 部署目标](Identify-Your-AD-FS-Deployment-Goals.md)

-   [规划 AD FS 部署拓扑](Plan-Your-AD-FS-Deployment-Topology.md)

-   [AD FS 要求](AD-FS-Requirements.md)


## <a name="see-also"></a>另请参阅
[AD FS 设计](../../ad-fs/AD-FS-Design.md)

