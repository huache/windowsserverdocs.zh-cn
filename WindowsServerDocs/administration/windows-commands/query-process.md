---
title: 查询进程
description: "\"查询处理\" 命令的参考文章，其中显示了有关在远程桌面会话主机服务器上运行的进程的信息。"
ms.topic: reference
ms.assetid: 36ce3ffc-0092-4eb1-a374-28e6616ca946
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: eb2deaeac012eba4dad06ae6084474942536adfd
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639900"
---
# <a name="query-process"></a>查询进程

适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关在远程桌面会话主机服务器上运行的进程的信息。 您可以使用此命令来找出特定用户正在运行的程序，以及哪些用户在运行特定程序。 此命令返回以下信息：

- 拥有此过程的用户

- 拥有进程的会话

- 会话的 ID

- 进程的名称

- 进程的 ID

> [!NOTE]
> 若要了解最新版本中的新增功能，请参阅 [Windows Server 中远程桌面服务的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
query process [*|<processID>|<username>|<sessionname>|/id:<nn>|<programname>] [/server:<servername>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| * | 列出所有会话的进程。 |
| `<processID>` | 指定标识要查询的进程的数字 ID。 |
| `<username>` | 指定要列出其进程的用户的名称。 |
| `<sessionname>` | 指定要列出其进程的活动会话的名称。 |
| /id`<nn>` | 指定要列出其进程的会话的 ID。 |
| `<programname>` | 指定要查询其进程的程序的名称。 .Exe 扩展名是必需的。 |
| /server:`<servername>` | 指定要列出其进程的远程桌面会话主机服务器。 如果未指定，则使用你当前登录到的服务器。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 管理员对所有 **查询处理** 函数具有完全访问权限。

- 如果未指定 <*用户名*>、<*会话*名称>、 */id `<nn>` ：*、<*programname*> 或 *&#42;* 参数，则此查询仅显示属于当前用户的进程。

- 当 **查询过程** 返回信息时，将在 `(>)` 每个属于当前会话的进程之前显示大于号。

## <a name="examples"></a>示例

若要显示有关所有会话正在使用的进程的信息，请键入：

```
query process *
```

若要显示有关 *会话 ID 2*使用的进程的信息，请键入：

```
query process /ID:2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [查询命令](query.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
