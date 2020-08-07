---
title: relog
description: 重新记录命令的参考文章，可从性能计数器日志文件中提取性能计数器信息。
ms.topic: article
ms.assetid: 7480f6c0-9953-4d70-9b1c-b27e09d8db13
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: c3c60503cf725d05afd4b21ceef5f36c64c2b155
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87883860"
---
# <a name="relog"></a>relog

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将性能计数器日志中的性能计数器提取到其他格式中，例如，以制表符分隔的文本格式的 () 、以逗号分隔的文本) 、二进制-BIN 或 SQL 的文本 CSV (。

>[!NOTE]
>若要详细了解如何将**重新登录合并**到 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) 脚本，请参阅脚本撰写[博客](https://devblogs.microsoft.com/scripting/)。

## <a name="syntax"></a>语法

```
relog [<filename> [<filename> ...]] [/a] [/c <path> [<path> ...]] [/cf <filename>] [/f  {bin|csv|tsv|SQL}] [/t <value>] [/o {outputfile|DSN!CounterLog}] [/b <M/D/YYYY> [[<HH>:] <MM>:] <SS>] [/e <M/D/YYYY> [[<HH>:] <MM>:] <SS>] [/config {<filename>|i}] [/q]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `filename [filename ...]` | 指定现有性能计数器日志的路径名。 可以指定多个输入文件。 |
| -a | 追加输出文件而不是覆盖。 此选项不适用于默认情况下始终追加的 SQL 格式。 |
| -c`path [path ...]` | 指定要记录的性能计数器路径。 若要指定多个计数器路径，请用空格分隔它们，并将计数器路径用引号括起来 (例如 `"path1 path2"`) 。 |
| -cf filename | 指定一个文本文件的路径，该文件列出要包含在重新记文件中的性能计数器。 使用此选项可以在输入文件中列出计数器路径，每行一个。 默认设置为 relogged 原始日志文件中的所有计数器。 |
| -f`{bin | csv | tsv | SQL}` | 指定输出文件格式的路径名。 默认格式为**bin**。 对于 SQL 数据库，输出文件指定 `DSN!CounterLog` 。 您可以使用 ODBC 管理器将 DSN 配置 (数据库系统名称) 来指定数据库位置。 |
| -t 值 | 指定*n*个记录中的采样间隔。 包括重新登录文件中的每个第 n 个数据点。 默认值为每个数据点。 |
| -o`{Outputfile | SQL:DSN!Counter_Log}` | 指定输出文件或将写入计数器的 SQL 数据库的路径名。 <P>**注意：** 对于64位和32位版本的 relog.exe，必须分别在 ODBC 数据源中定义一个 DSN (64 位和32位) 系统上。 使用 "SQL Server" ODBC 驱动程序定义 DSN。 |
| -b`<M/D/YYYY> [[<HH>:]<MM>:]<SS>]` | 指定从输入文件复制第一条记录的开始时间。 日期和时间必须采用以下格式： M/D/YYYYHH： MM： SS。 |
| -e `<M/D/YYYY> [[<HH>:]<MM>:]<SS>]` | 指定从输入文件复制最后一条记录的结束时间。 日期和时间必须采用以下格式： M/D/YYYYHH： MM： SS。 |
| -config`{filename | i}` | 指定包含命令行参数的设置文件的路径名。 如果使用的是配置文件，则可以使用 **-i**作为占位符，获取可放置在命令行上的输入文件的列表。 如果使用的是命令行，请不要使用 **-i**。 你还可以使用通配符，例如 `*.blg` 一次指定多个输入文件名。 |
| -q | 显示在输入文件中指定的日志文件的性能计数器和时间范围。 |
| -y | 通过对所有问题回答 "是"，绕过提示。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 计数器路径的一般格式如下： `[\<computer>] \<object>[<parent>\<instance#index>] \<counter>]` 其中，格式的父对象、实例、索引和计数器组件可能包含有效的名称或通配符。 计算机、父对象、实例和索引组件对于所有计数器都不是必需的。

- 根据计数器本身，确定要使用的计数器路径。 例如，**逻辑磁盘**对象有一个实例 `<index>` ，因此必须提供 `<#index>` 或通配符。 因此，您可以使用以下格式： `\LogicalDisk(*/*#*)\\*` 。

- 相比之下， **Process**对象不需要使用实例 `<index>` 。 因此，您可以使用以下格式： `\Process(*)\ID Process` 。

- 如果在**父**名称中指定了通配符，则将返回与指定的实例和计数器字段匹配的指定对象的所有实例。

- 如果在**实例**名称中指定了通配符，则如果与指定索引对应的所有实例名称匹配通配符，则将返回指定对象和父对象的所有实例。

- 如果在**计数器**名称中指定了通配符，则返回指定对象的所有计数器。

- 部分计数器路径字符串与 (例如，pro * ) 不受支持。

- 计数器文件是一个文本文件，用于列出现有日志中的一个或多个性能计数器。 以格式从日志或 **/q**输出复制完整计数器名称 `<computer>\<object>\<instance>\<counter>` 。 在每行上列出一个计数器路径。

- 运行**时，重新记录命令将**从输入文件中的每个记录复制指定的计数器，并在必要时转换格式。 计数器文件中允许使用通配符路径。

- 使用 **/t**参数指定输入文件按每条记录的间隔插入到输出文件中 `nth` 。 默认情况下，数据从每个记录 relogged。

- 您可以指定您的输出日志中包含开始时间之前的记录 (即 **/b**) 为需要格式化值的计算值的计数器提供数据。 输出文件将包含来自输入文件的最后一条记录，其时间戳小于 **/e** (，即结束时间) 参数。

- 与 **/config**选项一起使用的设置文件的内容应采用以下格式： `<commandoption>\<value>` ，其中 `<commandoption>` 是命令行选项并 `<value>` 指定其值。

##<a name="q-examples"></a>Q # 示例

若要按固定的时间间隔（30、list 计数器路径、输出文件和格式）对现有跟踪日志进行重新采样，请键入：

```
relog c:\perflogs\daily_trace_log.blg /cf counter_file.txt /o c:\perflogs\reduced_log.csv /t 30 /f csv
```

若要按固定的时间间隔（30、list 计数器路径和输出文件）对现有跟踪日志进行重新采样，请键入：

```
relog c:\perflogs\daily_trace_log.blg /cf counter_file.txt /o c:\perflogs\reduced_log.blg /t 30
```

若要将现有跟踪日志重新采样为数据库，请键入：

```
relog "c:\perflogs\daily_trace_log.blg" -f sql -o "SQL:sql2016x64odbc!counter_log"
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
