---
title: msg
description: Msg 命令的参考文章，可将消息发送到远程桌面会话主机服务器上的用户
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9501cf3e-568e-4982-9987-8daecc6c17ff
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6eff557b1fb7eb2c5f67b2902762786bbfc839c1
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934971"
---
# <a name="msg"></a>msg

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

向远程桌面会话主机服务器上的用户发送消息。

> [!NOTE]
> 您必须具有消息特殊访问权限才能发送消息。

## <a name="syntax"></a>语法

```
msg {<username> | <sessionname> | <sessionID>| @<filename> | *} [/server:<servername>] [/time:<seconds>] [/v] [/w] [<message>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<username>` | 指定要接收该消息的用户的名称。 如果未指定用户或会话，此命令会显示错误消息。 指定会话时，它必须是活动的。 |
| `<sessionname>` | 指定要接收消息的会话的名称。 如果未指定用户或会话，此命令会显示错误消息。 指定会话时，它必须是活动的。 |
| `<sessionID>` | 指定要接收消息的会话的数字 ID。 |
| `@<filename>` | 标识一个文件，该文件包含要接收消息的用户名、会话名称和会话 Id 的列表。 |
| * | 将消息发送到系统中的所有用户名。 |
| /server:`<servername>` | 指定您要接收消息的会话或用户的远程桌面会话主机服务器。 如果未指定， **/server**将使用你当前登录到的服务器。 |
| /time`<seconds>` | 指定您发送的消息在用户屏幕上显示的时间长度。 在达到时间限制后，消息将消失。 如果未设置时间限制，则在用户看到该消息并单击 **"确定"** 之前，消息将保留在用户屏幕上。 |
| /v | 显示要执行的操作的相关信息。 |
| /W | 等待用户确认已收到消息。 如果用户不立即响应，请将此参数与结合使用 `/time:<*seconds*>` 以避免可能的长时间延迟。 将此参数与 **/v**一起使用也很有用。 |
| `<message>` | 指定要发送的消息的文本。 如果未指定邮件，系统将提示您输入一条消息。 若要发送文件中包含的消息，请键入小于号（<）符号，后跟文件名。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要发送有权使用的消息，*现在我们*将为*User1*的所有会话提供帮助，请键入：

```
msg User1 Let's meet at 1PM today
```

若要将同一消息发送到 session *modeM02*，请键入：

```
msg modem02 Let's meet at 1PM today
```

若要将消息发送到文件*userlist*中包含的所有会话，请键入：

```
msg @userlist Let's meet at 1PM today
```

若要将消息发送给所有已登录的用户，请键入：

```
msg * Let's meet at 1PM today
```

若要将消息发送给所有用户，并且具有确认超时（例如10秒），请键入：

```
msg * /time:10 Let's meet at 1PM today
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
