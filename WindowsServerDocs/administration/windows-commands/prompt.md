---
title: prompt
description: Prompt 命令的参考文章，可自定义 Cmd.exe 命令提示符。
ms.topic: reference
ms.assetid: 3d98e965-02eb-46ad-9d0a-5dc44830373e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 8cf91a2a2e78191f035545bc897eceae4c897457
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640328"
---
# <a name="prompt"></a>prompt

更改 Cmd.exe 命令提示符，包括显示你需要的任何文本，如当前目录的名称、时间和日期或 Microsoft Windows 版本号。 如果在没有参数的情况下使用，则此命令会将命令提示符重置为默认设置，该设置是当前驱动器号和目录，后跟大于符号 (**>**) 。

## <a name="syntax"></a>语法

```
prompt [<text>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<text>` | 指定要包括在命令提示符中的文本和信息。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 可以包含的字符组合（而不是） *文本* 参数中有一个或多个字符串：

    | 字符 | 说明 |
    |--|--|
    | $q | = (等号)  |
    | $$ | $ (美元符号)  |
    | $t | 当前时间 |
    | $d | 当前日期 |
    | $p | 当前驱动器和路径 |
    | $v | Windows 版本号 |
    | $n | 当前驱动器 |
    | $g | > (大于符号)  |
    | $l | < (小于号)  |
    | $b | `|` (管道符号)  |
    | $_ | 回车-换行符 |
    | $e | ANSI 转义码 (代码 27)  |
    | $h | Backspace (删除已写入命令行的字符)  |
    | $a | & (与号)  |
    | $c |  ( (左括号)  |
    | $f | )  (右括号)  |
    | $s | Space |

- 当启用命令扩展时， **prompt** 命令支持以下格式字符：

    | 字符 | 说明 |
    |--|--|
    | $+ | 零个或多个加符号 (**+**) 个字符，具体取决于 **pushd** 目录堆栈的深度 (推送) 的每个级别一个字符。 |
    | $m | 与当前驱动器号关联的远程名称; 如果当前驱动器不是网络驱动器，则为空字符串。 |

- 如果在 text 参数中包含 **$p** 字符，则在输入每个命令 (来确定当前驱动器和路径) 后，会读取磁盘。 这可能需要额外的时间，特别是对于软盘驱动器。

### <a name="examples"></a>示例

若要设置带有当前时间和日期的两行命令提示符，并在第一行上设置大于号，请键入：

```
prompt $d$s$s$t$_$g
```

系统会按如下所示更改提示，其中日期和时间是最新的：

```
Fri 06/01/2007  13:53:28.91
```

若要将命令提示符设置为 () 的箭头显示 `-->` ，请键入：

```
prompt --$g
```

若要手动将命令提示符更改为默认设置 (当前驱动器和路径后跟大于号) ，请键入：

```
prompt $p$g
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
