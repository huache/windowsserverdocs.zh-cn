---
ms.assetid: 39acccd9-0402-49ca-8ce1-b239e1e7e455
title: 在资源伙伴组织中部署 AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: ae43da6a8aa2968cc5123c9bc707c44c77fa6ea2
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87942912"
---
# <a name="deploying-ad-fs-in-the-resource-partner-organization"></a>在资源伙伴组织中部署 AD FS

Active Directory 联合身份验证服务 AD FS 中的资源伙伴 \( 组织 \) 表示其 Web 服务器可能受资源 \- 端联合服务器保护的组织。 资源伙伴中的联合服务器使用由帐户伙伴生成的安全令牌向位于资源伙伴中的 Web 服务器提供声明。

在需要向多个不同用户（某些用户位于不同的组织中）提供对联合服务或应用程序的访问权限的情况下，你可以配置资源联合服务器，以便可以部署多个帐户伙伴。

有关如何设置和配置资源伙伴组织的详细信息，请参阅 [Checklist: Configuring the Resource Partner Organization](../../ad-fs/deployment/Checklist--Configuring-the-Resource-Partner-Organization.md)。

## <a name="in-this-section"></a>本节内容

-   [查看联合服务器在资源伙伴中的角色](Review-the-Role-of-the-Federation-Server-in-the-Resource-Partner.md)

-   [查看联合服务器代理在资源伙伴中的角色](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Resource-Partner.md)

-   [确定资源伙伴中的联合应用程序策略](Determine-Your-Federated-Application-Strategy-in-the-Resource-Partner.md)


## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
