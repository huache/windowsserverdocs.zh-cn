---
ms.assetid: bb9b9e18-bf2f-4115-be77-9a165944db41
title: 规划部署
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 6386aac112fcf936ccdd9772e3d5566d8dd21ad8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858640"
---
# <a name="planning-your-deployment"></a>规划部署

当你使用 Active Directory 联合身份验证服务 \(AD FS\)规划跨\-组织 \(联合\-的\) 协作时，请首先确定你的组织是否将托管要由其他组织通过 Internet 访问的 Web 资源，或你是否为组织中的员工提供对 Web 资源的访问权限。 这种决定会影响你部署 AD FS 的方式，这在规划你的 AD FS 基础结构方面是基本的。  
  
> [!NOTE]  
> 请确保所有各方都清楚地了解组织在联合协议中所扮演的角色。  
  
对于[联合 WEB SSO 设计](Federated-Web-SSO-Design.md)，AD FS 使用*帐户伙伴*\(等术语在 AD FS 管理 "管理器" 中的 "管理" 管理单元\-中称为 "*标识提供者*"。\) 中的 "管理" 管理单元 \(也称为 "*依赖方*" *AD FS，这*有助于区分托管帐户的组织\-\) 资源伙伴 \(的基于 Web\) 资源的组织。\-\(\)  
  
在 [Web SSO Design](Web-SSO-Design.md)中，组织同时扮演帐户伙伴和资源伙伴角色，因为它会向其用户提供对其应用程序的访问。  
  
以下主题介绍了 AD FS 的合作伙伴组织概念。 它们还包含有关基于 AD FS 部署目标设置和配置帐户伙伴组织和资源伙伴组织的信息 AD FS 部署指南中的主题的链接。  
  
## <a name="in-this-section"></a>本部分内容  
  
-   [AD FS 安全规划和部署的最佳做法](Best-Practices-for-Secure-Planning-and-Deployment-of-AD-FS.md)  
  
-   [规划与 AD FS 1.x 的互操作性](Planning-for-Interoperability-with-AD-FS-1.x.md)  
  
-   [何时使用标识委派](When-to-Use-Identity-Delegation.md)  
  
-   [在帐户伙伴组织中部署 AD FS](Deploying-AD-FS-in-the-Account-Partner-Organization-2012.md)  
  
-   [在资源伙伴组织中部署 AD FS](Deploying-AD-FS-in-the-Resource-Partner-Organization-2012.md)  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)


