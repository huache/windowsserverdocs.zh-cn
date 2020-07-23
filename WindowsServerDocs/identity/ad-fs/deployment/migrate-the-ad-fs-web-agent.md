---
title: 迁移 AD FS web 代理
description: 提供有关 AD FS web 代理到 Windows Server 2012 的信息。
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3c18e0a6a2e633c0fad0ce8585296afba8ce444c
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966929"
---
# <a name="migrate-the-ad-fs-web-agent"></a>迁移 AD FS web 代理

若要将随 Windows Server 2008 R2 或 Windows Server 2008 一起安装的 AD FS 1.1 基于 Windows 令牌的代理或 AD FS 1.1 声明感知代理迁移到 Windows server 2012，请对承载任一代理的计算机的操作系统进行就地升级。 有关详细信息，请参阅[安装 Windows Server 2012](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj134246(v=ws.11))。 无需进一步配置。  
  
> [!IMPORTANT]
>  迁移的 AD FS 1.1 基于 Windows 令牌的代理只能与随 Windows Server 2008 R2 或 Windows Server 2008 一起安装的 AD FS 1.1 联合身份验证服务一起使用。 有关详细信息，请参阅 [Interoperating with AD FS 1.x](Interoperating-with-AD-FS-1.x.md)。  
> 
>  迁移的 AD FS 1.1 声明感知 Web 代理可与以下联合身份验证服务一起使用：  
> 
> - 随 Windows Server 2008 R2 或 Windows Server 2008 一起安装的 AD FS 1.1 联合身份验证服务  
>   -   在 Windows Server 2008 R2 或 Windows Server 2008 上安装的 AD FS 2.0 联合身份验证服务  
>   -   随 Windows Server 2012 一起安装 AD FS 联合身份验证服务  
> 
>   有关详细信息，请参阅 [Interoperating with AD FS 1.x](Interoperating-with-AD-FS-1.x.md)。  
  
  
## <a name="next-steps"></a>后续步骤
 [准备迁移 AD FS 2.0 联合服务器](prepare-to-migrate-ad-fs-fed-server.md)   
 [准备迁移 AD FS 2.0 联合服务器代理](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [迁移 AD FS 2.0 联合服务器](migrate-the-ad-fs-fed-server.md)   
 [迁移 AD FS 2.0 联合服务器代理](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [迁移 AD FS 1.1 Web 代理](migrate-the-ad-fs-web-agent.md)
