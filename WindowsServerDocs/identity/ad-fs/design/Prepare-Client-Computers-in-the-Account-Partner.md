---
ms.assetid: cea6011d-3753-4b95-aaa5-38d4e97d6e42
title: 在帐户伙伴中准备客户端计算机
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 014524c78312c6fcd478b40ec47e212a194b0531
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858590"
---
# <a name="prepare-client-computers-in-the-account-partner"></a>在帐户伙伴中准备客户端计算机

帐户伙伴组织中的管理员为访问 Active Directory 联合身份验证服务 \(AD FS\) 联合应用程序准备客户端计算机的最简单方法是使用组策略。 组策略为你提供一种便捷的方法，可让你将联合所需的特定证书和设置推送到将用于访问联合应用程序的所有客户端计算机。  
  
为了使客户端计算机无需证书提示或受信任的站点相关提示即可无缝访问联合应用程序，我们建议你先准备好每台客户端计算机，然后在组织中广泛部署 AD FS。 请考虑使用组策略来自动：  
  
-   将每台客户端计算机上的 Internet Explorer 配置为信任帐户联合服务器。  
  
    有关详细信息，请参阅 [Configure Client Computers to Trust the Account Federation Server](../../ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md)。  
  
-   在每台客户端计算机上安装相应的帐户联合服务器、资源联合服务器和 Web 服务器安全套接字层 \(SSL\) 证书 \(或等效证书，这些证书链接到受信任的根\)。  
  
    有关详细信息，请参阅[使用组策略将证书分发到客户端计算机](../../ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md)。  
  

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
