---
title: netstat
description: 用于显示活动 TCP 连接、计算机正在侦听的端口、以太网统计信息、IP 路由表、IPv4 统计信息和 IPv6 统计信息的 netstat 命令参考文章。
ms.topic: article
ms.assetid: 60e2718f-93cc-4ceb-bf0e-58a6a6e4fc8b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9fe7fc15e86df884fb9610ba5d6e72ab52e2d129
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87886013"
---
# <a name="netstat"></a>netstat

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示处于活动状态的 TCP 连接、计算机正在侦听的端口、以太网统计信息、IP 路由表、用于 IP、ICMP、TCP 和 UDP 协议的 IPv4 统计信息 () 和 ipv6 统计信息 (ipv6、ICMPv6、TCP over IPv6 和 UDP over IPv6 协议) 。 使用没有参数的情况下，此命令显示活动 TCP 连接。

> [!IMPORTANT]
> 仅当在 "网络连接" 中网络适配器的属性中将 "Internet 协议" (TCP/IP) 协议安装为组件时，此命令才可用。

## <a name="syntax"></a>语法

```
netstat [-a] [-b] [-e] [-n] [-o] [-p <Protocol>] [-r] [-s] [<interval>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| -a | 显示所有活动 TCP 连接以及计算机正在侦听的 TCP 和 UDP 端口。 |
| -b | 显示创建每个连接或侦听端口所涉及的可执行文件。 在某些情况下，众所周知的可执行文件托管多个独立组件，并且在这种情况下，将显示创建连接或侦听端口所涉及的组件序列。 在这种情况下，可执行文件名称位于底部的 []，顶部是它调用的组件，依此类推，直到达到 TCP/IP。 请注意，此选项可能非常耗时且将失败，除非你有足够的权限。
| -E | 显示以太网统计信息，如发送和接收的字节数和数据包数。 此参数可以与 **-s**组合。 |
| -n | 显示活动 TCP 连接，但地址和端口号用数字表示，而不会尝试确定名称。 |
| -o | 显示活动 TCP 连接，并包含每个连接 (PID) 的进程 ID。 您可以根据 Windows 任务管理器中 "进程" 选项卡上的 PID 查找该应用程序。 此参数可以与 **-a**、 **-n**和 **-p**结合使用。 |
| -p`<Protocol>` | 显示*协议*指定的协议的连接。 在这种情况下，该*协议*可以是 tcp、udp、tcpv6 或 udpv6。 如果将此参数与 **-s**一起使用以按协议显示统计信息，则*协议*可以是 tcp、udp、icmp、ip、tcpv6、udpv6、icmpv6 或 ipv6。 |
| -S | 按协议显示统计信息。 默认情况下，会显示 TCP、UDP、ICMP 和 IP 协议的统计信息。 如果安装了 IPv6 协议，则会显示 TCP over IPv6、基于 IPv6 的 UDP、ICMPv6 和 IPv6 协议的统计信息。 **-P**参数可用于指定一组协议。 |
| -r | 显示 IP 路由表的内容。 这等效于路由打印命令。 |
| `<interval>` | 每隔*间隔*秒重新计算选定的信息。 按 CTRL + C 停止重新显示。 如果省略此参数，则此命令仅打印选定的信息一次。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Netstat**命令提供以下各项的统计信息：

    | 参数 | 描述 |
    | --------- | ----------- |
    | Proto | 协议 (TCP 或 UDP) 的名称。 |
    | 本地地址 | 本地计算机的 IP 地址和所使用的端口号。 除非指定了 **-n**参数，否则显示与 IP 地址和端口名称对应的本地计算机的名称。 如果尚未建立端口，则端口号显示为星号 ( * ) 。 |
    | 外部地址 | 套接字连接到的远程计算机的 IP 地址和端口号。 除非指定了 **-n**参数，否则将显示与 IP 地址和端口对应的名称。 如果尚未建立端口，则端口号显示为星号 ( * ) 。 |
    | 州省/自治区/直辖市 | 指示 TCP 连接的状态，包括：<ul><li>CLOSE_WAIT</li><li>CLOSED</li><li>端建立</li><li>FIN_WAIT_1</li><li>FIN_WAIT_2</li><li>LAST_ACK</li><li>侦听</li><li>SYN_RECEIVED</li><li>SYN_SEND</li><li>TIMED_WAIT</li></ul> |

### <a name="examples"></a>示例

若要显示以太网统计信息和所有协议的统计信息，请键入：

```
netstat -e -s
```

若要仅显示 TCP 和 UDP 协议的统计信息，请键入：

```
netstat -s -p tcp udp
```

若要每隔5秒显示一次活动 TCP 连接和进程 Id，请键入：

```
netstat -o 5
```

若要使用数字形式显示活动 TCP 连接和进程 Id，请键入：

```
netstat -n -o
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
