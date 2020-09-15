---
title: eventcreate
description: Eventcreate 命令的参考文章，它使管理员能够在指定的事件日志中创建自定义事件。
ms.topic: reference
ms.assetid: f2b1b26d-a70e-49a6-832b-91eb5a1a159a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d2fa1e4a90d0c24138c5353c5cf1b22308204d6f
ms.sourcegitcommit: 0b3d6661c44aa1a697087e644437279142726d84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90083648"
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
| /s `<computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| /u `<domain\user>` | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain\user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| /p `<password>` | 指定在 **/u** 参数中指定的用户帐户的密码。 |
| /l `{APPLICATION | SYSTEM}` | 指定将在其中创建事件的事件日志的名称。 有效的日志名称为 " **应用程序** " 或 " **系统**"。 |
| /so `<srcname>` | 指定要用于事件的源。 有效的源可以是任何字符串，并且应表示生成事件的应用程序或组件。 |
| /t `{ERROR | WARNING | INFORMATION | SUCCESSAUDIT | FAILUREAUDIT}` | 指定要创建的事件类型。 有效的类型为 **ERROR**、 **WARNING**、 **INFORMATION**、 **SUCCESSAUDIT**和 **FAILUREAUDIT**。 |
| /id `<eventID>` | 指定事件的事件 ID。 有效的 ID 是从1到1000的任何数字。 |
| /d `<description>` | 指定要用于新创建的事件的说明。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

下面的示例演示如何使用 **eventcreate** 命令：

```
eventcreate /t ERROR /id 100 /l application /d "Create event in application log"
eventcreate /t INFORMATION /id 1000 /d "Create event in WinMgmt source"
eventcreate /t ERROR /id 201 /so winword /l application /d "New src Winword in application log"
eventcreate /s server /t ERROR /id 100 /l application /d "Remote machine without user credentials"
eventcreate /s server /u user /p password /id 100 /t ERROR /l application /d "Remote machine with user credentials"
eventcreate /s server1 /s server2 /u user /p password /id 100 /t ERROR /d "Creating events on Multiple remote machines"
eventcreate /s server /u user /id 100 /t WARNING /d "Remote machine with partial user credentials"
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
