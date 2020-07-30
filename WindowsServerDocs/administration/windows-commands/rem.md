---
title: rem
description: 用于在脚本、批处理或 config.sys 文件中记录注释的 rem 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1a45b585-a83c-4ff6-badd-ff40f34cec23
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe0bfce3f9f72d0a32ef5b3bb540e5a297df24a1
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409698"
---
# <a name="rem"></a>rem

记录脚本、批处理或 config.sys 文件中的注释。 如果未指定任何注释，则**rem**将增加垂直间距。

## <a name="syntax"></a>语法

```
rem [<comment>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<comment>` | 指定要包含为注释的字符串。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Rem**命令不在屏幕上显示注释。 若要在屏幕上显示注释，必须在文件中包括**echo on**命令。

- 不能 `<` 在批处理文件注释中使用重定向字符（或 `>` ）或竖线（ `|` ）。

- 尽管可以使用不带注释的**rem**来向批处理文件添加垂直间距，但也可以使用空行。 处理批处理程序时，将忽略空白行。

### <a name="examples"></a>示例

若要通过批处理文件注释来添加垂直间距，请键入：

```
@echo off
rem  This batch program formats and checks new disks.
rem  It is named Checknew.bat.
rem
rem echo Insert new disk in Drive B.
pause
format b: /v chkdsk b:
```

若要在 config.sys 文件中的**prompt**命令之前包含解释性注释，请键入：

```
rem Set prompt to indicate current directory
prompt $p$g
```

若要提供有关脚本功能的注释，请键入：

```
rem The commands in this script set up 3 drives.
rem The first drive is a primary partition and is
rem assigned the letter D. The second and third drives
rem are logical partitions, and are assigned letters
rem E and F.
create partition primary size=2048
assign d:
create partition extended
create partition logical size=2048
assign e:
create partition logical
assign f:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)