---
title: replace
description: Replace 命令的参考文章，可将现有文件替换为目录或将新文件添加到目录。
ms.topic: reference
ms.assetid: 6143661e-d90f-4812-b265-6669b567dd1f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 5dfab76427a8f91339c29ac37607ce422d4f7e39
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037015"
---
# <a name="replace"></a>replace

替换目录中的现有文件。 如果与 **/a** 选项一起使用，则此命令会将新文件添加到目录，而不是替换现有文件。

## <a name="syntax"></a>语法

```
replace [<drive1>:][<path1>]<filename> [<drive2>:][<path2>] [/a] [/p] [/r] [/w]
replace [<drive1>:][<path1>]<filename> [<drive2>:][<path2>] [/p] [/r] [/s] [/w] [/u]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `[<drive1>:][<path1>]<filename>` | 指定源文件或文件集的位置和名称。 *Filename*选项是必需的，并且可以包括 (**&#42;** 和 **？**) 的通配符。 |
| `[<drive2>:][<path2>]` | 指定目标文件的位置。 不能为替换的文件指定文件名。 如果未指定驱动器或路径，此命令将使用当前驱动器和目录作为目标。 |
| /a | 将新文件添加到目标目录，而不是替换现有文件。 不能将此命令行选项与 **/s** 或 **/u** 命令行选项一起使用。 |
| /p | 在替换目标文件或添加源文件之前，提示你进行确认。 |
| /r | 替换只读和未受保护的文件。 如果尝试替换只读文件，但未指定 **/r**，则会产生错误并停止替换操作。 |
| /W | 在搜索源文件开始之前，请等待你插入磁盘。 如果未指定 **/w**，则按 enter 后，此命令会立即开始替换或添加文件。 |
| /s | 搜索目标目录中的所有子目录并替换匹配文件。 不能将 **/s** 与 **/a** 命令行选项一起使用。 此命令不搜索 *Path1*中指定的子目录。 |
| /U | 仅替换目标目录中比源目录中的文件旧的那些文件。 不能将 **/u** 与 **/a** 命令行选项一起使用。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 当此命令添加或替换文件时，文件名称会显示在屏幕上。 完成此命令后，将按以下格式之一显示摘要行：

  ```
  nnn files added
  nnn files replaced
  no file added
  no file replaced
  ```

- 如果你使用的是软盘，并且在运行此命令时需要切换磁盘，则可以指定 **/w** 命令行选项，以便此命令等待你切换磁盘。

- 不能使用此命令更新隐藏的文件或系统文件。

- 下表显示了每个退出代码及其含义的简短说明：

  | 退出代码 | 说明 |
  |--|--|
  | 0 | 此命令已成功替换或添加文件。 |
  | 1 | 此命令遇到了不正确的 MS-DOS 版本。 |
  | 2 | 此命令找不到源文件。 |
  | 3 | 此命令找不到源或目标路径。 |
  | 5 | 用户无权访问要替换的文件。 |
  | 8 | 系统内存不足，无法执行该命令。 |
  | 11 | 用户在命令行上使用了错误的语法。 |

> [!NOTE]
> 在批处理程序 **中，可以使用 ERRORLEVEL 命令行** 上的 "" 参数来处理此命令返回的退出代码。

## <a name="examples"></a>示例

若要更新在驱动器 C： ) 的多个目录中显示 *的名为* "phone" 的文件的所有版本，请在驱动器 a：的软盘中使用最新 *版本的 (* ，键入：

```
replace a:\phones.cli c:\ /s
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
