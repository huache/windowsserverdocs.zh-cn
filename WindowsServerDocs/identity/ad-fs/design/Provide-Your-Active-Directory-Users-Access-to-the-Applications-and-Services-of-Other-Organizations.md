---
ms.assetid: 2d62386c-b466-4a54-b6fa-5d16cda120d8
title: 为其他组织的应用程序和服务提供 Active Directory 用户访问权限
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: bcf9b9ec91c1757ad060747a6aa1589012c1ec14
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359032"
---
# <a name="provide-your-active-directory-users-access-to-the-applications-and-services-of-other-organizations"></a>为其他组织的应用程序和服务提供 Active Directory 用户访问权限

此 Active Directory 联合身份验证服务 \(AD FS\) 部署目标的构建目的在于向[用户 Active Directory 提供对声明感知应用程序和服务的访问权限](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)。  
  
当你是帐户伙伴组织中的管理员，并且你的部署目标是为员工提供对另一组织中的托管资源的联合访问权限时：  
  
-   如果员工登录到企业网络中的 Active Directory 域，则可以使用\-\-\(SSO\) 功能来访问多个基于 Web\-的应用程序或服务，当应用程序或服务位于其他组织中时，这些应用程序或服务受 AD FS 保护。 有关详细信息，请参阅 [Federated Web SSO Design](Federated-Web-SSO-Design.md)。  
  
    例如，Fabrikam 可能希望企业网络员工具有对 Contoso 中托管的 Web 服务的联合访问权限。  
  
-   登录到 Active Directory 域的远程员工可以从组织中的联合服务器获取 AD FS 的令牌，以获取对在另一组织中托管的基于 AD FS 保护的基于 Web\-的应用程序或服务的联合访问权限。  
  
    例如，Fabrikam 可能希望其远程员工具有对 Contoso 中托管的 AD FS 保护的服务的联合访问权限，而无需 Fabrikam 员工在 Fabrikam 企业网络上。  
  
除了 [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md) 中所述的基本组件和以下插图中以阴影显示的组件之外，比部署目标还需要以下组件：  
  
-   **帐户伙伴联合服务器代理：** 从 Internet 访问联合服务或应用程序的员工可以使用此 AD FS 组件来执行身份验证。 默认情况下，此组件执行窗体身份验证，但它还可以执行基本身份验证。 如果组织中的员工具有要显示的证书，则还可以将此组件配置为执行安全套接字层 \(SSL\) 客户端身份验证。 有关详细信息，请参阅 [Where to Place a Federation Server Proxy](Where-to-Place-a-Federation-Server-Proxy.md)。  
  
-   **外围 DNS：** 此域名系统的实现 \(DNS\) 为外围网络提供主机名。 有关如何为联合服务器代理配置外围 DNS 的详细信息，请参阅[联合服务器代理的名称解析要求](Name-Resolution-Requirements-for-Federation-Server-Proxies.md)。  
  
-   **远程员工：** 远程员工通过受支持的 Web 浏览器访问基于 Web\-的应用程序 \(\)\-或通过 \(应用程序\)使用企业网络中的有效凭据，而使用企业网络中的有效凭据访问基于 web 的应用程序。 员工在远程位置的客户端计算机与联合服务器代理直接通信，以生成令牌并对应用程序或服务进行身份验证。  
  
在查看链接的主题中的信息后，可以按照 [Checklist: Implementing a Federated Web SSO Design](../../ad-fs/deployment/Checklist--Implementing-a-Federated-Web-SSO-Design.md)中的步骤开始部署此目标。  
  
下图显示了此 AD FS 部署目标所需的每个组件。  
  
![访问应用](media/50af4837-31e0-451f-a942-e705c2300065.gif)  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
