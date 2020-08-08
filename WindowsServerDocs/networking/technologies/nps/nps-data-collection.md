---
title: 网络策略服务器用户数据收集
description: Windows Server 2016 中的网络策略服务器使用哪些信息来帮助对用户进行身份验证。
author: MicrosoftGuyJFlo
manager: mtillman
ms.author: joflore
ms.reviewer: richagi
ms.custom: it-pro
ms.topic: article
ms.date: 05/01/2018
ms.openlocfilehash: a47cb5791b6e157b434d80535d10b107159db48f
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87994601"
---
# <a name="network-policy-server-user-data-collection"></a>网络策略服务器用户数据收集

本文档介绍了如何查找网络策略服务器在你想要删除的网络策略服务器 (NPS) 收集的用户信息。

>[!Note]
>如果你有兴趣查看或删除个人数据，请查看 GDPR 站点的[Windows 数据主体请求](/microsoft-365/compliance/gdpr-dsr-windows)中的 Microsoft 指导。 如果正在查找有关 GDPR 的常规信息，请参阅[服务信任门户的 GDPR 部分](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)。

## <a name="information-collected-by-nps"></a>NPS 收集的信息

- Timestamp
- 事件时间戳
- 用户名
- 完全限定的用户名
- 客户端 IP 地址
- 客户端供应商
- 客户端友好名称
- 身份验证类型
- 涉及 RADIUS 协议的许多其他字段

## <a name="gather-data-from-nps"></a>从 NPS 收集数据

如果启用并配置了记帐数据，则可以从 SQL Server 或日志文件中获取用户的 NPS 身份验证尝试记录，具体取决于配置。

如果为 SQL Server 配置了记帐数据，则查询 User_Name = 的所有记录 `'<username>'` 。

如果为日志文件配置了记帐数据，则在日志文件中搜索 `<username>` 以查找所有日志条目。

网络策略和访问服务事件日志条目被视为重复到记帐数据，无需收集。

如果未启用记帐数据，则可以通过搜索来从网络策略和访问服务事件日志中获取用户的 NPS 身份验证尝试记录 `<username>` 。