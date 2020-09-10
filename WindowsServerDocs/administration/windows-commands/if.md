---
title: if
description: 用于在 batch 程序中执行条件处理的 if 命令的参考文章。
ms.topic: reference
ms.assetid: 698b3fb9-532b-4c2b-af7f-179f8dc57131
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9bb3c29b7d77b6b1e07e647735701be3171cfb85
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634574"
---
# <a name="if"></a>if

在批处理程序中执行条件处理。

## <a name="syntax"></a>语法

```
if [not] ERRORLEVEL <number> <command> [else <expression>]
if [not] <string1>==<string2> <command> [else <expression>]
if [not] exist <filename> <command> [else <expression>]
```

如果启用了命令扩展，请使用以下语法：

```
if [/i] <string1> <compareop> <string2> <command> [else <expression>]
if cmdextversion <number> <command> [else <expression>]
if defined <variable> <command> [else <expression>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| not | 指定仅当条件为 false 时才应执行该命令。 |
| errorlevel `<number>` | 仅当由 Cmd.exe 运行的上一个程序返回等于或大于 *数字*的退出代码时，才指定 true 条件。 |
| `<command>` | 如果满足前面的条件，则指定应执行的命令。 |
| `<string1>==<string2>` | 仅当 *string1* 和 *string2* 相同时，才指定 true 条件。 这些值可以是文本字符串或批处理变量 (例如 `%1`) 。 不需要将文字字符串括在引号中。 |
| 处于 `<filename>` | 如果指定的文件名存在，则指定 true 条件。 |
| `<compareop>` | 指定由三个字母构成的比较运算符，包括：<ul><li>**等于** -等于</li><li>**NEQ** -不等于</li><li>**LSS** -小于</li><li>**LEQ** -小于或等于</li><li>**GTR** -大于</li><li>**GEQ** -大于或等于</li></ul> |
| /i | 强制字符串比较忽略大小写。 如果为， **/i**则可以使用的 `string1==string2` 形式**if**的/i。 这些比较是泛型的，因为如果 *string1* 和 *string2* 只包含数字，则会将字符串转换为数字，并执行数值比较。 |
| cmdextversion `<number>` | 仅当与 Cmd.exe 的命令扩展功能相关联的内部版本号等于或大于指定的数字时，才指定 true 条件。 第一个版本为1。 当向命令扩展添加重大增强功能时，它会递增1。 默认情况下， (禁用命令扩展时， **cmdextversion** 条件始终为 true，) 启用命令扩展。 |
| defined `<variable>` | 如果定义了 *变量* ，则指定 true 条件。 |
| `<expression>` | 指定要传递给 **else** 子句中的命令的命令行命令和任何参数。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果在 **if** 子句中指定的条件为 true，则执行条件下的命令。如果条件为 false，则忽略 **if** 子句中的命令，该命令将执行 **else** 子句中指定的任何命令。

- 当程序停止时，它将返回退出代码。 若要使用退出代码作为条件，请使用 **errorlevel** 参数。

- 如果你使用 **定义**的，则以下三个变量将添加到环境中： **% errorlevel%**、 **% cmdcmdline%** 和 **% cmdextversion%**。

  - **% errorlevel%**：展开为 errorlevel 环境变量的当前值的字符串表示形式。 此变量假定尚没有名称为 ERRORLEVEL 的现有环境变量。 如果有，则会改为获取该 ERRORLEVEL 值。

  - **% cmdcmdline%**：扩展到 Cmd.exe 之前传递到 Cmd.exe 的原始命令行。 这假设尚不存在名为 CMDCMDLINE 的环境变量。 如果有，则会改为获取该 CMDCMDLINE 值。

  - **% cmdextversion%**：展开为 **cmdextversion**的当前值的字符串表示形式。 这假设尚不存在名为 CMDEXTVERSION 的环境变量。 如果有，则会改为获取该 CMDEXTVERSION 值。

- 在**if**之后，必须在命令所在的行上使用**else**子句。

### <a name="examples"></a>示例

若要显示消息 "找不到文件，则找 **不到数据文件**"，请键入：

```
if not exist product.dat echo Cannot find data file
```

若要格式化驱动器 A 中的磁盘，并在格式化过程中出现错误时显示一条错误消息，请在批处理文件中键入以下行：

```
:begin
@echo off
format a: /s
if not errorlevel 1 goto end
echo An error occurred during formatting.
:end
echo End of batch program.
```

若要从当前目录中删除文件 Product .dat，或在找不到 Product .dat 时显示消息，请在批处理文件中键入以下行：

```
IF EXIST Product.dat (
del Product.dat
) ELSE (
echo The Product.dat file is missing.
)
```

> [!NOTE]
> 可以按如下所示将这些行合并为一行：
> ```
> IF EXIST Product.dat (del Product.dat) ELSE (echo The Product.dat file is missing.)
> ```

若要在运行批处理文件后回显 ERRORLEVEL 环境变量的值，请在批处理文件中键入以下行：

```
goto answer%errorlevel%
:answer1
echo The program returned error level 1
goto end
:answer0
echo The program returned error level 0
goto end
:end
echo Done!
```

若要在 ERRORLEVEL 环境变量的值小于或等于1的情况下切换到 ok 标签，请键入：

```
if %errorlevel% LEQ 1 goto okay
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [goto 命令](goto.md)
