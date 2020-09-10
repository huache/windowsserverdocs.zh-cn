---
title: rpcinfo
description: Rpcinfo 命令的参考文章，其中列出了远程计算机上的程序。
ms.topic: reference
ms.assetid: 7c342232-a8f0-42ff-8f11-d18c4981f5ca
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 3e5865bb976f71b9fbb90e4dd77008f00056a455
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639829"
---
# <a name="rpcinfo"></a>rpcinfo

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

列出远程计算机上的程序。 **Rpcinfo**命令行实用工具为 rpc 服务器 (rpc) 建立远程过程调用，并报告它找到的内容。

## <a name="syntax"></a>语法

```
rpcinfo [/p [<node>]] [/b <program version>] [/t <node program> [<version>]] [/u <node program> [<version>]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /p `[<node>]` | 列出注册到指定主机上的端口映射器的所有程序。 如果未指定节点 (计算机) 名称，程序将查询本地主机上的端口映射器。 |
| /b `<program version>` | 请求所有网络节点的响应，这些网络节点具有注册到端口映射器的指定程序和版本。 必须同时指定程序名称或编号和版本号。 |
| /t `<node program> [\<version>]` | 使用 TCP 传输协议调用指定的程序。 必须同时指定节点 (计算机) 名称和程序名称。 如果未指定版本，程序将调用所有版本。 |
| /u `<node program> [\<version>]` | 使用 UDP 传输协议调用指定的程序。 必须同时指定节点 (计算机) 名称和程序名称。 如果未指定版本，程序将调用所有版本。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要列出注册到端口映射器的所有程序，请键入：

```
rpcinfo /p [<node>]
```

若要从具有指定程序的网络节点请求响应，请键入：

```
rpcinfo /b <program version>
```

若要使用传输控制协议 (TCP) 调用程序，请键入：

```
rpcinfo /t <node program> [<version>]
```

使用用户数据报协议 (UDP) 调用程序：

```
rpcinfo /u <node program> [<version>]
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
