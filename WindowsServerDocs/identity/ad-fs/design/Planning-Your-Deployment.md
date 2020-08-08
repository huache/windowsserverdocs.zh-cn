---
ms.assetid: bb9b9e18-bf2f-4115-be77-9a165944db41
title: 规划你的部署
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 9ada8872c7d74e4a0a10504ffaf34a235536dcbb
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954313"
---
# <a name="planning-your-deployment"></a>规划你的部署

当你 \- \( \- 使用 Active Directory 联合身份验证服务 AD FS 计划基于组织联合的协作时 \) \( \) ，请首先确定你的组织是否将承载由其他组织通过 Internet 访问的 web 资源，或你是否为组织中的员工提供对 web 资源的访问权限。 此结果会影响部署 AD FS 的方式，是计划 AD FS 结构中的基础。

> [!NOTE]
> 请确保所有各方都清楚地了解组织在联合协议中所扮演的角色。

对于[联合 WEB SSO 设计](Federated-Web-SSO-Design.md)，AD FS 使用*帐户伙伴*等术语，在 " \( AD FS 管理" 管理单元中也称为 "*标识提供者*" \- ，在 \) *resource partner* \( "AD FS 管理" 管理单元中也称为 "*信赖方*"， \- \) 以帮助将托管帐户 \( 的组织 \) 从托管基于 Web 的资源的组织（ \- \( 资源伙伴） \) 。

在 [Web SSO Design](Web-SSO-Design.md)中，组织同时扮演帐户伙伴和资源伙伴角色，因为它会向其用户提供对其应用程序的访问。

以下主题介绍了 AD FS 的合作伙伴组织概念。 它们还包含有关基于 AD FS 部署目标设置和配置帐户伙伴组织和资源伙伴组织的信息 AD FS 部署指南中的主题的链接。

## <a name="in-this-section"></a>本节内容

-   [AD FS 安全规划和部署的最佳做法](Best-Practices-for-Secure-Planning-and-Deployment-of-AD-FS.md)

-   [规划与 AD FS 1.x 的互操作性](Planning-for-Interoperability-with-AD-FS-1.x.md)

-   [何时使用标识委派](When-to-Use-Identity-Delegation.md)

-   [在帐户伙伴组织中部署 AD FS](Deploying-AD-FS-in-the-Account-Partner-Organization-2012.md)

-   [在资源伙伴组织中部署 AD FS](Deploying-AD-FS-in-the-Resource-Partner-Organization-2012.md)

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)


