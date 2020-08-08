---
ms.assetid: 4d002764-58b4-4137-9c86-1e55b02e07ce
title: 配置合作伙伴组织
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 123968fdc9ce9e30b3cf78d25fe37b30e46fd473
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87962971"
---
# <a name="configuring-partner-organizations"></a>配置合作伙伴组织

若要在 Active Directory 联合身份验证服务 AD FS 中部署新的合作伙伴组织 \( \) ，请完成以下任一清单中的任务[：配置资源伙伴组织](Checklist--Configuring-the-Resource-Partner-Organization.md)或[清单：配置帐户伙伴组织](Checklist--Configuring-the-Account-Partner-Organization.md)，具体取决于你的 AD FS 设计。

> [!NOTE]
> 使用上述任一清单时，我们强烈建议您先阅读[Windows Server 2012 的 "AD FS 设计指南](../design/ad-fs-design-guide-in-windows-server-2012.md)" 中的帐户伙伴或资源伙伴计划指南，然后再继续执行设置新的合作伙伴组织的步骤。 以这种方式遵循清单将有助于更好地了解帐户伙伴或资源伙伴组织的完整 AD FS 设计和部署案例。

## <a name="about-account-partner-organizations"></a>关于帐户伙伴组织
帐户伙伴是联合身份验证信任关系中的组织，以物理方式将用户帐户存储在 AD FS 支持的属性存储中。 帐户伙伴负责收集和验证用户凭据、累积该用户的声明并将声明封装到安全令牌中。 然后，可以通过联合身份验证信任提供这些令牌，以允许访问 \- 资源伙伴组织中基于 Web 的资源。

换句话说，帐户伙伴代表其用户帐户 \- 端联合服务器颁发安全令牌的组织。 帐户伙伴组织中的联合服务器对本地用户进行身份验证，并创建资源伙伴在做出授权决定时使用的安全令牌。

对于属性存储，AD FS 中的帐户伙伴在概念上等效于单个 Active Directory 林，其帐户需要访问物理上位于另一个林中的资源。 只有当两个林之间存在外部信任或林信任关系并且用户尝试访问的资源已使用适当的授权权限进行设置时，此林中的帐户才能访问资源林中的资源。

## <a name="about-resource-partner-organizations"></a>关于资源伙伴组织
资源伙伴是 Web 服务器所在 AD FS 部署中的组织。 资源伙伴信任帐户伙伴对用户进行身份验证。 因此，若要做出授权决策，资源伙伴需使用由帐户伙伴中的用户提供的安全令牌中的声明。

换句话说，资源伙伴代表其 Web 服务器受资源 \- 端联合服务器保护的组织。 资源伙伴中的联合服务器使用由帐户伙伴生成的安全令牌为资源伙伴中的 Web 服务器做出授权决策。

若要作为 AD FS 资源运行，资源伙伴组织中的 Web 服务器必须安装 Windows Identity Foundation \( WIF， \) 或者安装了 Active Directory 联合身份验证服务 \( AD FS 1.X \) 声明 \- 感知 Web 代理角色服务。 作为 AD FS 资源的 web 服务器可以托管 \- 基于 web 浏览器 \- 或 \- 基于 web 服务的 \- 应用程序。
