---
ms.assetid: 1b21b0a9-1fe6-4fd1-8a25-92e578d774ed
title: 部署联合服务器代理
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 418fd3bc1c53a4f8f3bdb4b945df29b70806272a
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965959"
---
# <a name="deploying-federation-server-proxies"></a>部署联合服务器代理

若要在 Active Directory 联合身份验证服务 AD FS 中部署联合服务器代理 \( \) ，请完成清单中的每个任务[：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)。  
  
> [!NOTE]  
> 使用此清单时，建议您先阅读[Windows server 2012 的 "AD FS 设计指南](../design/ad-fs-design-guide-in-windows-server-2012.md)" 中的联合服务器代理规划指南的参考，然后再开始配置服务器的步骤。 按照清单，可以更好地了解联合服务器代理的设计和部署过程。  
  
## <a name="about-federation-server-proxies"></a>关于联合服务器代理  
联合服务器代理是运行 Windows Server &reg; 2012 和 AD FS 软件的计算机，这些软件已手动配置为充当代理角色。 你可以在组织中使用联合服务器来提供企业网络上防火墙后的 Internet 客户端和联合服务器之间的中介服务。  
  
> [!NOTE]  
> 尽管不能在同一台计算机上安装联合服务器和联合服务器代理角色，但联合服务器可以执行联合服务器代理功能。 有关详细信息，请参阅 [When to Create a Federation Server](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807101(v=ws.11))。  
  
在 Windows Server 2012 计算机上安装 AD FS 软件并将 &reg; 其配置为在代理角色中服务的操作使该计算机成为联合服务器代理。  
  
