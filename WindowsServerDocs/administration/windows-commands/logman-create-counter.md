---
title: logman create counter
description: 用于创建计数器数据收集器的 logman create counter 命令的参考文章。
ms.topic: reference
ms.assetid: 1e214c32-b704-43c1-b548-e1cf43b583c3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6e0d30cc175d2450a77a747985281cb8d9a8558f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640187"
---
# <a name="logman-create-counter"></a>logman create counter

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建计数器数据收集器。

## <a name="syntax"></a>语法

```
logman create counter <[-n] <name>> [options]
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
| -e `<M/d/yyyy h:mm:ss[AM|PM]>` | 结束在指定时间收集的数据。 |
| -si `<[[hh:]mm:]ss>` | 指定性能计数器数据收集器的采样间隔。 |
| -o `<path|dsn!log>` | 指定 SQL 数据库中的输出日志文件或 DSN 和日志集名称。 |
| -[-] r | 每日在指定的开始和结束时间重复数据收集器。 |
| -[-] a | 追加现有的日志文件。 |
| -[-] o | 覆盖现有的日志文件。 |
| -[-] v `<nnnnnn|mmddhhmm>` | 将文件版本信息附加到日志文件名称的末尾。 |
| -[-] rc `<task>` | 运行每次关闭日志时指定的命令。 |
| -[-] 最大值 `<value>` | 最大日志文件大小（MB）或 SQL 日志的最大记录数。 |
| -[-] .cnf `<[[hh:]mm:]ss>` | 指定 time 后，在指定的时间已过后创建新的文件。 如果未指定时间，则在超出最大大小时创建新文件。 |
| -y | 在不提示的情况下回答 "是"。 |
| -cf `<filename>` | 指定列出要收集的性能计数器的文件。 该文件应包含每行一个性能计数器名称。 |
| -c `<path [path [ ]]>` | 指定要收集)  (性能计数器。 |
| -sc `<value>` | 指定要使用性能计数器数据收集器收集的样本的最大数目。 |
| /? | 显示区分上下文的帮助。 |

#### <a name="remarks"></a>备注

- 其中列出了 [-]，添加了额外的连字符 ( ) 对该选项求反。

### <a name="examples"></a>示例

若要使用处理器 (_Total) 计数器类别中的% Processor time 计数器创建名为 *perf_log* 的计数器，请键入：

```
logman create counter perf_log -c \Processor(_Total)\% Processor time
```

若要创建一个名为 *perf_log* 的计数器，请使用处理器 (_Total) 计数器类别中的% Processor time 计数器，创建最大大小为 10 MB 的日志文件，并收集1分钟到0秒的数据，请键入：

```
logman create counter perf_log -c \Processor(_Total)\% Processor time -max 10 -rf 01:00
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [logman update counter 命令](logman-update-counter.md)

- [logman 命令](logman.md)
