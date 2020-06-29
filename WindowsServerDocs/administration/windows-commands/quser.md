---
title: quser
description: Quser 命令的参考主题，该命令显示远程桌面会话主机服务器上的用户会话的相关信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8056204f-ed11-4c91-bb1d-c799283a48a4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e51abe030ca0f473246cdc85fd01d89fddf8b056
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85471922"
---
# <a name="quser"></a>quser

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程桌面会话主机服务器上的用户会话的相关信息。 可以使用此命令查明特定用户是否登录到特定的远程桌面会话主机服务器。 此命令返回以下信息：

- 用户的名称

- 远程桌面会话主机服务器上的会话名称

- 会话 ID

- 会话的状态（活动或已断开连接）

- 空闲时间（自上一次击键或鼠标移动后的分钟数）

- 用户登录的日期和时间

> [!NOTE]
> 此命令与 "[查询用户" 命令](query-user.md)相同。 若要了解最新版本中的新增功能，请参阅[Windows Server 中远程桌面服务的新增功能](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
quser [<username> | <sessionname> | <sessionID>] [/server:<servername>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<username>` | 指定要查询的用户的登录名。 |
| `<sessionname>` | 指定要查询的会话的名称。 |
| `<sessionID>` | 指定要查询的会话的 ID。 |
| /server:`<servername>` | 指定要查询的远程桌面会话主机服务器。 否则，将使用当前远程桌面会话主机服务器。 仅当在远程服务器上使用此命令时，才需要此参数。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 若要使用此命令，您必须具有 "完全控制" 权限或 "特殊访问" 权限。

- 如果未使用 <用户名> 指定用户，<*会话**名称*> 或*sessionID*参数，则将返回登录到服务器的所有用户的列表。 此外，还可以使用 "**查询会话**" 命令显示服务器上所有会话的列表。

- 当**quser**返回信息时，将在 `(>)` 当前会话之前显示大于号。

### <a name="examples"></a>示例

若要显示有关记录在系统上的所有用户的信息，请键入：

```
quser
```

若要显示有关服务器*Server1*上的用户*USER1*的信息，请键入：

```
quser USER1 /server:Server1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [查询用户命令](query-user.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
