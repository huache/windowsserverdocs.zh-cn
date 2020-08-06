---
ms.assetid: 222e9f93-7c41-4527-8a98-8f7fbc7a58af
title: 在 Windows Server 2012 R2 的 AD FS 中部署联合服务器代理
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: eaf33a1f5398adc1237eaed5c8b418ccbebed9fe
ms.sourcegitcommit: de8fea497201d8f3d995e733dfec1d13a16cb8fa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87864165"
---
# <a name="deploying-federation-server-proxies"></a>部署联合服务器代理

在 \( \) Windows Server 2012 R2 的 Active Directory 联合身份验证服务 AD FS 中，联合服务器代理的角色由称为 Web 应用程序代理的新远程访问角色服务处理。 若要使你的 AD FS 可以从企业网络外部进行访问（这是在旧版 AD FS 中部署联合服务器代理的目的，如 AD FS 2.0 和 Windows Server 2012 中的 AD FS），可以在 Windows Server 2012 R2 中为 AD FS 部署一个或多个 web 应用程序代理。  
  
在 AD FS 的上下文中，Web 应用程序代理充当 AD FS 联合服务器代理。 除此之外，Web 应用程序代理为企业网络内部的 Web 应用程序提供反向代理功能，使任意设备上的用户都能够从企业网络外部访问这些 Web 应用程序。 有关 Web 应用程序代理角色服务的详细信息，请参阅“Web 应用程序代理概述”。  
  
若要规划 Web 应用程序代理的部署，可以查看以下主题中的信息：  
  
-   [规划 Web 应用程序代理基础结构 (WAP) ](/previous-versions/orphan-topics/ws.11/dn383648(v=ws.11))  
  
-   [规划 Web 应用程序代理服务器](/previous-versions/orphan-topics/ws.11/dn383647(v=ws.11))  
  
若要部署 Web 应用程序代理，可以遵循以下主题中的过程：  
  
-   [配置 Web 应用程序代理基础结构](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383644(v=ws.11))  
  
-   [安装和配置 Web 应用程序代理服务器](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383662(v=ws.11))  
  
 
## <a name="see-also"></a>另请参阅 

[AD FS 部署](../../ad-fs/AD-FS-Deployment.md)  

[Windows Server 2012 R2 AD FS 部署指南](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[部署联合服务器场](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  
