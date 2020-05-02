---
title: attrib
description: Attrib 命令的参考主题，其中显示、设置或删除分配给文件或目录的属性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5e763ca5-21a2-45d2-b26d-a9c44c99091a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c525fe1dc5b78032f20358492a1bfde4df909add
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719198"
---
# <a name="attrib"></a>attrib

显示、设置或删除分配给文件或目录的属性。 如果在没有参数的情况下使用，则**attrib**将显示当前目录中所有文件的属性。

## <a name="syntax"></a>语法

```
attrib [{+|-}r] [{+|-}a] [{+|-}s] [{+|-}h] [{+|-}i] [<drive>:][<path>][<filename>] [/s [/d] [/l]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `{+|-}r` | 设置（**+**）或清除（**-**）只读文件属性。 |
| `{+\|-}a` | 设置（**+**）或清除（**-**）存档文件属性。 此属性集用于标记自上次备份以来发生更改的文件。 请注意， **xcopy**命令使用存档属性。 |
| `{+\|-}s` | 设置（**+**）或清除（**-**）系统文件属性。 如果文件使用此属性集，则必须清除该属性，然后才能更改文件的任何其他属性。 |
| `{+\|-}h` | 设置（**+**）或清除（**-**）隐藏文件属性。 如果文件使用此属性集，则必须清除该属性，然后才能更改文件的任何其他属性。 |
| `{+\|-}i` | 设置（**+**）或清除（**-**） "非内容索引文件" 属性。 |
| `[<drive>:][<path>][<filename>]` | 指定要显示或更改属性的目录、文件或文件组的位置和名称。<p>您可以使用 **？** 和 **&#42;** *filename*参数中的通配符，以显示或更改一组文件的属性。 |
| /s | 将**attrib**和任何命令行选项应用于当前目录及其所有子目录中的匹配文件。 |
| /d | 将**attrib**和任何命令行选项应用于目录。 |
| /l | 将**attrib**和任何命令行选项应用于符号链接，而不是符号链接的目标。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要显示位于当前目录中名为 News86 的文件的属性，请键入：

```
attrib news86
```

若要将只读属性分配给名为 test.txt 的文件，请键入：

```
attrib +r report.txt
```

若要从位于驱动器 b：中的磁盘上的公共目录及其子目录中删除只读属性，请键入：

```
attrib -r b:\public\*.* /s
```

若要为驱动器 a 上的所有文件设置 Archive 属性，然后清除扩展名为 .bak 的文件的 Archive 属性，请键入：

```
attrib +a a:*.* & attrib -a a:*.bak
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [xcopy 命令](xcopy.md)
