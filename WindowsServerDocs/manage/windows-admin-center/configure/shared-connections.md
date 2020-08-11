---
title: 为 Windows Admin Center 网关的所有用户配置共享连接
description: 了解管理员如何将 Windows Admin Center (Project Honolulu) 网关配置一次即可允许所有用户共享一组连接。
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 03/28/2019
ms.localizationpriority: medium
ms.openlocfilehash: eea0e467629a6110d38ed3081a1320e002496cfb
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87970874"
---
# <a name="configure-shared-connections-for-all-users-of-the-windows-admin-center-gateway"></a>为 Windows Admin Center 网关的所有用户配置共享连接

> 适用于：Windows Admin Center 预览版、Windows Admin Center

在有了配置共享连接的功能后，网关管理员可以一次为给定 Windows Admin Center 网关的所有用户都配置连接列表。 此功能仅在 Windows Admin Center 服务模式下可用。

在 Windows Admin Center 网关设置的“共享连接”  选项卡上，网关管理员可以像在“所有连接”页中那样添加服务器、群集和 PC 连接，包括对连接进行标记。 在“共享连接”列表中添加的任何连接和标记将显示给此 Windows Admin Center 网关的所有用户（在其“所有连接”页中）。

![Windows Admin Center -“共享连接”页](../media/shared-cnxns-1.png)

在配置“共享连接”后，任何 Windows Admin Center 用户访问“所有连接”页面时都将看到自己的连接已分组到两个部分：“个人”和“共享连接”。 “个人”组是特定用户的连接列表，持久保存于该用户的浏览器会话中。 “共享连接”组对所有用户都是相同的，并且不能从“所有连接”页进行修改。

![Windows Admin Center -“所有连接”页](../media/shared-cnxns-2.png)