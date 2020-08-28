---
title: fc
description: Fc 命令的参考文章，它比较两个文件或文件集，并显示它们之间的差异。
ms.topic: reference
ms.assetid: 485fc3d8-b7c5-496d-87be-0011112f27d5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eb4bd745ec9c1a9dfe066fd5eeefdc2d5517d7cb
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036625"
---
# <a name="fc"></a>fc

比较两个文件或文件集，并显示它们之间的差异。

## <a name="syntax"></a>语法

```
fc /a [/c] [/l] [/lb<n>] [/n] [/off[line]] [/t] [/u] [/w] [/<nnnn>] [<drive1>:][<path1>]<filename1> [<drive2>:][<path2>]<filename2>
fc /b [<drive1:>][<path1>]<filename1> [<drive2:>][<path2>]<filename2>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /a | 缩写 ASCII 比较的输出。 **Fc**只显示每个差异集的第一行和最后一行，而不是显示所有不同的行。 |
| /b | 在二进制模式下将两个文件按字节进行比较，并且不会在找到不匹配后尝试重新同步文件。 这是比较具有以下文件扩展名的文件的默认模式： .exe、.com、.sys、.obj、.lib 或 bin。 |
| /c | 忽略字母大小写。 |
| /l | 在 ASCII 模式下逐行比较文件，并在找到不匹配项后尝试重新同步文件。 这是用于比较文件的默认模式，但文件扩展名为： .exe、.com、.sys、.obj、.lib 或 bin。 |
| /lb`<n>` | 将内部行缓冲区的行数设置为 *N*。行缓冲区的默认长度为100行。 如果要比较的文件具有超过100个连续不同的行， **fc** 会取消比较。 |
| /n | 在 ASCII 比较中显示行号。 |
| /off [line] | 不会跳过设置了脱机属性的文件。 |
| /t  | 阻止 **fc** 将制表符转换为空格。 默认行为是将制表符视为空格，并在每八个字符位置停止。 |
| /U | 将文件作为 Unicode 文本文件进行比较。 |
| /W | 压缩空白 (即，在比较期间) 制表符和空格。 如果行包含多个连续的空格或制表符，则 **/w** 会将这些字符视为单个空格。 与 **/w**一起使用时， **fc** 将忽略行开头和结尾处的空格。 |
| /`<nnnn>` | 指定在 **fc** 认为要重新同步的文件之前，必须在不匹配的情况下匹配的连续行数。 如果文件中的匹配行数小于 *nnnn*， **fc** 会将匹配行显示为不同。 默认值为 2。 |
| `[<drive1>:][<path1>]<filename1>` | 指定要比较的第一个文件或一组文件的位置和名称。 *filename1* 是必需的。 |
| `[<drive2>:][<path2>]<filename2>` | 指定要比较的第二个文件或文件集的位置和名称。 *filename2* 是必需的。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 此命令 implemeted c:\WINDOWS\fc.exe。 可以在 PowerShell 中使用此命令，但请务必将完整的可执行文件拼写 ( # A0) ，因为 "fc" 也是格式自定义的别名。

- 使用 **fc** 进行 ASCII 比较时， **fc** 会按以下顺序显示两个文件之间的差异：

  - 第一个文件的名称

  - 不同文件之间的 *filename1* 的行

  - 要在两个文件中匹配的第一行

  - 第二个文件的名称

  - 不同 *filename2* 的行

  - 要匹配的第一行

- **/b** 显示在二进制比较过程中发现的不匹配项，采用以下语法：

    `\<XXXXXXXX: YY ZZ>`

    *Xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx*的值指定从文件开头开始度量的字节对的相对十六进制地址。 地址以00000000开头。 *YY*和*ZZ*的十六进制值分别表示*filename1*和*filename2*中不匹配的字节。

- 可以在*filename1*和*filename2*中使用 (**&#42;** 和 **？**) 的通配符。 如果在 *filename1*中使用通配符， **fc** 会将所有指定的文件与 *filename2*指定的文件或文件集进行比较。 如果在 *filename2*中使用通配符， **fc** 将使用 *filename1*中的相应值。

- 比较 ASCII 文件时， **fc** 使用内部缓冲区 (足够大，以将100行保存) 为存储。 如果文件大于缓冲区， **fc** 就会将它加载到缓冲区中的内容进行比较。 如果 **fc** 在文件的加载部分中找不到匹配项，它将停止并显示以下消息：

    `Resynch failed. Files are too different.`

    比较大于可用内存的二进制文件时， **fc** 会完全比较这两个文件，将内存中的部分覆盖到磁盘中的下一部分。 此输出与完全容纳在内存中的文件的输出相同。

### <a name="examples"></a>示例

若要对两个文本文件（ *rpt* 和 *RPT*）进行 ASCII 比较，并以缩写格式显示结果，请键入：

```
fc /a monthly.rpt sales.rpt
```

若要对两个批处理文件进行二进制比较（ *profits.bat* 和 *earnings.bat*），请键入：

```
fc /b profits.bat earnings.bat
```

将显示类似于以下内容的结果：

```
00000002: 72 43
00000004: 65 3A
0000000E: 56 92
000005E8: 00 6E
FC: earnings.bat longer than profits.bat
```

如果 profits.bat 和 earnings.bat 文件相同， **fc** 将显示以下消息：

```
Comparing files profits.bat and earnings.bat
FC: no differences encountered
```

若要将当前目录中的每个 .bat 文件与 *new.bat*文件进行比较，请键入：

```
fc *.bat new.bat
```

若要将驱动器 C 上的文件 *new.bat* 与驱动器 D 上的文件 *new.bat* 进行比较，请键入：

```
fc c:new.bat d:*.bat
```

若要将驱动器 C 上根目录中的每个批处理文件与驱动器 D 上根目录中的文件进行比较，请键入：

```
fc c:*.bat d:*.bat
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
