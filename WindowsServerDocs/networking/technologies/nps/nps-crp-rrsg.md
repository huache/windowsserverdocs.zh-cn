---
title: 远程 RADIUS 服务器组
description: 本主题概述了 Windows Server 2016 中的网络策略服务器远程 RADIUS 服务器组。
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: d81678a7-be21-48f2-9b3f-5a75d6aef013
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 8275c3e8902ed78d77d01a2ff5d769d3e99abf97
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80316178"
---
# <a name="remote-radius-server-groups"></a>远程 RADIUS 服务器组

>适用于：Windows Server（半年频道）、Windows Server 2016

将网络策略服务器（NPS）配置为远程身份验证拨入用户服务（RADIUS）代理时，可以使用 NPS 将连接请求转发到能够处理连接请求的 RADIUS 服务器，因为它们可以执行用户或计算机帐户所在的域中的身份验证和授权。 例如，如果希望将连接请求转发到不受信任域中的一个或多个 RADIUS 服务器，可以将 NPS 配置为 RADIUS 代理，从而将请求转发到不受信任域中的远程 RADIUS 服务器。

>[!NOTE]
>远程 RADIUS 服务器组与 Windows 组无关并独立于它们。

若要将 NPS 配置为 RADIUS 代理，必须创建连接请求策略，它包含用于 NPS 评估转发哪些消息和将消息发送何处所需的全部信息。

在 NPS 中配置远程 RADIUS 服务器组，并使用该组配置连接请求策略时，需指定 NPS 转发连接请求的位置。

## <a name="configuring-radius-servers-for-a-group"></a>为组配置 RADIUS 服务器

远程 RADIUS 服务器组是包括一个或多个 RADIUS 服务器的指定组。 如果配置多个服务器，可以指定负载平衡设置，以确定代理使用服务器的顺序，或者跨组中的所有服务器分发 RADIUS 消息流，以防止具有太多连接请求的一个或多个服务器过载。

该组中的每个服务器都具有以下设置。

- **名称或地址**。 每个组成员都必须具有一个在组中唯一的名称。 名称可以是 IP 地址或可解析为其 IP 地址的名称。

- **身份验证和计帐**。 可以将身份验证请求和/或记帐请求转发到每个远程 RADIUS 服务器组成员。

- **负载均衡**。 优先级设置用于表明组中的哪个成员是主服务器（优先级设置为 1）。 对于具有相同优先级的组成员，使用权重设置来计算将 RADIUS 消息发送到每个服务器的频率。 你可以使用其他设置来配置 NPS 在组成员首次变为不可用时的检测方法，以及在确定其不可用后该成员变为可用的方式。

配置远程 RADIUS 服务器组之后，可以在连接请求策略的 "身份验证和记帐" 设置中指定组。 因此，可以首先配置远程 RADIUS 服务器组。 接下来，可以配置连接请求策略以使用新配置的远程 RADIUS 服务器组。 或者，也可以在创建连接请求策略时使用新建连接请求策略向导创建新的远程 RADIUS 服务器组。

有关 NPS 的详细信息，请参阅[网络策略服务器（NPS）](nps-top.md)。
