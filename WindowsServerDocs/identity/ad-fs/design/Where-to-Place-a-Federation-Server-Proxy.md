---
ms.assetid: ec26705c-4446-4226-b9b4-b775b642f0f4
title: 联合服务器代理放置位置
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: beef5fb1cc52b5ed3f4c4eafd1fde6a9523c9260
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858450"
---
# <a name="where-to-place-a-federation-server-proxy"></a>联合服务器代理放置位置

您可以在外围网络中放置 Active Directory 联合身份验证服务 \(AD FS\)联合服务器代理，以提供针对可能来自 Internet 的恶意用户的保护层。 联合服务器代理不能访问用于创建令牌的私钥，因此非常适合外围网络环境。 但是，联合服务器代理可以将传入请求高效路由到有权生成这些令牌的联合服务器。  
  
不需要将联合服务器代理放在帐户伙伴或资源伙伴的企业网络内，因为连接到企业网络的客户端计算机可以与联合服务器直接通信。 在此方案中，联合服务器还为来自企业网络的客户端计算机提供联合服务器代理功能。  
  
与外围网络的典型一样，外围网络和企业网络之间建立了一个面向\-intranet 的防火墙，Internet\-的防火墙通常在外围网络和 Internet 之间建立。 在此方案中，联合服务器代理位于外围网络中的这两个防火墙之间。  
  
## <a name="configuring-your-firewall-servers-for-a-federation-server-proxy"></a>配置联合服务器代理的防火墙服务器  
为了使联合服务器代理重定向过程成功，必须将所有防火墙服务器配置为允许安全超文本传输协议 \(HTTPS\) 通信。 需要使用 HTTPS，因为防火墙服务器必须使用端口443发布联合服务器代理，以便外围网络中的联合服务器代理可以访问企业网络中的联合服务器。  
  
> [!NOTE]  
> 与客户端计算机之间的所有通信往来也通过 HTTPS 进行。  
  
此外，Internet\-面向防火墙服务器（例如运行 Microsoft Internet 安全和加速 \(ISA\) 服务器的计算机）使用称为服务器发布的过程将 Internet 客户端请求分发到适当的外围网络服务器和企业网络服务器（例如联合服务器代理或联合服务器）。  
  
服务器发布规则用于确定服务器发布的工作原理，即筛选通过 ISA 服务器计算机的所有传入和传出请求。 服务器发布规则将传入客户端请求映射到 ISA 服务器计算机后的相应服务器。 有关如何配置 ISA 服务器以发布服务器的信息，请参阅[创建安全的 Web 发布规则](https://go.microsoft.com/fwlink/?LinkId=75182)。  
  
在 AD FS 的联合世界中，通常会向特定 URL 发出这些客户端请求，例如 http：\//fs.fabrikam.com 的联合服务器标识符 URL。 因为这些客户端请求来自 Internet，所以面向\-Internet 的防火墙服务器必须配置为发布外围网络中部署的每个联合服务器代理的联合服务器标识符 URL。  
  
### <a name="configuring-isa-server-to-allow-ssl"></a>配置 ISA 服务器为允许使用 SSL  
为了便于安全 AD FS 通信，必须配置 ISA 服务器以允许安全套接字层 \(SSL\) 以下各项之间的通信：  
  
-   **联合服务器和联合服务器代理。** 联合服务器和联合服务器代理之间的所有通信都需要 SSL 通道。 因此，必须配置 ISA 服务器为允许在企业网络和外围网络之间建立 SSL 连接。  
  
-   **客户端计算机、联合服务器和联合服务器代理。** 为了在客户端计算机与联合服务器之间或客户端计算机与联合服务器代理之间进行通信，你可以将运行 ISA 服务器的计算机放在联合服务器或联合服务器代理的前面。  
  
    如果你的组织在联合服务器或联合服务器代理上执行 SSL 客户端身份验证，则将运行 ISA 服务器的计算机放在联合服务器或联合服务器代理的前面时，必须将服务器配置为通过 SSL 连接进行传递\-，因为 SSL 连接必须在联合服务器或联合服务器代理上终止。  
  
    如果你的组织不在联合服务器或联合服务器代理上执行 SSL 客户端身份验证，另一个选项是在运行 ISA Server 的计算机上终止 SSL 连接，然后重新\-与联合服务器或联合服务器代理建立 SSL 连接。  
  
> [!NOTE]  
> 联合服务器或联合服务器代理要求连接受 SSL 保护，以保护安全令牌的内容。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
