---
title: nbtstat
description: Nbtstat 命令的参考文章，其中显示了 TCP/IP 上的 NetBIOS (NetBT) 协议统计信息、本地计算机和远程计算机的 NetBIOS 名称表以及 NetBIOS 名称缓存。
ms.topic: article
ms.assetid: 1d2ea99e-72f1-471f-9525-d2c49bf3be82
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3367190fb751a0cb5081724c6ea8ad2b7f2c95ff
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87886116"
---
# <a name="nbtstat"></a>nbtstat

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示 TCP/IP 上的 NetBIOS (NetBT) 协议统计信息、本地计算机和远程计算机的 NetBIOS 名称表以及 NetBIOS 名称缓存。 此命令还允许刷新 NetBIOS 名称缓存和在 Windows Internet 名称服务中注册的名称， (入选) 。 使用不带参数的命令将显示帮助信息。

仅当在 "网络连接" 中网络适配器的属性中将 "Internet 协议" (TCP/IP) 协议安装为组件时，此命令才可用。

## <a name="syntax"></a>语法

```
nbtstat [/a <remotename>] [/A <IPaddress>] [/c] [/n] [/r] [/R] [/RR] [/s] [/S] [<interval>]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /a`<remotename>` | 显示远程计算机的 NetBIOS 名称表，其中*remotename*是远程计算机的 netbios 计算机名称。 NetBIOS 名称表是对应于计算机上运行的 NetBIOS 应用程序的 NetBIOS 名称的列表。 |
| /A`<IPaddress>` | 显示远程计算机的 NetBIOS 名称表，由 IP 地址指定， (以点分隔的十进制表示法) 远程计算机。 |
| /c | 显示 NetBIOS 名称缓存的内容、NetBIOS 名称表及其解析的 IP 地址。 |
| /n | 显示本地计算机的 NetBIOS 名称表。 "**已注册**" 状态指示该名称是通过广播或 WINS 服务器注册的。 |
| /r | 显示 NetBIOS 名称解析统计信息。 |
| /R | 清除 NetBIOS 名称缓存的内容，然后重新加载**Lmhosts**文件中的预标记条目。 |
| /RR | 释放并刷新向 WINS 服务器注册的本地计算机的 NetBIOS 名称。 |
| /s | 显示 NetBIOS 客户端和服务器会话，尝试将目标 IP 地址转换为名称。 |
| /S | 显示 NetBIOS 客户端和服务器会话，仅按目标 IP 地址列出远程计算机。 |
| `<interval>` | 显示所选统计信息，并按每个显示的*间隔*暂停指定的秒数。 按 CTRL + C 停止显示统计信息。 如果省略此参数，则**nbtstat**仅打印当前配置信息一次。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Nbtstat**命令行参数区分大小写。

- 由**nbtstat**命令生成的列标题包括：

    | 方位 | 说明 |
    | ------- | ----------- |
    | 输入 | 收到的字节数。 |
    | 输出 | 已发送的字节数。 |
    | 输入/输出 | 连接是从计算机 (出站) 还是从另一台计算机连接到本地计算机 (入站) 。 |
    | Life | 名称表缓存条目在清除之前将处于活动的时间。 |
    | 本机名称 | 与连接关联的本地 NetBIOS 名称。 |
    | 远程主机 | 与远程计算机关联的名称或 IP 地址。 |
    | `<03>` | NetBIOS 名称的最后一个字节转换为十六进制。 每个 NetBIOS 名称长度为16个字符。 最后一个字节通常具有特殊意义，因为同一名称可能在计算机上出现多次，只是在最后一个字节内有所不同。 例如， `<20>` 是 ASCII 文本中的空格。 |
    | type | 名称的类型。 名称可以为唯一名称或组名称。 |
    | 状态 | 远程计算机上的 NetBIOS 服务是否正在运行 (注册的) 或者重复的计算机名是否已注册了相同的服务 (冲突) 。 |
    | 州省/自治区/直辖市 | NetBIOS 连接的状态。 |

- 可能的 NetBIOS 连接状态包括：

    | 州省/自治区/直辖市 | 说明 |
    | ------- | ----------- |
    | 连续 | 已建立会话。 |
    | 收听 | 此终结点可用于入站连接。 |
    | 空闲 | 此终结点已打开，但无法接收连接。 |
    | Connecting | 会话正在连接阶段，正在解析目标的名称到 IP 地址映射。 |
    | 接受 | 当前正在接受入站会话，不久将会连接。 |
    | 正在 | 会话正在尝试重新连接 (在第一次尝试) 失败。 |
    | 出站 | 会话正在连接阶段，当前正在创建 TCP 连接。 |
    | 入站 | 入站会话在连接阶段。 |
    | 正在断开连接 | 会话正在断开连接。 |
    | 已断开连接 | 本地计算机发出断开连接，它正在等待来自远程系统的确认。 |

### <a name="examples"></a>示例

若要显示计算机的 netbios 名称为*CORP07*的远程计算机的 netbios 名称表，请键入：

```
nbtstat /a CORP07
```

若要显示分配有*10.0.0.99*IP 地址的远程计算机的 NetBIOS 名称表，请键入：

```
nbtstat /A 10.0.0.99
```

若要显示本地计算机的 NetBIOS 名称表，请键入：

```
nbtstat /n
```

若要显示本地计算机的 NetBIOS 名称缓存内容，请键入：

```
nbtstat /c
```

若要清除 NetBIOS 名称缓存并在本地*Lmhosts*文件中重新加载预标记条目，请键入：

```
nbtstat /R
```

若要释放注册到 WINS 服务器并重新注册的 NetBIOS 名称，请键入：

```
nbtstat /RR
```

若要每隔五秒按 IP 地址显示 NetBIOS 会话统计信息，请键入：

```
nbtstat /S 5
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
