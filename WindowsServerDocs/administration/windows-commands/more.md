---
title: 更多
description: 更多命令的参考文章，其中每次显示一个输出屏幕。
ms.topic: reference
ms.assetid: ded14f6a-d82f-4aeb-a2d8-7ec1c94dfb8f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/26/2019
ms.openlocfilehash: 18e40ff1f3281967e05b47e41f3de405d7009691
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640155"
---
# <a name="more"></a>更多

一次显示输出的一个屏幕。

> [!NOTE]
> 还可从恢复控制台获取 **更多** 具有不同参数的命令。

## <a name="syntax"></a>语法

```
<command> | more [/c] [/p] [/s] [/t<n>] [+<n>]
more [[/c] [/p] [/s] [/t<n>] [+<n>]] < [<drive>:][<path>]<filename>
more [/c] [/p] [/s] [/t<n>] [+<n>] [<files>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<command>` | 指定要显示其输出的命令。 |
| /c | 在显示页面之前清除屏幕。 |
| /p | 展开换页符。 |
| /s | 以单个空行的形式显示多个空行。 |
| /t`<n>` | 将选项卡显示为 *n*指定的空格数。 |
| +`<n>` | 显示从 *n*指定的行开始的第一个文件。 |
| `[<drive>:][<path>]<filename>` | 指定要显示的文件的位置和名称。 |
| `<files>` | 指定要显示的文件的列表。 必须使用空格分隔文件。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 在) 的 **更多** 提示 (接受以下子命令 `-- More --` ，其中包括：

    | 密钥 | 操作 |
    | --- | ------ |
    | 空格键 | 按 **空格键** 显示下一屏幕。 |
    | Enter | 按 **enter** 键，一次显示一行文件。 |
    | F | 按 **F** 显示命令行上列出的下一个文件。 |
    | q | 按 **Q** 退出 **更多** 命令。 |
    | = | 显示行号。 |
    | h-p `<n>` | 按 **P** *显示下一行* 。 |
    | 些 `<n>` | 按 **S** 跳过接下来的 *n* 行。 |
    | ? | 按 **？** 显示在 " **更多** " 提示符下可用的命令。|

- 如果 () 使用重定向字符 `<` ，还必须指定一个文件名作为源。

- 如果使用管道 (`|`) ，则可以使用类似于 **dir**、 **sort**和 **type**的命令。

### <a name="examples"></a>示例

若要查看名为 " *客户端*" 的文件的第一个屏幕，请键入以下命令之一：

```
more < clients.new
type clients.new | more
```

" **更多** " 命令显示客户端中的第一个屏幕信息，你可以按空格键查看下一个屏幕信息。

若要清除屏幕并在显示文件 *客户端*之前删除所有额外的空白行，请键入以下命令之一：

```
more /c /s < clients.new
type clients.new | more /c /s
```

若要在 " **更多** " 提示符下显示当前行号，请键入：

```
more =
```

将当前行号添加到 **更多** 的提示符中，如 `-- More [Line: 24] --`

若要在 **更多** 提示符下显示特定数量的行，请键入：

```
more p
```

**更多**提示会要求你提供要显示的行数，如下所示： `-- More -- Lines:` 。 键入要显示的行数，然后按 ENTER。 屏幕将更改为仅显示该数目的行。

若要在 **更多** 提示时跳过特定数量的行，请键入：

```
more s
```

**更多**提示会要求您输入要跳过的行数，如下所示： `-- More -- Lines:` 。 键入要跳过的行数，然后按 ENTER。 屏幕将发生变化，以显示跳过这些行。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Windows 恢复环境 (WinRE) ](/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
