---
ms.assetid: 97999892-29c6-4076-be19-5e5259d8ada6
title: 与 AD FS 1.x 进行互操作
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 21f0ef0e3ad77d5ea58e5d3b82da66ce420e5d49
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972144"
---
# <a name="interoperating-with-ad-fs-1x"></a>与 AD FS 1.x 进行互操作

对于 \( \) Windows Server 2012 中的 Active Directory 联合身份验证服务 AD FS &reg; 与 AD FS 1*之间的互操作性。x*完成以下一项或多项任务，具体取决于你的组织的需求：

-   Windows Server 2012 中的 AD FS 和以前版本的 AD FS 之间的互操作性规划和了解更多有关名称 ID 声明类型。 有关详细信息，请参阅[规划与 AD FS 1.x 的互操作性](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff678040(v=ws.11))。

-   如果要从可由 AD FS 1 使用的 Windows Server 2012 中的 AD FS 联合身份验证服务发送声明。*x*联合身份验证服务，请参阅[清单：配置 AD FS 将声明发送到 AD FS 1.x 联合身份验证服务](Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Federation-Service.md)。

-   如果要从 Windows Server 2012 中的 AD FS 联合身份验证服务发送声明，则该应用程序可由运行 AD FS 1 的 Web 服务器所承载的应用程序使用。*x*声明 \- 感知 web 代理，请参阅[清单：配置 AD FS 将声明发送到 AD FS 1.X 声明感知 Web 代理](Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Claims-Aware-Web-Agent.md)。

-   如果将从 AD FS 1 发送声明。*x*联合身份验证服务要由 Windows Server 2012 中的 AD FS 联合身份验证服务使用，请参阅[清单：将 AD FS 配置为使用 AD FS 1.X 中的声明](Checklist--Configuring-AD-FS--to-Consume-Claims-from-AD-FS-1.x.md)。

## <a name="differences-between-federation-service-settings"></a>联合身份验证服务设置之间的差异
尽管大部分 AD FS 1。*x*联合身份验证服务设置的工作方式类似于 Windows Server 2012 设置中的 AD FS 联合身份验证服务，某些设置名称已更改。 下表列出了 AD FS 1 的设置名称。*x*联合身份验证服务和它们在 Windows Server 2012 中的 AD FS 联合身份验证服务的等效名称。

|AD FS 1.x 联合身份验证服务设置|Windows Server 2012 设置中的等效 AD FS 联合身份验证服务
|----------------------------------------|----------------------------------------------------------------------------------------------------------
|帐户伙伴|声明提供方信任
|资源伙伴|信赖方信任
|应用程序|信赖方信任
|Application Properties|信赖方信任属性
|应用程序 URL|信赖方标识符和 WS \- 联合身份验证被动终结点 URL
|联合身份验证服务 URI|联合身份验证服务标识符
|联合身份验证服务终结点 URL|WS \- 联合身份验证被动终结点 URL

## <a name="see-also"></a>另请参阅
[AD FS 和 AD FS 1.x 互操作性](https://go.microsoft.com/fwlink/?LinkId=200776)

