---
title: 配置连接请求策略
description: 本主题提供有关如何在 Windows Server 2016 中的网络策略服务器中配置连接请求策略的信息。
manager: brianlic
ms.topic: article
ms.assetid: f62c6a67-4dda-47f8-8bdf-9b76c37953e6
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 422ef3238aac950b7d2808d8576b186aeb430767
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969414"
---
# <a name="configure-connection-request-policies"></a>配置连接请求策略

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题来创建和配置连接请求策略，以指定本地 NPS 是否处理连接请求或将其转发到远程 RADIUS 服务器进行处理。

连接请求策略是一组条件和设置，这些设置允许网络管理员指定远程身份验证拨入用户服务 (RADIUS) 服务器对运行网络策略服务器 NPS 的服务器 \( \) 从 RADIUS 客户端接收的连接请求进行身份验证和授权。

默认连接请求策略使用 NPS 作为 RADIUS 服务器并在本地处理全部身份验证请求。

若要将运行 NPS 的服务器配置为 RADIUS 代理并将连接请求转发到其他 NPS 或者 RADIUS 服务器，除了添加新的连接请求策略以指定连接请求必须匹配的条件和设置之外，还必须配置一个远程 RADIUS 服务器组。

可以在使用新连接请求策略向导创建新的连接请求策略时新建一个远程 RADIUS 服务器组。

如果你不希望 NPS 作为 RADIUS 服务器，并在本地处理连接请求，则可以删除默认连接请求策略。

如果希望 NPS 同时作为 RADIUS 服务器，并在本地处理连接请求，并将某些连接请求转发到远程 RADIUS 服务器组，请使用以下过程添加新的策略，然后验证默认连接请求策略是否是通过将最后一个策略放置在策略列表中。

## <a name="add-a-connection-request-policy"></a>添加连接请求策略

若要完成该过程，必须至少具有 **Domain Admins** 的成员资格或同等权限。

### <a name="to-add-a-new-connection-request-policy"></a>添加新的连接请求策略

1. 在服务器管理器中，单击 "**工具**"，然后单击 "**网络策略服务器**" 以打开 NPS 控制台。
2. 在控制台树中，双击 "**策略**"。
3. 右键单击 "**连接请求策略**"，然后单击 "**新建连接请求策略**"。
4. 使用新建连接请求策略向导配置连接请求策略，如果以前未配置，还需配置远程 RADIUS 服务器组。


有关管理 NPS 的详细信息，请参阅[管理网络策略服务器](nps-manage-top.md)。

有关 NPS 的详细信息，请参阅[网络策略服务器 (nps) ](nps-top.md)。

