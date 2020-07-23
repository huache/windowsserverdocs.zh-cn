---
title: nfsstat
description: Nfsstat 命令的参考文章，其中显示有关网络文件系统（NFS）和远程过程调用（RPC）调用的统计信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da7a9768-44bd-404b-97ee-c388d00dc395
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0eb2836b15c24dc946953c0c82c4b3586971c5bc
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956729"
---
# <a name="nfsstat"></a>nfsstat

一个命令行实用程序，显示有关网络文件系统（NFS）和远程过程调用（RPC）调用的统计信息。 在不使用参数的情况下，此命令将显示所有统计数据，而不重置任何内容。

## <a name="syntax"></a>语法

```
nfsstat [-c][-s][-n][-r][-z][-m]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -c | 显示客户端发送和拒绝的客户端 NFS 和 RPC 调用。 若要仅显示 NFS 或 RPC 信息，请将此标志与 **-n**或 **-r**参数结合。 |
| -S | 仅显示服务器端 NFS 和服务器发送和拒绝的 RPC 调用。 若要仅显示 NFS 或 RPC 信息，请将此标志与 **-n**或 **-r**参数结合。 |
| -m | 显示有关装载选项设置的装载标志、系统内部装载标志以及其他装载信息的信息。 |
| -n | 显示客户端和服务器的 NFS 信息。 若要仅显示 NFS 客户端或服务器信息，请将此标志与 **-c**或 **-s**参数组合在一起。 |
| -r | 显示客户端和服务器的 RPC 信息。 若要仅显示 RPC 客户端或服务器信息，请将此标志与 **-c**或 **-s**参数组合在一起。 |
| -Z | 重置呼叫统计信息。 此标志仅对根用户可用，并可与任何其他参数组合使用，以在显示后重置特定的统计信息集。 |

### <a name="examples"></a>示例

若要显示有关客户端发送和拒绝的 RPC 和 NFS 调用数的信息，请键入：

```
nfsstat -c
```

若要显示和打印客户端 NFS 调用相关信息，请键入：

```
nfsstat -cn
```

若要显示客户端和服务器的 RPC 调用相关信息，请键入：

```
nfsstat -r
```

若要显示有关服务器接收和拒绝的 RPC 和 NFS 调用数的信息，请键入：

```
nfsstat -s
```

若要在客户端和服务器上将所有调用相关信息重置为零，请键入：

```
nfsstat -z
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [网络文件系统命令参考服务](services-for-network-file-system-command-reference.md)

- [NFS cmdlet 参考](/powershell/module/nfs)
