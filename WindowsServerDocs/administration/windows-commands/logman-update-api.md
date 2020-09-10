---
title: logman update api
description: 用于更新现有 API 跟踪数据收集器属性的 logman 更新 api 命令的参考文章。
ms.topic: reference
ms.assetid: 6f322e52-0f9f-42b1-bd64-8b8f8fe086fc
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 016a6728d032393990e1ff1fd0cb5e4e9a20df94
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639944"
---
# <a name="logman-update-api"></a>logman update api

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更新现有 API 跟踪数据收集器的属性。

## <a name="syntax"></a>语法

```
logman update api <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -s `<computer name>` | 在指定的远程计算机上执行命令。 |
| -config `<value>` | 指定包含命令选项的设置文件。 |
| [-n] `<name>` | 目标对象的名称。 |
| -f `<bin|bincirc>` | 指定数据收集器的日志格式。 |
| -[-] u `<user [password]>` | 指定要以其身份运行的用户。 输入 `*` 密码将生成密码提示。 如果你在密码提示符处键入密码，密码不会显示。 |
| -m `<[start] [stop] [[start] [stop] [...]]>` | 更改为手动启动或停止，而不是计划的开始或结束时间。 |
| -rf `<[[hh:]mm:]ss>` | 在指定的时间段内运行数据收集器。 |
| -b `<M/d/yyyy h:mm:ss[AM|PM]>` | 开始在指定时间收集数据。 |
| -e `<M/d/yyyy h:mm:ss[AM|PM]>` | 在指定的时间结束数据收集。 |
| -si `<[[hh:]mm:]ss>` | 指定性能计数器数据收集器的采样间隔。 |
| -o `<path|dsn!log>` | 指定 SQL 数据库中的输出日志文件或 DSN 和日志集名称。 |
| -[-] r | 每日在指定的开始和结束时间重复数据收集器。 |
| -[-] a | 追加现有的日志文件。 |
| -[-] o | 覆盖现有的日志文件。 |
| -[-] v `<nnnnnn|mmddhhmm>` | 将文件版本信息附加到日志文件名称的末尾。 |
| -[-] rc `<task>` | 运行每次关闭日志时指定的命令。 |
| -[-] 最大值 `<value>` | 最大日志文件大小（MB）或 SQL 日志的最大记录数。 |
| -[-] .cnf `<[[hh:]mm:]ss>` | 指定 time 后，在指定的时间过后，将创建一个新的文件。 如果未指定时间，则在超出最大大小时创建新文件。 |
| -y | 在不提示的情况下回答 "是"。 |
| -mods `<path [path [...]]>` | 指定要从中记录 API 调用的模块的列表。 |
| -inapis` <module!api [module!api [...]]>` | 指定要包含在日志记录中的 API 调用的列表。 |
| -exapis `<module!api [module!api [...]]>` | 指定要从日志记录中排除的 API 调用的列表。 |
| -[-] ano | 仅记录 () API 名称，或不记录 () API 名称。 |
| -[-] recursive | 日志 ( 递归) 或不记录 (-递归) Api 在第一层以外递归。 |
| -exe `<value>` | 指定 API 跟踪的可执行文件的完整路径。 |
| /? | 显示区分上下文的帮助。 |

#### <a name="remarks"></a>备注

- 其中列出了 [-]，添加了额外的连字符 ( ) 对该选项求反。

### <a name="examples"></a>示例

若要更新 c:\windows\notepad.exe 的可执行文件 *trace_notepad*的现有 api 跟踪计数器，请通过排除模块 kernel32.dll 生成的 Api 调用 TlsGetValue，键入：

```
logman update api trace_notepad -exe c:\windows\notepad.exe -exapis kernel32.dll!TlsGetValue
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman create api 命令](logman-create-api.md)

- [logman 命令](logman.md)
