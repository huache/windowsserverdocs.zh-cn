---
title: '动态主机配置协议的故障排除指南 (DHCP) '
description: 此 artilce 介绍了 DHCP 问题的疑难解答指南。
manager: dcscontentpm
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: 92a7984fe2070ac194aa01a5a9aa63e85b7aa45d
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078614"
---
# <a name="troubleshooting-guide-for-dynamic-host-configuration-protocol-dhcp"></a>动态主机配置协议的故障排除指南 (DHCP) 

对于任何设备 (例如计算机或电话) 能够在网络中操作，必须为其分配 IP 地址。 可以手动或自动分配 IP 地址。 自动分配由 DHCP 服务 (Microsoft 或第三方服务器) 进行处理。

本文将讨论 Microsoft IPv4 DHCP 客户端和服务器的常规故障排除步骤。

## <a name="more-information"></a>更多信息

IPv4 地址分配的过程通常涉及三个主要组件：

- 必须获得 IP 地址的 DHCP 客户端设备

- 基于特定设置向客户端提供 IP 地址的 DHCP 服务

- DHCP 中继代理/IP 帮助器将 DHCP 广播请求发送到不同网段

DHCP 客户端到服务器通信包括两个对等方之间的三种交互：

- **基于广播的 DORA** (发现、提供、请求、确认) 。 此过程包括以下步骤：

    - DHCP 客户端将 DHCP 发现广播请求发送到范围内的所有可用 DHCP 服务器。

    - 将从 DHCP 服务器接收 DHCP 优惠广播响应，提供可用的 IP 地址租约。

    - DHCP 客户端广播请求会要求提供 IP 地址租约和 DHCP 广播确认结束。

    - 如果 DHCP 客户端和服务器位于不同的逻辑网段中，则 DHCP 中继代理将充当转发器，并在对等方之间来回发送 DHCP 广播数据包。

- **单播 DHCP 续订请求**：这些请求从 dhcp 客户端直接发送到 dhcp 服务器，以便在 ip 地址租约时间50% 之后续订 ip 地址分配。

- 重新**绑定 dhcp 广播请求**：将这些请求发送到客户端范围内的任何 DHCP 服务器。 在 IP 地址租约持续时间的87.5% 后发送这些请求，因为这表明定向单播请求不起作用。 对于 DORA 进程，此过程涉及到 DHCP 中继代理通信。

如果 Microsoft DHCP 客户端未收到有效的 DHCP IPv4 地址，则可能会将客户端配置为使用 APIPA 地址。 有关详细信息，请参阅以下知识库文章： [220874](https://support.microsoft.com/help/220874) 如何使用没有 DHCP 服务器的自动 tcp/ip 寻址

所有通信都是在 UDP 端口67和68上完成的。 有关详细信息，请参阅以下知识库文章： [169289](https://support.microsoft.com/help/169289) DHCP (动态主机配置协议) 基础知识。