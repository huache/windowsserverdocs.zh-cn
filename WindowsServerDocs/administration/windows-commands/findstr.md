---
title: findstr
description: Findstr 命令的参考文章，可搜索文件中的文本模式。
ms.topic: reference
ms.assetid: c2d803fb-4cd2-46a1-a1b7-6f5e0249c418
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bdd268c3b2ddde1b42527968252770e6903bacc4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035125"
---
# <a name="findstr"></a>findstr

搜索文件中的文本模式。

## <a name="syntax"></a>语法

```
findstr [/b] [/e] [/l | /r] [/s] [/i] [/x] [/v] [/n] [/m] [/o] [/p] [/f:<file>] [/c:<string>] [/g:<file>] [/d:<dirlist>] [/a:<colorattribute>] [/off[line]] <strings> [<drive>:][<path>]<filename>[ ...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /b | 如果文本模式位于行的开头，则匹配它。 |
| /e | 如果文本模式位于行尾，则匹配它。 |
| /l | 按字面处理搜索字符串。 |
| /r | 将搜索字符串处理为正则表达式。 这是默认设置。 |
| /s | 搜索当前目录和所有子目录。 |
| /i | 搜索字符串时忽略字符的大小写。 |
| /x | 打印完全匹配的行。 |
| /v | 仅打印不包含匹配项的行。 |
| /n | 打印每个匹配行的行号。 |
| /m | 如果文件包含匹配项，则仅打印文件名。 |
| /o | 打印每个匹配行前的字符偏移量。 |
| /p | 跳过包含不可打印字符的文件。 |
| /off [line] | 不会跳过设置了脱机属性的文件。 |
| /f`<file>` | 从指定的文件中获取文件列表。 |
| /c`<string>` | 使用指定的文本作为文本搜索字符串。 |
| /g`<file>` | 从指定的文件中获取搜索字符串。 |
| /d`<dirlist>` | 搜索指定的目录列表。 每个目录必须用分号分隔 (; 例如 ) `dir1;dir2;dir3` 。 |
| /a`<colorattribute>` | 指定带有两个十六进制数字的颜色属性。 `color /?`有关其他信息，请键入。 |
| `<strings>` | 指定要在 *filename*中搜索的文本。 必需。 |
| `[\<drive>:][<path>]<filename>[ ...]` | 指定要搜索的位置和文件。 至少需要一个文件名。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 所有 **findstr** 命令行选项都必须在命令字符串中的 *字符串* 和 *文件名* 之前。

- 正则表达式使用文本字符和元字符来查找文本模式，而不是精确字符串。

  - 文本字符是在正则表达式语法中没有特殊含义的字符;而是匹配该字符的匹配项。 例如，字母和数字是原义字符。

  - 元字符是在正则表达式语法中具有特殊含义 (运算符或分隔符) 的符号。

    接受的元字符包括：

    | 元字符 | “值” |
    | -------------- | ----- |
    | `.` | **通配符** -任意字符 |
    | `*` | **重复执行** 零次或多次出现的上一个字符或类。 |
    | `^` | **起始行位置** -行的开头。 |
    | `$` | **结束行位置** -行的末尾。 |
    | `[class]` | **字符类** -集合中的任何一个字符。 |
    | `[^class]` | **反向类** -任何一个不在集内的字符。 |
    | `[x-y]` | **范围** -指定范围内的任何字符。 |
    | `\x` | 元字符的**转义**文本使用。 |
    | `<string` | **开始单词位置** -单词的开头。 |
    | `string>` | **结束单词位置** -单词的结尾。 |

    正则表达式语法中的特殊字符在一起使用时，其功能最高。 例如，使用通配符 () 的组合 `.` ，并重复 (`*`) 字符以匹配任意字符串： `.*`

    使用以下表达式作为更大的表达式的一部分，以匹配以 *b* 开头并以 *ing*结尾的任何字符串： `b.*ing`

- 若要在一组文件中搜索多个字符串，必须在单独的行上创建一个包含每个搜索条件的文本文件。

- 使用空格分隔多个搜索字符串，除非参数使用 **/c**作为前缀。

### <a name="examples"></a>示例

若要在文件*a.x*中搜索 " *hello* *" 或 ""，* 请键入：

```
findstr hello there x.y
```

若要在文件*x.x.x.x*中搜索*hello* ，请键入：

```
findstr /c:hello there x.y
```

若要使用文件*proposal.txt*中) 的初始大写字母 W*查找 word (* 的所有匹配项，请键入：

```
findstr Windows proposal.txt
```

若要搜索当前目录中的每个文件以及包含 word *Windows*的所有子目录，无论字母大小写如何，请键入：

```
findstr /s /i Windows *.*
```

若要 *查找以开头并以* 零个或多个空格开头的行的所有匹配项 (如) 的计算机程序循环，并显示找到每个匹配项的行号，请键入：

```
findstr /b /n /r /c:^ *FOR *.bas
```

若要列出要在文本文件中搜索的确切文件，请使用 *stringlist.txt*文件中的搜索条件，搜索 *filelist.txt*中列出的文件，然后在文件结果中存储结果 *。 out*，请键入：

```
findstr /g:stringlist.txt /f:filelist.txt > results.out
```

若要列出当前目录和所有子目录中包含 word *计算机* 的每个文件，请键入：

```
findstr /s /i /m <computer> *.*
```

若要列出每个包含 word 计算机的文件以及以 comp 开头的任何其他单词， (如) 的补充和竞争，请键入：

```
findstr /s /i /m <comp.* *.*
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)