---
ms.assetid: a8558c9d-0606-4881-93b2-f2d2716b18e7
title: Windows Server 2012 R2 中的 AD FS 设计指南
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: e8675c255032bca4623a9649bfc0bcca478008e3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854890"
---
# <a name="ad-fs-design-guide-in-windows-server"></a>Windows Server 中 AD FS 设计指南 

Active Directory 联合身份验证服务 \(AD FS\) 为想要访问\-\(安全企业、联合伙伴组织或云中的应用程序的最终用户提供简化、安全的联合身份验证和 Web 单一签名\)。\-  
  
在 Windows Server&reg; 2012 R2 中，AD FS 包括充当标识提供者的联合身份验证服务角色服务，\(对用户进行身份验证以向信任 AD FS\) 或作为联合身份验证提供程序的应用程序提供安全令牌 \(使用其他标识提供者的令牌，然后为信任 AD FS\)的应用程序提供安全令牌。  
  
现在由一个称为 Web 应用程序代理的新远程访问角色服务来提供对在 Windows Server 2012 R2 中受 AD FS 保护的应用程序和服务的 Extranet 访问。 这与之前版本的 Windows Server 使用 AD FS 联合服务器代理处理此功能有所不同。 Web 应用程序代理是一种服务器角色，旨在为 AD FS\-相关 extranet 方案和其他 extranet 方案提供访问权限。 有关 Web 应用程序代理的详细信息，请参阅[Web 应用程序代理操作实例指南](https://technet.microsoft.com/library/dn280944.aspx)。  
  
## <a name="about-this-guide"></a>关于本指南  
本指南提供了一些建议，以帮助你根据组织的要求规划 AD FS 的新部署。 本指南供基础结构专家或系统架构师使用。 当你计划 AD FS 部署时，它将重点介绍你的主要决策点。 阅读本指南之前，应充分了解 AD FS 在功能级别上的工作方式。 有关详细信息，请参阅 [Understanding Key AD FS Concepts](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)。  
  
## <a name="in-this-guide"></a>本指南内容  
  
-   [标识 AD FS 部署目标](Identify-Your-AD-FS-Deployment-Goals.md)  
  
-   [规划 AD FS 部署拓扑](Plan-Your-AD-FS-Deployment-Topology.md)  
  
-   [AD FS 要求](AD-FS-Requirements.md)  
  
  
## <a name="see-also"></a>另请参阅  
[AD FS 设计](../../ad-fs/AD-FS-Design.md)  
  

