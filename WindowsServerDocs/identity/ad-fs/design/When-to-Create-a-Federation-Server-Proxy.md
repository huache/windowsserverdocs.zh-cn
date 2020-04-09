---
ms.assetid: aa20c8b3-7f01-4165-8b73-92642bff9676
title: 何时创建联合服务器代理
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 13ca7d49e8044273c9f40e58c06e705e758c68bf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858480"
---
# <a name="when-to-create-a-federation-server-proxy"></a>何时创建联合服务器代理

在组织中创建联合服务器代理会将额外的安全层添加到 Active Directory 联合身份验证服务 \(AD FS\) 部署。 当你想要执行以下操作时，请考虑在组织的外围网络中部署联合服务器代理：  
  
-   阻止外部客户端计算机直接访问你的联合服务器。 通过在外围网络中部署联合服务器代理，可以有效地隔离联合服务器，以便只能通过联合服务器代理（代表外部客户端计算机）登录到企业网络的客户端计算机来访问它们。 联合服务器代理不能访问用于生成令牌的私钥。 有关详细信息，请参阅 [Where to Place a Federation Server Proxy](Where-to-Place-a-Federation-Server-Proxy.md)。  
  
-   提供一种简便的方法来区分来自 Internet 的用户的登录\-，而不是使用 Windows 集成身份验证从公司网络访问的用户。 联合服务器代理使用登录、注销和标识提供程序发现 \(\) 存储在联合服务器代理上的页，从 Internet 客户端计算机中收集凭据或主页领域详细信息。  
  
    与此相反，来自企业网络的客户端计算机会根据联合服务器的配置体验到不同的体验。 企业网络联合服务器通常配置为使用 Windows 集成身份验证，为企业网络上的用户提供无缝签名\-。  
  
联合服务器代理在你的组织中扮演的角色取决于你是将联合服务器代理放在帐户伙伴组织中还是资源伙伴组织中。 例如，将联合服务器代理放在帐户伙伴的外围网络中时，其角色是从浏览器客户端收集用户凭据信息。 将联合服务器代理放在资源伙伴的外围网络中时，它将向资源联合服务器中继安全令牌请求，并生成组织安全令牌来响应由其帐户伙伴提供的安全令牌。  
  
有关详细信息，请参阅 [Review the Role of the Federation Server Proxy in the Account Partner](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md) 和 [Review the Role of the Federation Server Proxy in the Resource Partner](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Resource-Partner.md)。  
  
## <a name="how-to-create-a-federation-server-proxy"></a>如何创建联合服务器代理  
您可以使用 AD FS 联合服务器代理配置向导或 Fsconfig.exe 命令\-行工具来创建联合服务器代理。 有关如何执行此操作的说明，请参阅 [Configure a Computer for the Federation Server Proxy Role](../../ad-fs/deployment/Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md)。  
  
有关如何设置部署联合服务器代理所需的所有必备软件的常规信息，请参阅 [Checklist: Setting Up a Federation Server Proxy](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server-Proxy.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
