---
ms.assetid: 04b63d9f-e924-4146-9b1d-785ed8b4239c
title: 规划与 AD FS 1.x 的互操作性
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: a0bbf64a7bf110e3d73084dd047c84b2b83be8d9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858610"
---
# <a name="planning-for-interoperability-with-ad-fs-1x"></a>规划与 AD FS 1.x 的互操作性

Active Directory 联合身份验证服务 \(AD FS\) 运行 Windows Server&reg; 2012 的联合服务器可以1.0 与随 Windows Server 2003 R2 AD FS \(\) 联合身份验证服务 AD FS \(\) 联合身份验证服务和 windows server 2008 或 Windows Server 2008 R2 安装的1.1 互操作。 支持以下任何互操作性组合：  

-   任何 AD FS 1。*x*联合身份验证服务可以发送可由 Windows Server 2012 中的 AD FS 联合身份验证服务使用的声明。 有关详细信息，请参阅[清单：将 AD FS 配置为使用 AD FS 1.x 中的声明](../../ad-fs/deployment/Checklist--Configuring-AD-FS--to-Consume-Claims-from-AD-FS-1.x.md)。  

-   Windows Server 2012 中的任何 AD FS 联合身份验证服务都可以发送 AD FS 1。*x*\-可供 AD FS 1 使用的兼容声明。*x*联合身份验证服务。 有关详细信息，请参阅 [Checklist: Configuring AD FS to Send Claims to an AD FS 1.x Federation Service](../../ad-fs/deployment/Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Federation-Service.md)。  

-   Windows Server 2012 中的任何 AD FS 联合身份验证服务都可以发送 AD FS 1。*x*\-兼容的声明，可供运行 AD FS 1 的一台或多台 Web 服务器使用。*x*声明\-感知 Web 代理。 有关详细信息，请参阅 [Checklist: Configuring AD FS to Send Claims to an AD FS 1.x Claims-Aware Web Agent](../../ad-fs/deployment/Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Claims-Aware-Web-Agent.md)。  

> [!NOTE]  
> AD FS 不支持 AD FS 1 或与之进行互操作。基于*x* Windows NT 令牌的 Web 代理。  

AD FS 1。*x*\-兼容声明是可以由 Windows Server 2012 中的 AD FS 联合身份验证服务发送并由 AD FS 1 理解的声明。*x*联合身份验证服务。 AD FS 1。*x*联合身份验证服务可以使用 AD FS 联合身份验证服务发送的声明，必须发送名称标识符 \(ID\) 声明类型。  

## <a name="understanding-the-name-id-claim-type"></a>了解名称 ID 声明类型  
名称 ID 声明类型等效于 AD FS 1.*x* 使用的标识声明类型。 每当要与 AD FS 1.*x*进行互操作时，都必须使用该类型。 名称 ID 声明类型启用 AD FS 1。*x*联合身份验证服务或 AD FS 1。*x*声明\-知道使用 Windows Server 2012 发送 AD FS 的声明，只要这些声明是使用下表中的名称 ID 格式之一发送的。  


|      名称 ID 格式       |               对应 URI                |
|---------------------------|------------------------------------------------|
| AD FS 1.*x* 电子邮件地址 | http://schemas.xmlsoap.org/claims/EmailAddress |
|   AD FS 1.*x* 电子邮件 UPN   |     http://schemas.xmlsoap.org/claims/UPN      |
|        公用名        |  http://schemas.xmlsoap.org/claims/CommonName  |
|           组           |    http://schemas.xmlsoap.org/claims/Group     |

必须仅发送一个采用合适格式的名称 ID 声明。 满足该条件时，还可能会发送许多其他声明（假设它们符合表中描述的限制）。  

> [!NOTE]  
> AD FS 1。*x*联合身份验证服务只能解释以统一资源标识符（\(URI\) 的 http://schemas.xmlsoap.org/claims/）开头的传入声明类型。  

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
