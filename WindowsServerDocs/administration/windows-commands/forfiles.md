---
title: forfiles
description: Forfiles 命令的参考文章，用于在一组文件或一组文件上选择并运行命令。
ms.topic: reference
ms.assetid: 43f6b004-446d-4fdd-91c5-5653613524a4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/20/2020
ms.openlocfilehash: c79aeddec4a2ea74eb79c7d807428b6bc5955ce2
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027625"
---
# <a name="forfiles"></a>forfiles

选择并运行一个文件或一组文件的命令。 此命令最常在批处理文件中使用。

## <a name="syntax"></a>语法

```
forfiles [/P pathname] [/M searchmask] [/S] [/C command] [/D [+ | -] [{<date> | <days>}]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /P `<pathname>` | 指定从其开始搜索的路径。 默认情况下，搜索从当前工作目录开始。 |
| 一样 `<searchmask>` | 根据指定的搜索掩码搜索文件。 默认的 searchmask 为 `*` 。 |
| /S | 指示 **forfiles** 命令以递归方式搜索子目录。 |
| /C `<command>` | 对每个文件运行指定的命令。 命令字符串应以双引号括起来。 默认命令为 `"cmd /c echo @file"` 。 |
| /D `[{+\|-}][{<date> | <days>}]` | 选择在指定时间范围内具有最后修改日期的文件：<ul><li>选择上次修改日期晚于或等于 (**+**) 或 (早于 **-**) 指定日期的文件，其中 *date* 的格式为 MM/DD/YYYY。</li><li>选择上次修改日期晚于或等于 (的文件 **+**) 当前日期加上指定的天数，或者早于或等于 (**-**) 当前日期减去指定的天数。</li><li>*天数*的有效值包括0–32768范围内的任何数字。 如果未指定任何符号， **+** 则默认情况下使用。</li></ul> |
| /? | 在 cmd 窗口中显示帮助文本。 |

#### <a name="remarks"></a>注解

- `forfiles /S`命令类似于 `dir /S` 。

- 可以在命令字符串中使用由 **/C** 命令行选项指定的以下变量：

    | 变量 | 说明 |
    | -------- | ----------- |
    | @FILE | 文件名。 |
    | @FNAME | 不带扩展名的文件名。 |
    | @EXT | 文件扩展名。 |
    | @PATH | 文件的完整路径。 |
    | @RELPATH | 文件的相对路径。 |
    | @ISDIR | 如果文件类型为目录，则计算结果为 TRUE。 否则，此变量的计算结果为 FALSE。 |
    | @FSIZE | 文件大小（以字节为单位）。 |
    | @FDATE | 文件中上次修改的日期戳。 |
    | @FTIME | 文件中上次修改的时间戳。 |

- 使用 **forfiles** 命令可以在多个文件上运行命令或传递参数。 例如，你可以对具有 .txt 文件扩展名的树中的所有文件运行 **类型** 命令。 或者，你可以在驱动器 C 上 ( * .bat) 执行每个批处理文件，文件名 Myinput.txt 为第一个参数。

- 此命令可以：

    - 使用 **/d** 参数按绝对日期或相对日期选择文件。

    - 使用和等变量生成文件的存档树 @FSIZE @FDATE 。

    - 使用变量来区分目录中的文件 @ISDIR 。

    - 在命令行中包含特殊字符，采用 0x*HH* 格式 (例如，选项卡的 0x09) 。

- 此命令的工作方式是 `recurse subdirectories` 在设计为仅处理一个文件的工具上实施标志。

### <a name="examples"></a>示例

若要列出驱动器 C 上的所有批处理文件，请键入：

```
forfiles /P c:\ /S /M *.bat /C "cmd /c echo @file is a batch file"
```

若要列出驱动器 C 上的所有目录，请键入：

```
forfiles /P c:\ /S /M *.* /C "cmd /c if @isdir==TRUE echo @file is a directory"
```

若要列出当前目录中至少一年的所有文件，请键入：

```
forfiles /S /M *.* /D -365 /C "cmd /c echo @file is at least one year old."
```

若要为当前目录中早于2007年1月1日的每个文件显示 *该文本文件，* 请键入：

```
forfiles /S /M *.* /D -01/01/2007 /C "cmd /c echo @file is outdated."
```

若要以列格式列出当前目录中所有文件的文件扩展名，并在扩展之前添加选项卡，请键入：

```
forfiles /S /M *.* /C "cmd /c echo The extension of @file is 0x09@ext"
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
