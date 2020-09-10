---
title: ping
description: 用于验证网络连接的 ping 命令的参考文章。
ms.topic: reference
ms.assetid: 49272671-2eec-4fa5-881f-65c24cfbef52
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 903bf25f228adaf3634ffc2cd8da988acd9be8af
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633667"
---
# <a name="ping"></a>ping

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过向另一台 TCP/IP 计算机发送 Internet 控制消息协议 (ICMP) 回响请求消息来验证 IP 级连接。 将显示相应的回响回复消息以及往返时间。 ping 是用于排查连接性、可访问性和名称解析的主要 TCP/IP 命令。 使用没有参数的情况下，此命令显示帮助内容。

你还可以使用此命令测试计算机的计算机名和 IP 地址。 如果成功完成了 IP 地址的 ping 操作，但不对计算机名称进行 ping 操作，则可能存在名称解析问题。 在这种情况下，请确保你指定的计算机名可以通过本地主机文件进行解析，方法是使用域名系统 (DNS) 查询，或通过 NetBIOS 名称解析技术。

> [!NOTE]
> 仅当在 "网络连接" 中网络适配器的属性中将 "Internet 协议" (TCP/IP) 协议安装为组件时，此命令才可用。

## <a name="syntax"></a>语法

```
ping [/t] [/a] [/n <count>] [/l <size>] [/f] [/I <TTL>] [/v <TOS>] [/r <count>] [/s <count>] [{/j <hostlist> | /k <hostlist>}] [/w <timeout>] [/R] [/S <Srcaddr>] [/4] [/6] <targetname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /t  | 指定 ping 继续向目标发送回显请求消息，直到中断。 若要中断和显示统计信息，请按 CTRL + ENTER。 若要中断并退出此命令，请按 CTRL + C。 |
| /a | 指定对目标 IP 地址执行反向名称解析。 如果此操作成功，则 ping 将显示相应的主机名。 |
| /n `<count>` | 指定发送的回送请求消息数。 默认值为 4。 |
| /l `<size>` | 指定发送的回响请求消息中的 **数据** 字段的长度（以字节为单位）。 默认值为 32。 最大大小为65527。 |
| /f | 指定发送回显请求消息时，如果 IP 标头中的 " **不分段** " 标志设置为1，则在 IPv4 上仅) 可用 (。 目标的路径中的路由器无法对 echo 请求消息进行分段。 此参数可用于排查路径最大传输单元 (PMTU) 问题。 |
| /I `<TTL>` | 指定发送的回响请求消息的 IP 标头中的 TTL 字段的值。 默认值为主机的默认 TTL 值。 最大 *TTL* 为255。 |
| /v `<TOS>` | 为)  (发送的回响请求消息的 IP 标头中的服务 (TOS) 字段指定类型的值。 默认值为 0。 *TOS* 指定为介于0到255之间的十进制值。 |
| /r `<count>` | 指定 IP 标头中的 **记录路由** 选项用于记录回显请求消息所采用的路径，以及相应的回显回复消息 (仅在 IPv4 上提供) 。 路径中的每个跃点都使用 **记录路由** 选项中的条目。 如果可能，请指定等于或大于源和目标之间的跃点数的 *计数* 。 *计数*的最小值必须为1，最大值为9。 |
| /s `<count>` | 指定 IP 标头中的 **Internet 时间戳** 选项用于记录每个跃点的回显请求消息到达的时间和相应的回显答复消息。 *计数*的最小值必须为1，最大值为4。 这对于链接本地目标地址是必需的。 |
| /j `<hostlist>` | 指定回显请求消息使用 IP 标头中的 " **松散源路由** " 选项，其中包含 *hostlist* 中指定的中间目标集， (仅在 IPv4 上提供) 。 使用松散源路由时，可通过一个或多个路由器分隔连续的中间目标。 主机列表中的最大地址或名称数为9。 主机列表是一系列以点分隔的十进制表示法 (的 IP 地址，) 用空格分隔。 |
| 遇到 `<hostlist>` | 指定回显请求消息使用 IP 标头中的 " **严格源路由** " 选项，其中包含 *hostlist* 中指定的中间目标集， (仅在 IPv4 上提供) 。 使用严格源路由时，下一个中间目标必须是直接可访问的 (它必须是路由器的接口) 上的邻居。 主机列表中的最大地址或名称数为9。 主机列表是一系列以点分隔的十进制表示法 (的 IP 地址，) 用空格分隔。 |
| /w `<timeout>` | 指定等待回送答复消息的时间量（以毫秒为单位），该消息对应于要接收的给定回响请求消息。 如果在超时时间内未收到回显回复消息，则会显示 "请求超时" 错误消息。 默认超时为 4000 (4 秒) 。 |
| /R | 指定仅) 在 IPv6 上跟踪往返路径 (。 |
| /S `<Srcaddr>` | 指定要使用的源地址 (仅) 上可用的 IPv6。 |
| /4 | 指定使用 IPv4 进行 ping 操作。 使用 IPv4 地址标识目标主机时不需要此参数。 只需按名称标识目标主机即可。 |
| /6 | 指定使用 IPv6 来进行 ping 操作。 使用 IPv6 地址标识目标主机时不需要此参数。 只需按名称标识目标主机即可。 |
| `<targetname>` | 指定目标的主机名或 IP 地址。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="example-of-the-ping-command-output"></a>Ping 命令输出示例

```
C:\>ping example.microsoft.com
    pinging example.microsoft.com [192.168.239.132] with 32 bytes of data:
    Reply from 192.168.239.132: bytes=32 time=101ms TTL=124
    Reply from 192.168.239.132: bytes=32 time=100ms TTL=124
    Reply from 192.168.239.132: bytes=32 time=120ms TTL=124
    Reply from 192.168.239.132: bytes=32 time=120ms TTL=124
```

### <a name="examples"></a>示例

若要 ping 目标10.0.99.221 并解析10.0.99.221 的主机名，请键入：

```
ping /a 10.0.99.221
```

若要使用10个回响请求消息 ping 目标10.0.99.221，其中每个请求消息的数据字段为1000字节，请键入：

```
ping /n 10 /l 1000 10.0.99.221
```

若要 ping 目标10.0.99.221 并记录4个跃点的路由，请键入：

```
ping /r 4 10.0.99.221
```

若要 ping 目标10.0.99.221 并指定 10.12.0.1-10.29.3.1-10.1.44.1 的稀疏源路由，请键入：

```
ping /j 10.12.0.1 10.29.3.1 10.1.44.1 10.0.99.221
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
