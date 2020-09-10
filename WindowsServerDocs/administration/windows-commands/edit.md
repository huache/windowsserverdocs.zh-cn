---
title: 编辑
description: 用于启动 MS-DOS 编辑器的 "编辑" 命令的参考文章，以便你可以创建和更改 ASCII 文本文件。
ms.topic: reference
ms.assetid: 4e0ff2e8-3518-47c1-8c69-5e93f895fa0e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b3723c65456fd7e17395cd7a9bc931ddc56a09b3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636177"
---
# <a name="edit"></a>编辑

启动 MS-DOS 编辑器，该编辑器创建并更改 ASCII 文本文件。

## <a name="syntax"></a>语法

```
edit [/b] [/h] [/r] [/s] [/<nnn>] [[<drive>:][<path>]<filename> [<filename2> [...]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `[<drive>:][<path>]<filename> [<filename2> [...]]` | 指定一个或多个 ASCII 文本文件的位置和名称。 如果文件不存在，MS-DOS 编辑器会创建它。 如果该文件存在，MS-DOS 编辑器会将其打开，并在屏幕上显示其内容。 *Filename*选项可以包含 (**&#42;** 和 **？**) 的通配符字符。 用空格分隔多个文件名。 |
| /b | 强制单色模式，以便 MS-DOS 编辑器以黑白显示。 |
| /h | 显示当前监视器可能具有的最大行数。 |
| /r | 在只读模式下加载文件 () 。 |
| /s | 强制使用短文件名。 |
| `<nnn>` | 将二进制文件 () 加载到 *nnn* 个字符范围内。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 有关更多帮助，请打开 MS-DOS 编辑器，然后按 F1 键。

- 默认情况下，某些监视器不支持显示快捷键。 如果监视器未显示快捷键，请使用 **/b**。

### <a name="examples"></a>示例

若要打开 MS-DOS 编辑器，请键入：

```
edit
```

若要在当前目录中创建和编辑名为 *newtextfile.txt* 的文件，请键入：

```
edit newtextfile.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
