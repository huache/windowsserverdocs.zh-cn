---
title: 注销
description: "\"注销\" 命令的参考文章，用于从远程桌面会话主机服务器上的会话中注销用户并删除会话。"
ms.topic: reference
ms.assetid: 939f09cc-de8c-436c-a05d-aca5f2a06371
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b7a211f1b4bcb76ea63d79ae38d1cf78c757d6e0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639319"
---
# <a name="logoff"></a>注销

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将用户从远程桌面会话主机服务器上的会话中注销并删除会话。

## <a name="syntax"></a>语法
```
logoff [<sessionname> | <sessionID>] [/server:<servername>] [/v]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<sessionname>` | 指定会话的名称。 这必须是活动会话。|
| `<sessionID>` | 指定标识服务器会话的数字 ID。 |
| /server:`<servername>` | 指定包含要注销其用户的会话的远程桌面会话主机服务器。 如果未指定，则使用当前处于活动状态的服务器。 |
| /v | 显示要执行的操作的相关信息。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 你始终可以从你当前登录到的会话中注销。 但是，您必须拥有 " **完全控制** " 权限才能从其他会话注销用户。

- 从会话中注销用户而不发出警告可能导致用户会话中的数据丢失。 在执行此操作之前，应使用 **msg** 命令向用户发送消息来警告用户。

- 如果 `<sessionID>` `<sessionname>` 未指定或，则 **注销** 将从当前会话中注销用户。

- 注销用户后，所有进程都将结束，并且将从服务器中删除该会话。

- 不能从控制台会话中注销用户。

### <a name="examples"></a>示例

若要从当前会话中注销用户，请键入：

```
logoff
```

若要使用会话的 ID （例如 *会话 12*）从会话中注销用户，请键入：

```
logoff 12
```

若要使用会话和服务器的名称从会话中注销用户，例如，在*Server1*上使用 session *TERM04* ，请键入：

```
logoff TERM04 /server:Server1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
