---
title: echo
description: 用于显示消息或打开或关闭命令回显功能的 echo 命令的参考文章。
ms.topic: reference
ms.assetid: fb9fcd0f-5e73-4504-aa95-78204e1a79d3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aca758e2eec979fa4b90a4de4f0fbb6119a3d74a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030755"
---
# <a name="echo"></a>echo

显示消息或打开或关闭命令回显功能。 如果不使用参数， **echo** 将显示当前的回显设置。

## <a name="syntax"></a>语法

```
echo [<message>]
echo [on | off]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| [ \| 关闭时] | 打开或关闭命令回显功能。 默认情况下，命令回显处于启用状态。 |
| `<message>` | 指定要在屏幕上显示的文本。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- `echo <message>`当**回响**关闭时，此命令特别有用。 若要在不显示任何命令的情况下显示长达几行的消息，可以 `echo <message>` 在批处理程序中的 " **echo off** " 命令后包含多个命令。

- 关闭 **回响** 后，命令提示符窗口中不会显示命令提示符。 若要显示命令提示符，请 **在上键入 echo。**

- 如果在批处理文件中使用， **回响** 和 **echo off** 不会影响命令提示符下的设置。

- 若要防止在批处理文件中回显特定命令，请 `@` 在命令前面插入一个登录。 若要防止在批处理文件中回显所有命令，请在文件开头包含 **回响 off** 命令。

- 若要 `|` 在使用 echo 时显示管道 () 或重定向字符 (`<` 或 `>`) ，请在**echo** `^` 管道或重定向字符之前立即使用插入符号 () 。 例如，、 `^|` `^>` 或 `^<`) 。 若要显示插入符号，请连续键入两个插入符号 (`^^`) 。

### <a name="examples"></a>示例

若要显示当前 **echo** 设置，请键入：

```
echo
```

若要在屏幕上回显空白行，请键入：

```
echo.
```

> [!NOTE]
> 句点前不要包含空格。 否则，将显示句点而不是空行。

若要在命令提示符处阻止回显命令，请键入：

```
echo off
```

> [!NOTE]
> 关闭 **回响** 后，命令提示符窗口中不会显示命令提示符。 若要再次显示命令提示符，请 **在上键入 echo**。

若要防止批处理文件中的所有命令 (包括 **echo off** 命令) 在屏幕上显示在批处理文件类型的第一行：

```
@echo off
```

可以使用 **echo** 命令作为 **if** 语句的一部分。 例如，若要在当前目录中搜索文件扩展名为 rpt 的任何文件，并在找到此类文件时回显消息，请键入：

```
if exist *.rpt echo The report has arrived.
```

以下批处理文件将在当前目录中搜索 .txt 文件扩展名的文件，并显示一条消息，指出搜索结果：

```
@echo off
if not exist *.txt (
echo This directory contains no text files.
) else (
   echo This directory contains the following text files:
   echo.
   dir /b *.txt
   )
```

如果在批处理文件运行时找不到 .txt 文件，将显示以下消息：

```
This directory contains no text files.
```

如果在运行批处理文件时找到 .txt 文件，则以下输出会显示 (此示例，假定 File1.txt、File2.txt 和 File3.txt 存在的文件) ：

```
This directory contains the following text files:
File1.txt
File2.txt
File3.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
