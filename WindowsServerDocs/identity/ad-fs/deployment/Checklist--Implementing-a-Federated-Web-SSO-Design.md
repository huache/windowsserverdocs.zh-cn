---
ms.assetid: 6b49cde3-d2cb-4ece-b9b7-dc600e037495
title: 清单-实现联合 Web SSO 设计
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: b9d56dd2852d7efdabb0c9fbad221f8b6798ef52
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966349"
---
# <a name="checklist-implementing-a-federated-web-sso-design"></a>清单︰ 实施联合的 Web SSO 设计

此父清单包含交叉\-引用链接到有关联合 Web 单一的重要概念\-登录\-上 \(SSO\) Active Directory 联合身份验证服务的设计 \(AD FS\)。 它还包含指向从属清单的链接，该清单将帮助你完成实现此设计所需的任务。  
  
> [!NOTE]  
> 请按顺序完成本清单中的任务。 当引用链接将你带到概念主题或从属清单时，在查看概念主题或完成从属清单中的任务后，请返回到本主题，这样你就可以继续完成此清单中的剩余任务。  
  
![联合 web sso](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**清单：实现联合 WEB Sso 设计**  
  
||任务|参考|  
|-|--------|-------------|  
|![联合的 web sso](media/icon_checkboxo.gif)|查看有关联合 Web SSO 设计的重要概念并确定可用于自定义此设计以满足您的组织的需求的 AD FS 部署目标。|![联合 web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[联合 WEB Sso 设计](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807050(v=ws.11))<p>![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[用于标识你的 AD FS 部署目标的](../design/identifying-your-ad-fs-deployment-goals.md)联合 web sso<p>![联合 web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[规划你的部署](../design/planning-your-deployment.md)|  
|![联合的 web sso](media/icon_checkboxo.gif)|查看硬件、 软件、 证书、 域名系统 \(DNS\), ，属性存储和您的组织中部署 AD FS 的客户端要求。|![联合 web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[附录 A：查看 AD FS 要求](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678034(v=ws.11))|  
|![联合的 web sso](media/icon_checkboxo.gif)|查看有关声明的重要概念，在这两个伙伴组织中部署 AD FS 之前声明规则、 属性存储和 AD FS 配置数据库。|![联合 web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[了解密钥 AD FS 概念](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)|  
|![联合的 web sso](media/icon_checkboxo.gif)|根据您的设计规划，每个伙伴组织中安装一个或多个联合服务器。 **注意︰** 对于联合 Web SSO 设计中，您需要在帐户伙伴组织中的至少一台联合服务器和资源伙伴组织中的至少一台联合服务器。|![联合 web sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)|  
|![联合的 web sso](media/icon_checkboxo.gif)|\(可选 \) 确定你的组织是否需要联合服务器代理。 如果你的设计规划需要代理，您可以在每个伙伴组织中安装一个或多个联合服务器代理。|![联合 web sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)|  
|![联合的 web sso](media/icon_checkboxo.gif)|根据你的设计规划，请共享证书、配置客户端并在这两个伙伴组织中配置信任关系，以便他们可以通过联合信任进行通信。|![联合 web sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：配置帐户伙伴组织](Checklist--Configuring-the-Account-Partner-Organization.md)<p>![联合 web sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：配置资源伙伴组织](Checklist--Configuring-the-Resource-Partner-Organization.md)|  
|![联合的 web sso](media/icon_checkboxo.gif)|如果你是资源伙伴组织中的管理员，则 \- 使用 WIF 和 WIF SDK 声明启用 web 浏览器应用程序、web 服务应用程序或 Microsoft &reg; Office SharePoint &reg; Server 应用程序。|![联合 web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=122266)<p>![联合 web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity FOUNDATION SDK](https://go.microsoft.com/fwlink/?LinkId=122266)|  
