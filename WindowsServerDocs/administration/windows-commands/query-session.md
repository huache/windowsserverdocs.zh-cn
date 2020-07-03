---
title: query session
description: 查询会话命令的参考文章，其中显示了有关远程桌面会话主机服务器上的会话的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: abc0ace8-0b74-4b6e-a937-a78bb4b61a1f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 440830af55763fbb3ebee7cdbdca97ca11cde30c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937046"
---
# <a name="query-session"></a>query session

适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关远程桌面会话主机服务器上的会话的信息。 此列表不仅包括有关活动会话的信息，还包括有关服务器运行的其他会话的信息。

> [!NOTE]
> 若要了解最新版本中的新增功能，请参阅[Windows Server 中远程桌面服务的新增功能](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
query session [<sessionname> | <username> | <sessionID>] [/server:<servername>] [/mode] [/flow] [/connect] [/counter]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<sessionname>` | 指定要查询的会话的名称。 |
| `<username>` | 指定要查询其会话的用户的名称。 |
| `<sessionID>` | 指定要查询的会话的 ID。 |
| /server:`<servername>` | 标识要查询的 rd 会话主机服务器。 默认值为当前服务器。 |
| /mode | 显示当前行设置。 |
| /flow | 显示当前的流控制设置。 |
| /connect | 显示当前连接设置。 |
| /counter | 显示当前计数器信息，包括创建、断开连接和重新连接的会话总数。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 用户始终可以查询用户当前登录到的会话。 若要查询其他会话，用户必须具有特殊访问权限。

- 如果未使用 <用户名> 指定会话，<*会话**名称*> 或*sessionID*参数，此查询将显示系统中所有活动会话的相关信息。

- 当**查询会话**返回信息时，将在 `(>)` 当前会话之前显示大于号。 例如：

    ```
    C:\>query session
        SESSIONNAME     USERNAME        ID STATE    TYPE    DEVICE
        console         Administrator1  0 active    wdcon
        >rdp-tcp#1      User1           1 active    wdtshare
        rdp-tcp                         2 listen    wdtshare
                                        4 idle
                                        5 idle
    ```

    其中：
  - **SESSIONNAME**指定分配给会话的名称。
  - **用户名**表示连接到该会话的用户的用户名。
  - **状态**提供有关会话的当前状态的信息。
  - **类型**指示会话类型。
  - **设备**（对于控制台或网络连接的会话不存在）是分配给会话的设备名称。
  - 初始状态配置为 "已禁用" 的任何会话将不会显示在 "**查询会话**" 列表中，直到它们启用。

### <a name="examples"></a>示例

若要显示有关服务器*Server2*上的所有活动会话的信息，请键入：

```
query session /server:Server2
```

若要显示有关活动会话*modeM02*的信息，请键入：

```
query session modeM02
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [查询命令](query.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
