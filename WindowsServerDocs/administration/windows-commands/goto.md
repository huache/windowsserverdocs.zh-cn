---
title: goto
description: Goto 命令的参考文章，将 cmd.exe 定向到批处理程序中的标记行。
ms.topic: reference
ms.assetid: e0de1458-1f78-48ff-a746-c285a945a510
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 537026fc2b4faafa57b7a4f2842d79775759cdc9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634800"
---
# <a name="goto"></a>goto

将 cmd.exe 定向到批处理程序中带标签的行。 在批处理程序中，此命令将命令处理定向到由标签标识的行。 找到标签后，处理将从下一行开始的命令开始。

## <a name="syntax"></a>语法

```
goto <label>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<label>` | 指定一个文本字符串，该字符串用作批处理程序中的标签。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

-  如果 (默认的) 启用命令扩展，并使用目标标签为 **： EOF**的**goto**命令，则可以将控制转移到当前批处理脚本文件的末尾并退出批处理脚本文件而不定义标签。 将此命令与 **： EOF** 标签一起使用时，必须在标签之前插入一个冒号。 例如：`goto:EOF`。

- 可以在 *标签* 参数中使用空格，但不能包含其他分隔符 (例如，分号 (; ) 或等于符号 (=) # A5。

- 指定的 *标签* 值必须与批处理程序中的标签相匹配。 批处理程序内的标签必须以冒号 (： ) 开头。 如果行以冒号开头，则将其视为标签，并忽略该行上的所有命令。 如果批处理程序不包含在 *标签* 参数中指定的标签，则批处理程序将停止并显示以下消息： `Label not found` 。

- 可以将 **goto** 与其他命令结合使用来执行条件操作。 有关对条件运算使用 **goto** 的详细信息，请参阅 [if 命令](if.md)。

## <a name="examples"></a>示例

以下批处理程序将驱动器 A 中的磁盘格式化为系统磁盘。 如果操作成功， **goto** 命令会将处理定向到 **：结束** 标签：

```
echo off
format a: /s
if not errorlevel 1 goto end
echo An error occurred during formatting.
:end
echo End of batch program.
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [cmd 命令](cmd.md)

- [if 命令](if.md)