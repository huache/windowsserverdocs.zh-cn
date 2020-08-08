---
ms.assetid: 935ea7c2-4678-4033-b50f-2036a0359c5d
title: 联合服务器的放置位置
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: d459ca354a462912c6343d6d6397222fa483b45a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87962651"
---
# <a name="where-to-place-a-federation-server"></a>联合服务器的放置位置

作为最佳安全方案，请将 Active Directory 联合身份验证服务 \( AD FS \) 在防火墙后面的联合服务器，并将它们连接到企业网络以防止从 Internet 暴露。 这一点很重要，因为联合服务器具有授予安全令牌的完全授权。 因此，它们应具有与域控制器相同的保护。 如果联合服务器受到威胁，则恶意用户能够向所有 Web 应用程序以及 \( \) 在所有资源伙伴组织中 Active Directory 联合身份验证服务 AD FS 保护的联合服务器颁发完全访问令牌。

> [!NOTE]
> 作为安全方面的最佳做法，请避免在 Internet 上直接访问联合服务器。 请考虑仅当设置测试实验室环境或组织没有外围网络时，为联合服务器提供直接 Internet 访问权限。

对于典型的企业网络， \- 企业网络和外围网络之间建立了面向 intranet 的防火墙，并且 \- 通常在外围网络和 Internet 之间建立面向 Internet 的防火墙。 在这种情况下，联合服务器位于企业网络内部，Internet 客户端不能直接对其进行访问。

> [!NOTE]
> 连接到企业网络的客户端计算机可以通过 Windows 集成身份验证直接与联合服务器通信。

在配置防火墙服务器以与 AD FS 一起使用之前，联合服务器代理应放置在外围网络中。 有关详细信息，请参阅[放置联合服务器代理的位置](Where-to-Place-a-Federation-Server-Proxy.md)。

## <a name="configuring-your-firewall-servers-for-a-federation-server"></a>为联合服务器配置防火墙服务器
为了使联合服务器可以直接与联合服务器代理进行通信，intranet 防火墙服务器必须配置为允许将安全超文本传输协议 \( HTTPS \) 流量从联合服务器代理发送到联合服务器。 这是一项要求，因为 intranet 防火墙服务器必须使用端口443发布联合服务器，以便外围网络中的联合服务器代理可以访问联合服务器。

此外，面向 intranet 的 \- 防火墙服务器（例如运行 Internet 安全和加速 ISA 服务器的服务器 \( ） \) 使用称为服务器发布的过程将 Internet 客户端请求分发到适当的企业联合服务器。 这意味着必须在运行 ISA 服务器的 intranet 服务器上手动创建发布群集联合服务器 URL 的服务器发布规则，例如 http： \/ \/ fs.fabrikam.com。

有关如何在外围网络中配置服务器发布的详细信息，请参阅 [Where to Place a Federation Server Proxy](Where-to-Place-a-Federation-Server-Proxy.md)。 有关如何配置 ISA 服务器以发布服务器的信息，请参阅[创建安全的 Web 发布规则](https://go.microsoft.com/fwlink/?LinkId=75182)。

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
