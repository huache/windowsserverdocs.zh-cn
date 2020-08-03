---
ms.assetid: 30657638-5709-48c5-87aa-98f688e07b4c
title: 清单-实现 Web SSO 设计
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 8d6accc36c7fbd1910d921c1673046960373075c
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520026"
---
# <a name="checklist-implementing-a-web-sso-design"></a>清单：实现 Web SSO 设计

此父清单包括 \- 指向有关 Active Directory 联合身份验证服务 AD FS 的 Web 单一 \- 登录 \- \( SSO \) 设计的 \( 重要概念的交叉引用链接 \) 。 它还包含指向从属清单的链接，该清单将帮助你完成实现此设计所需的任务。

> [!NOTE]
> 请按顺序完成本清单中的任务。 当引用链接将你带到概念主题或从属清单时，在查看概念主题或完成从属清单中的任务后，请返回到本主题，这样你就可以继续完成此清单中的剩余任务。

![web sso](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**清单：实现 WEB Sso 设计**

|任务|参考|
|--------|-------------|
|查看有关 Web SSO 设计的重要概念，并确定可以用于自定义此设计以满足组织需求的 AD FS 部署目标。 **注意：**|![web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[WEB Sso 设计](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807033(v=ws.11))<p>![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[标识你的 AD FS 部署目标的](../design/identifying-your-ad-fs-deployment-goals.md)web sso|
|查看硬件、 软件、 证书、 域名系统 \(DNS\), ，属性存储和您的组织中部署 AD FS 的客户端要求。|![web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[附录 A：查看 AD FS 要求](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678034(v=ws.11))|
|根据你的设计规划，请在企业网络或外围网络中安装一个或多个联合服务器。 **注意：** Web SSO 设计只需一个联合服务器就能成功运行。 单个联合服务器在声明提供方角色和信赖方角色中起作用。|![web sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)|
|\(可选 \) 确定你的组织是否需要外围网络中的联合服务器代理。|![web sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)|
|根据你的 Web SSO 设计规划和要使用它的方式，请将相应的属性存储、信赖方信任、声明和声明规则添加到联合身份验证服务。|![web sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[清单：配置帐户伙伴组织](Checklist--Configuring-the-Account-Partner-Organization.md)|
|如果你是资源伙伴组织中的管理员，则 \- 使用 WIF 和 WIF SDK 声明启用 web 浏览器应用程序、web 服务应用程序或 Microsoft &reg; Office SharePoint &reg; Server 应用程序。 **注意：**|![web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=122266)<p>![web sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity FOUNDATION SDK](https://go.microsoft.com/fwlink/?LinkId=122266)|
