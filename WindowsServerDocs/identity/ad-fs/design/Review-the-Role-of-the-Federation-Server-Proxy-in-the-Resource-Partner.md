---
ms.assetid: 14aa112d-ae31-4181-97e4-92623b5c9270
title: 查看联合服务器代理在资源伙伴中的角色
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: b431d14abfa66ceb70e5885b4301648936c4c4ff
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969684"
---
# <a name="review-the-role-of-the-federation-server-proxy-in-the-resource-partner"></a>查看联合服务器代理在资源伙伴中的角色

Active Directory 联合身份验证服务 AD FS 中的联合服务器 \( 代理 \) 可在以下一个或多个角色中工作，具体取决于你如何配置服务器来满足资源伙伴组织的需求：

-   **帐户伙伴发现**：Internet 客户端计算机必须确定将对其进行身份验证的帐户伙伴。 客户端使用帐户伙伴发现 Web 窗体 discoverclientrealm.aspx 查找帐户伙伴 \( ，该窗体 \) 存储在资源伙伴中的联合服务器代理上。 如果在 AD FS 管理 "管理单元中配置了多个帐户伙伴 \- ，则会向客户端显示一个下拉菜单，其中 \- 包含对访问帐户伙伴发现 Web 窗体的 Internet 客户端计算机可见的所有可用帐户伙伴。 你可以通过自定义 discoverclientrealm.aspx 文件来更改帐户伙伴发现 Web 窗体对客户端计算机的呈现方式。

-   **安全令牌重定向**：帐户伙伴中的联合服务器代理将安全令牌发送给资源伙伴。 资源联合服务器代理接受这些令牌并将它们传递给资源伙伴中的联合服务器。 然后，资源联合服务器颁发一个与特定资源 Web 服务器绑定的安全令牌。 然后，资源联合服务器代理会将该令牌重定向到客户端。

总而言之，资源联合服务器代理通过将客户端计算机重定向到可以对客户端进行身份验证的联合身份验证服务器，来简化联合登录过程。 资源联合服务器代理也充当资源联合服务器的客户端安全令牌代理。

> [!NOTE]
> 如果需要帮助减少硬件和所需证书的数量，联合服务器代理可以与 Web 服务器位于同一台计算机上。

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)

