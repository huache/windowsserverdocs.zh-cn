---
title: pathping
description: Pathping 命令的参考主题，可在源和目标之间的中间跃点获取网络延迟和网络丢失的相关信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ec430125-b1dc-4aad-a7c9-b70f486d9e3c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 6f3f90be7be29f1c50e70fa8ec49685ee1843c45
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85472553"
---
# <a name="pathping"></a>pathping

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

提供有关源和目标之间的中间跃点网络延迟和网络丢失情况的信息。 此命令会将多个回显请求消息发送到源和目标之间的每个路由器，在一段时间内，然后根据从每个路由器返回的数据包来计算结果。 由于此命令显示了任何给定路由器或链接的数据包丢失程度，因此可以确定哪些路由器或子网可能出现网络问题。 使用没有参数的情况下，此命令显示帮助。

> [!NOTE]
> 仅当 Internet 协议（TCP/IP）协议安装为网络连接中的网络适配器属性中的组件时，此命令才可用。
>
> 此外，此命令将标识路径上的哪些路由器，与使用[tracert 命令](tracert.md)时相同。 Howevever，此命令还会在指定的时间段内定期将 ping 发送到所有路由器，并基于从每个返回的数字计算统计信息。

## <a name="syntax"></a>语法

```
pathping [/n] [/h <maximumhops>] [/g <hostlist>] [/p <Period>] [/q <numqueries> [/w <timeout>] [/i <IPaddress>] [/4 <IPv4>] [/6 <IPv6>][<targetname>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /n | 防止**pathping**尝试将中间路由器的 IP 地址解析为其名称。 这可能会加快**pathping**结果的显示。 |
| /h`<maximumhops>` | 指定路径中要搜索目标的最大跃点数（目标）。 默认值为30个跃点。 |
| /g`<hostlist>` | 指定回显请求消息使用 IP 标头中的 "**松散源路由**" 选项，其中包含*hostlist*中指定的中间目标集。 使用松散源路由时，可通过一个或多个路由器分隔连续的中间目标。 主机列表中的最大地址或名称数为**9**。 *Hostlist*是一系列由空格分隔的 IP 地址（采用点分十进制表示法）。 |
| /p`<period>` | 指定在连续 ping 之间等待的毫秒数。 默认值为250毫秒（1/4 秒）。 此参数将单个 ping 发送到每个中间跃点。 因此，发送到同一跃点的两个 ping 之间的时间间隔与跃点的*数量相乘。* |
| /q`<numqueries>` | 指定发送到路径中的每个路由器的回显请求消息数。 默认值为100个查询。 |
| /w`<timeout>` | 指定等待每个答复的毫秒数。 默认值为3000毫秒（3秒）。 此参数并行发送多个 ping。 因此，在*超时*参数中指定的时间量不会限制在*period*参数中指定的时间，以便在 ping 之间等待。 |
| /i`<IPaddress>` | 指定源地址。 |
| /4`<IPv4>` | 指定 pathping 仅使用 IPv4。 |
| /6`<IPv6>` | 指定 pathping 仅使用 IPv6。 |
| `<targetname>` | 指定目标，该目标通过 IP 地址或主机名进行标识。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 所有参数都区分大小写。

- 为了避免网络拥塞，并最大程度地减少突发丢失的影响，应以足够慢的速度发送 ping。

### <a name="example-of-the-pathping-command-output"></a>Pathping 命令输出示例

```
D:\>pathping /n contoso1
Tracing route to contoso1 [10.54.1.196]
over a maximum of 30 hops:
  0  172.16.87.35
  1  172.16.87.218
  2  192.168.52.1
  3  192.168.80.1
  4  10.54.247.14
  5  10.54.1.196
computing statistics for 125 seconds...
            Source to Here   This Node/Link
Hop  RTT    Lost/Sent = Pct  Lost/Sent = Pct  address
  0                                           172.16.87.35
                                0/ 100 =  0%   |
  1   41ms     0/ 100 =  0%     0/ 100 =  0%  172.16.87.218
                               13/ 100 = 13%   |
  2   22ms    16/ 100 = 16%     3/ 100 =  3%  192.168.52.1
                                0/ 100 =  0%   |
  3   24ms    13/ 100 = 13%     0/ 100 =  0%  192.168.80.1
                                0/ 100 =  0%   |
  4   21ms    14/ 100 = 14%     1/ 100 =  1%  10.54.247.14
                                0/ 100 =  0%   |
  5   24ms    13/ 100 = 13%     0/ 100 =  0%  10.54.1.196
Trace complete.
```

当**pathping**运行时，第一个结果列出该路径。 接下来，会显示大约90秒（时间依跃点计数而变化）的繁忙消息。 在此期间，将从前面列出的所有路由器和它们之间的链接中收集信息。 在此期间结束时，将显示测试结果。

在上面的示例报表中，"**此节点/链接**、**丢失/已发送 = Pct** " 和 "**地址**" 列显示*172.16.87.218*和*192.168.52.1*之间的链接正在删除13% 的数据包。 跃点2和4的路由器也会丢弃发送到它们的数据包，但这种损失不会影响其转发未处理流量的能力。

对于在 "地址" 列中标识为竖线（）的链接，显示的丢失率 **|** 表示导致在路径上转发的数据包丢失的链接拥塞。 **address** 为路由器显示的丢失率（由其 IP 地址标识）表明这些路由器可能超载。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [tracert 命令](tracert.md)
