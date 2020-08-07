---
ms.assetid: f88238ea-d851-4129-8b4e-a3a62b813614
title: 查看联合服务器在资源伙伴中的角色
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: b090384cebd5213ec10799f4b2c0d594de3a3fd6
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972064"
---
# <a name="review-the-role-of-the-federation-server-in-the-resource-partner"></a>查看联合服务器在资源伙伴中的角色

资源伙伴组织中的联合服务器截获由帐户联合服务器发送的传入安全令牌，对其进行验证和签名，然后颁发其自己的基于 Web 应用程序的安全令牌 \- 。

> [!NOTE]
> 当联合用户使用他们的 Web 浏览器访问 \- 基于 web 的应用程序时，资源伙伴组织中的联合服务器将生成新的身份验证 cookie 并将其写入浏览器。 此 cookie 启用单一 \- 登录 \- \( SSO 功能，使用户在 \) 尝试访问 \- 资源伙伴中基于 Web 的不同应用程序时，不必重新登录帐户伙伴中的联合服务器。

在 Web SSO 设计中，必须在外围网络中安装至少一台联合服务器。 在联合 Web SSO 设计中，至少必须在帐户伙伴组织的企业网络中安装至少一台联合服务器，并在资源伙伴组织的企业网络中安装至少一台联合服务器。

> [!NOTE]
> 必须先将计算机加入资源伙伴组织中的任何 Active Directory 域，然后才能在资源伙伴组织中设置联合服务器计算机。 有关详细信息，请参阅 [Checklist: Setting Up a Federation Server](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md)。

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)

