---
title: find
description: Find 命令的参考主题，该主题在文件中搜索文本字符串，并在文件中显示指定的文本字符串。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ca66b22-3b7c-4166-8503-eb75fc53ab46
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0273405ce5e5b4958a347cd1eaddee0a38897f0c
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83437002"
---
# <a name="find"></a>find

搜索文件中的文本字符串，并显示包含指定字符串的文本行。

## <a name="syntax"></a>语法

```
find [/v] [/c] [/n] [/i] [/off[line]] <string> [[<drive>:][<path>]<filename>[...]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /v | 显示所有不包含指定的行 `<string>` 。 |
| /c | 对包含指定的行进行计数 `<string>` ，并显示合计。 |
| /n | 每行的前面都有文件的行号。 |
| /i | 指定搜索不区分大小写。 |
| [/off [line]] | 不会跳过设置了脱机属性的文件。 |
| `<string>` | 必需。 指定要搜索的字符组（用引号引起来）。 |
| `[<drive>:][<path>]<filename>` | 指定要在其中搜索指定字符串的文件的位置和名称。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果不使用 **/i**，则此命令将搜索为*字符串*指定的确切内容。 例如，此命令将处理字符 `a` 并 `A` 不同。 但是，如果使用 **/i**，搜索将变为不区分大小写，并且会将和视为 `a` `A` 相同的字符。

- 如果要搜索的字符串包含引号，则必须对字符串中包含的每个引号使用双引号（例如，"" 此字符串包含引号 ""）。

- 如果省略文件名，则此命令将充当筛选器，采用标准输入源（通常是键盘、管道（|）或重定向文件）输入，然后显示包含*字符串*的任何行。

- 可以按任意顺序键入**find**命令的参数和命令行选项。

- 使用此命令时，不能在指定的文件名或扩展名中使用通配符（**&#42;** 和 **？**）。 若要在使用通配符指定的一组文件中搜索字符串，可以在**for**命令中使用此命令。

- 如果在同一命令行中使用 **/c**和 **/v** ，此命令将显示不包含指定字符串的行的计数。 如果在同一命令行中指定 **/c**和 **/n** ， **find**将忽略 **/n**。

- 此命令不能识别回车符。 使用此命令在包含回车符的文件中搜索文本时，必须将搜索字符串限制为可在回车符之间找到的文本（即，不太可能被回车符中断的字符串）。 例如，如果字词和文件之间发生回车符，则此命令不会报告字符串税文件的匹配项。

### <a name="examples"></a>示例

若要显示*pencil.ad*中包含字符串 " *sharpener*" 的所有行，请键入：

```
find pencil sharpener pencil.ad
```

若要查找文本，"科学家仅标记其书面内容。 这不是最终报表。 " 在*报告 .doc*文件中，键入：

```
find ""The scientists labeled their paper for discussion only. It is not a final report."" report.doc
```

若要搜索一组文件，你可以使用中的 "**查找** **" 命令**。 若要在当前目录中搜索扩展名为 .bat 且包含字符串提示符的文件，请键入：

```
for %f in (*.bat) do find PROMPT %f
```

若要在硬盘上搜索并显示包含字符串 CPU 的驱动器 C 上的文件名，请使用竖线（|）将**dir**命令的输出定向到**find**命令，如下所示：

```
dir c:\ /s /b | find CPU
```

因为**查找**搜索区分大小写，而**dir**产生大写输出，所以必须以大写字母键入字符串 CPU，或将 **/i**命令行选项与**find**一起使用。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [对于命令](for.md)