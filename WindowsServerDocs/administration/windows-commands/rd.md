---
title: rd
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 42e672f6-5bc2-4c16-af25-18e7ed2dd555
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cb169a44f9613b237af71321f9619d9ea93a6912
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722637"
---
# <a name="rd"></a>rd



删除目录。 此命令与**rmdir**命令相同。



## <a name="syntax"></a>语法

```
rd [<Drive>:]<Path> [/s [/q]]
rmdir [<Drive>:]<Path> [/s [/q]]
```

### <a name="parameters"></a>参数

|     参数     |                                                                 描述                                                                  |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| [\<驱动器>：]<Path> |                      指定要删除的目录的位置和名称。 *路径*是必需的。                       |
|        /s         |                     删除目录树（指定的目录及其所有子目录，包括所有文件）。                      |
|        /q         | 指定安静模式。 删除目录树时不提示进行确认。 （请注意， **/q**仅在指定 **/s**时才起作用。） |
|        /?         |                                                     在命令提示符下显示帮助。                                                     |

## <a name="remarks"></a>备注

-   不能删除包含文件（包括隐藏文件或系统文件）的目录。 如果尝试这样做，将显示以下消息：

    `The directory is not empty`

    使用**dir/a**命令列出所有文件（包括隐藏文件和系统文件）。 然后，使用带有 **-h**的**attrib**命令删除隐藏的文件属性，使用- **s**删除系统文件属性，或使用 **-h-s**删除隐藏文件和系统文件属性。 删除隐藏属性和文件属性后，可以删除这些文件。
-   如果插入反斜杠（\)在*路径*的开头，*路径*将从根目录开始，而不考虑当前目录）。
-   你无法使用**rd**删除当前目录。 如果尝试删除当前目录，将显示以下错误消息：

    `The process cannot access the file because it is being used by another process.`

    如果收到此错误消息，则必须更改为其他目录（而不是当前目录的子目录），然后使用**rd** （如有必要，请指定*路径*）。
-   可从恢复控制台获取带有不同参数的**rd**命令。

## <a name="examples"></a>示例

不能删除当前正在使用的目录。 必须更改为不在当前目录中的目录。 例如，要更改为父目录，请键入：
```
cd ..
```
现在，可以安全地删除所需的目录。

使用 **/s**选项来删除目录树。 例如，若要从当前目录中删除名为 Test 的目录及其所有子目录和文件，请键入：
```
rd /s test
```
若要在安静模式下运行前面的示例，请键入：
```
rd /s /q test
```

> [!CAUTION]
> 在安静模式下运行**rd/s**时，将删除整个目录树而不进行确认。 请确保在使用 **/q**命令行选项之前移动或备份重要文件。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)