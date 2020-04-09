---
ms.assetid: d0ba3c0d-869f-4e24-89d7-499da7576f22
title: 查看联合服务器在帐户伙伴中的角色
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 2d51f0091746d2d5e816108e3b92d0cb1a8267cd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858530"
---
# <a name="review-the-role-of-the-federation-server-in-the-account-partner"></a>查看联合服务器在帐户伙伴中的角色

Active Directory 联合身份验证服务中的联合服务器 \(AD FS\) 充当安全令牌颁发者。 联合服务器基于驻留在本地属性存储中的帐户值生成声明并将它们打包为安全令牌，以便用户可以使用在资源伙伴组织中托管 \(SSO\)\) 上的单一符号\-来无缝地访问 Web\-browser\-应用 \(程序。  
  
> [!NOTE]  
> 当你的用户使用 Web 浏览器访问联合应用程序时，联合服务器会自动向用户颁发 cookie，以维护该 Web\-browser\-的应用程序的登录状态。 这些 cookie 包括用于用户的声明。 Cookie 可实现 SSO 功能，使用户不必在每次访问资源伙伴中不同的基于 Web\-浏览器\-应用程序时输入凭据。  
  
在 Web SSO 设计中，具有外围网络并且希望 Internet 用户可以访问应用程序的组织必须在外围网络中安装联合服务器代理。 在联合 Web SSO 设计中，至少必须在帐户伙伴组织的企业网络中安装至少一台联合服务器，并在资源伙伴组织的企业网络中安装至少一台联合服务器。  
  
> [!NOTE]  
> 在帐户伙伴组织中设置联合服务器计算机之前，必须先将计算机加入到 Active Directory 林中的任何域中，联合服务器将用来对该林的用户进行身份验证。 有关详细信息，请参阅 [Checklist: Setting Up a Federation Server](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
