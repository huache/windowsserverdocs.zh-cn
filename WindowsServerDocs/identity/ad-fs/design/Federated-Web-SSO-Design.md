---
ms.assetid: 09f335bb-896a-45dd-adc2-f215b8fba828
title: 联合 Web SSO 设计
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 6a3e7eb6c42c8190da799c88c1e947e6aef1c29f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408101"
---
# <a name="federated-web-sso-design"></a>联合 Web SSO 设计

\(SSO 上的联合 Web 单一\-SSO\) 设计\-Active Directory 联合身份验证服务 \(AD FS\) 包括跨多个防火墙、外围网络和名称\-解析服务器的安全通信，以及整个 Internet 路由基础结构。  
  
通常，当两个组织同意创建联合信任关系以允许一个组织中的用户 \(帐户伙伴组织\) 在资源伙伴组织 \(的其他组织中访问 AD FS 所保护的基于\-Web 的应用程序或服务时，将使用此设计。\)  
  
换句话说，联合信任关系是两个组织之间的业务\-级别协议或合作关系的体现。 如下图所示，可以在两个企业之间建立联合身份验证信任关系，这将导致最终\-\-结束联合方案。  
  
![联合的 web sso](media/adfs2_FederatedWebSSODesign.gif)  
  
图中的一个\-方式箭头表示联合身份验证信任的方向，这与 Windows 信任的方向类似，它始终指向林的帐户端。 这意味着，身份验证将从帐户伙伴组织流向资源伙伴组织。  
  
在此联合 Web SSO 设计中，两个联合服务器 \(Fabrikam 中的一个，而另一个在 Contoso 中\) 将来自 Fabrikam 中用户帐户的身份验证请求路由到 Contoso 中基于 Web\-的应用程序或服务。  
  
> [!NOTE]  
> 为了进一步提高安全性，你可以使用联合服务器代理将请求中继到无法从 Internet 直接访问的联合服务器。  
  
在此示例中，Fabrikam 是标识、帐户或提供程序。 联合 Web SSO 设计的 Fabrikam 部分使用以下 AD FS 部署目标：  
  
-   [为其他组织的应用程序和服务提供 Active Directory 用户访问权限](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)  
  
Contoso 是资源提供单元。 联合 Web SSO 设计的 Contoso 部分实现了以下 AD FS 部署目标：  
  
-   [为另一个组织中的用户提供对声明感知应用程序和服务的访问权限](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)  
  
-   [为声明感知应用程序和服务提供 Active Directory 用户访问权限](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)  
  
有关可用于计划和部署联合 Web SSO 设计的详细任务的列表，请参阅 [Checklist: Implementing a Federated Web SSO Design](../../ad-fs/deployment/Checklist--Implementing-a-Federated-Web-SSO-Design.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
