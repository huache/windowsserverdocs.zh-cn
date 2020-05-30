---
title: logman 更新跟踪
description: Logman update trace 命令的参考主题，用于更新现有事件跟踪数据收集器的属性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b7111f7f-4162-4d1a-8e53-d766db0ede1f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9edb8df5d5d7e2f3c3f1ccf17fbd817efe4faa10
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222756"
---
# <a name="logman-update-trace"></a>logman 更新跟踪

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更新现有事件跟踪数据收集器的属性。

## <a name="syntax"></a>语法

```
logman update trace <[-n] <name>> [options]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -s`<computer name>` | 在指定的远程计算机上执行命令。 |
| -config`<value>` | 指定包含命令选项的设置文件。 |
| -ets | 直接向事件跟踪会话发送命令，而无需保存或计划。 |
| [-n]`<name>` | 目标对象的名称。 |
| -f`<bin|bincirc>` | 指定数据收集器的日志格式。 |
| -[-] u`<user [password]>` | 指定要以其身份运行的用户。 输入 `*` 密码将生成密码提示。 如果你在密码提示符处键入密码，密码不会显示。 |
| -m`<[start] [stop] [[start] [stop] [...]]>` | 更改为手动启动或停止，而不是计划的开始或结束时间。 |
| -rf`<[[hh:]mm:]ss>` | 在指定的时间段内运行数据收集器。 |
| -b`<M/d/yyyy h:mm:ss[AM|PM]>` | 开始在指定时间收集数据。 |
| -e `<M/d/yyyy h:mm:ss[AM|PM]>` | 结束在指定时间收集的数据。 |
| -o`<path|dsn!log>` | 指定 SQL 数据库中的输出日志文件或 DSN 和日志集名称。 |
| -[-] r | 每日在指定的开始和结束时间重复数据收集器。 |
| -[-] a | 追加现有的日志文件。 |
| -[-] o | 覆盖现有的日志文件。 |
| -[-] v`<nnnnnn|mmddhhmm>` | 将文件版本信息附加到日志文件名称的末尾。 |
| -[-] rc`<task>` | 运行每次关闭日志时指定的命令。 |
| -[-] 最大值`<value>` | 最大日志文件大小（MB）或 SQL 日志的最大记录数。 |
| -[-] .cnf`<[[hh:]mm:]ss>` | 指定 time 后，在指定的时间过后，将创建一个新的文件。 如果未指定时间，则在超出最大大小时创建新文件。 |
| -y | 在不提示的情况下回答 "是"。 |
| -ct`<perf|system|cycle>` | 指定事件跟踪会话时钟类型。 |
| -ln`<logger_name>` | 指定事件跟踪会话的记录器名称。 |
| -ft`<[[hh:]mm:]ss>` | 指定事件跟踪会话刷新计时器。 |
| -[-] p`<provider [flags [level]]>` | 指定要启用的单个事件跟踪提供程序。 |
| -pf`<filename>` | 指定列出多个要启用的事件跟踪提供程序的文件。 文件应为一个文本文件，每行包含一个访问接口。 |
| -[-] rt | 实时运行事件跟踪会话。 |
| -[-] ul | 在用户中运行事件跟踪会话。 |
| -bs.1770`<value>` | 指定事件跟踪会话缓冲区大小（kb）。 |
| -nb`<min max>` | 指定事件跟踪会话缓冲区的数量。 |
| -模式`<globalsequence|localsequence|pagedmemory>` | 指定事件跟踪会话记录器模式，其中包括：<ul><li>**Globalsequence** -指定事件跟踪器将序列号添加到它接收的每个事件，而不考虑哪个跟踪会话收到了该事件。</li><li>**Localsequence** -指定事件跟踪器为在特定跟踪会话中接收的事件添加序列号。 使用此选项时，重复的序列号可以在所有会话中存在，但在每个跟踪会话中是唯一的。</li><li>**Pagedmemory** -指定事件跟踪器使用分页内存而不是默认的非分页内存池来实现其内部缓冲区分配。</li></ul> |
| /? | 显示区分上下文的帮助。 |

#### <a name="remarks"></a>备注

- 其中列出了 [-]，添加额外的连字符（-）将对选项求反。

### <a name="examples"></a>示例

若要更新名为*trace_log*的现有事件跟踪数据收集器，将最大日志大小更改为 10 MB，将日志文件格式更新为 CSV，并以 mmddhhmm 格式追加文件版本控制，请键入：

```
logman update trace trace_log -max 10 -f csv -v mmddhhmm
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman 创建跟踪命令](logman-create-trace.md)

- [logman 命令](logman.md)
