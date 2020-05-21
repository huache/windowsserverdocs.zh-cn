---
title: eventcreate
description: Eventcreate 命令的参考主题，它使管理员能够在指定的事件日志中创建自定义事件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f2b1b26d-a70e-49a6-832b-91eb5a1a159a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8348e61f6cd94c9b660d0ad9cac4cb1f96920cad
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436872"
---
# <a name="eventcreate"></a>eventcreate

使管理员能够在指定的事件日志中创建自定义事件。

> [!IMPORTANT]
> 不能将自定义事件写入安全日志。

## <a name="syntax"></a>语法

```
eventcreate [/s <computer> [/u <domain\user> [/p <password>]] {[/l {APPLICATION|SYSTEM}]|[/so <srcname>]} /t {ERROR|WARNING|INFORMATION|SUCCESSAUDIT|FAILUREAUDIT} /id <eventID> /d <description>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| /s`<computer>` | 指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。 |
| /u`<domain\user>` | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain\user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| /p`<password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| /l`{APPLICATION | SYSTEM}` | 指定将在其中创建事件的事件日志的名称。 有效的日志名称为 "**应用程序**" 或 "**系统**"。 |
| /so`<srcname>` | 指定要用于事件的源。 有效的源可以是任何字符串，并且应表示生成事件的应用程序或组件。 |
| /t`{ERROR | WARNING | INFORMATION | SUCCESSAUDIT | FAILUREAUDIT}` | 指定要创建的事件类型。 有效的类型为**ERROR**、 **WARNING**、 **INFORMATION**、 **SUCCESSAUDIT**和**FAILUREAUDIT**。 |
| /id`<eventID>` | 指定事件的事件 ID。 有效的 ID 是从1到1000的任何数字。 |
| /d`<description>` | 指定要用于新创建的事件的说明。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

下面的示例演示如何使用**eventcreate**命令：

```
eventcreate /t error /id 100 /l application /d Create event in application log
eventcreate /t information /id 1000 /so winmgmt /d Create event in WinMgmt source
eventcreate /t error /id 2001 /so winword /l application /d new src Winword in application log
eventcreate /s server /t error /id 100 /l application /d Remote machine without user credentials
eventcreate /s server /u user /p password /id 100 /t error /l application /d Remote machine with user credentials
eventcreate /s server1 /s server2 /u user /p password /id 100 /t error /so winmgmt /d Creating events on Multiple remote machines
eventcreate /s server /u user /id 100 /t warning /so winmgmt /d Remote machine with partial user credentials
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
