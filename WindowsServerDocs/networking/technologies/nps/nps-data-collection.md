---
title: 网络策略服务器用户数据收集
description: Windows Server 2016 中的网络策略服务器使用哪些信息来帮助对用户进行身份验证。
author: MicrosoftGuyJFlo
manager: mtillman
ms.author: joflore
ms.reviewer: richagi
ms.custom: it-pro
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.date: 05/01/2018
ms.openlocfilehash: def65c174ff608301f8d4f35ef1ce19818103e61
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859370"
---
# <a name="network-policy-server-user-data-collection"></a>网络策略服务器用户数据收集

本文档说明如何查找网络策略服务器（NPS）在你要删除它的情况下收集的用户信息。

>[!Note]
>如果你有兴趣查看或删除个人数据，请查看 GDPR 站点的[Windows 数据主体请求](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-windows)中的 Microsoft 指导。 如果正在查找有关 GDPR 的常规信息，请参阅[服务信任门户的 GDPR 部分](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)。

## <a name="information-collected-by-nps"></a>NPS 收集的信息

- Timestamp
- 事件时间戳
- Username
- 完全限定的用户名
- 客户端 IP 地址
- 客户端供应商
- 客户端友好名称
- 身份验证类型
- 涉及 RADIUS 协议的许多其他字段

## <a name="gather-data-from-nps"></a>从 NPS 收集数据

如果启用并配置了记帐数据，则可以从 SQL Server 或日志文件中获取用户的 NPS 身份验证尝试记录，具体取决于配置。 

如果为 SQL Server 配置了记帐数据，则查询 User_Name = `'<username>'`的所有记录。

如果为日志文件配置了记帐数据，则在日志文件中搜索 `<username>` 查找所有日志条目。

网络策略和访问服务事件日志条目被视为重复到记帐数据，无需收集。

如果未启用记帐数据，则可以通过搜索 `<username>`从网络策略和访问服务事件日志中获取用户的 NPS 身份验证尝试记录。
