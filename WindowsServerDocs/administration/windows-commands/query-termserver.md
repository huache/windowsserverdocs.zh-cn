---
title: query termserver
description: Query termserver 命令的参考文章，其中显示了网络上所有远程桌面会话主机服务器的列表。
ms.topic: reference
ms.assetid: 3b89d3b4-236f-4376-90b6-939a0ec4b288
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 33abf76e66b2d42cf0368503fa3a6e119dc1fd1c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639875"
---
# <a name="query-termserver"></a>query termserver

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示网络上所有远程桌面会话主机服务器的列表。 此命令将在网络上搜索所有附加的远程桌面会话主机服务器，并返回以下信息：

- 服务器的名称

- 如果使用/address 选项，则为网络 (和节点地址) 

> [!NOTE]
> 若要了解最新版本中的新增功能，请参阅 [Windows Server 中远程桌面服务的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
query termserver [<servername>] [/domain:<domain>] [/address] [/continue]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<servername>` | 指定标识远程桌面会话主机服务器的名称。 |
| /domain`<domain>` | 指定要查询终端服务器的域。 如果要查询当前正在工作的域，则无需指定域。 |
| /address | 显示每个服务器的网络和节点地址。 |
| /continue | 阻止显示每个信息屏幕后暂停。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要显示有关网络上所有远程桌面会话主机服务器的信息，请键入：

```
query termserver
```

若要显示有关名为 *Server3*的远程桌面会话主机服务器的信息，请键入：

```
query termserver Server3
```

若要显示有关域 *CONTOSO*中所有远程桌面会话主机服务器的信息，请键入：

```
query termserver /domain:CONTOSO
```

若要显示名为 *Server3*的远程桌面会话主机服务器的网络和节点地址，请键入：

```
query termserver Server3 /address
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [查询命令](query.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
