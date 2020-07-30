---
title: ren
description: 用于重命名文件或目录的 ren 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 60398e12-a05d-4524-a73a-0a925943e21d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: c5f873de224ff335be097d97c7d8933a70af726d
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409668"
---
# <a name="ren"></a>ren

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

重命名文件或目录。

> [!NOTE]
> 此命令与 "[重命名" 命令](rename.md)相同。

## <a name="syntax"></a>语法

```
ren [<drive>:][<path>]<filename1> <filename2>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `[<drive>:][<path>]<filename1>` | 指定要重命名的文件或文件集的位置和名称。 *Filename1*可以包含通配符（**&#42;** 和 **？**）。 |
| `<filename2>` | 指定文件的新名称。 您可以使用通配符来指定多个文件的新名称。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 在重命名文件时，不能指定新的驱动器或路径。 还不能使用此命令在驱动器之间重命名文件，或将文件移动到不同的目录。

- *Filename2*中的通配符所表示的字符将与*filename1*中的相应字符相同。

- *Filename2*必须是唯一的文件名。 如果*filename2*与现有文件名匹配，将显示以下消息： `Duplicate file name or file not found` 。

### <a name="examples"></a>示例

若要将当前目录中的所有 .txt 文件扩展名更改为 .doc 扩展名，请键入：

```
ren *.txt *.doc
```

若要将目录的名称从*Chap10*更改为*Part10*，请键入：

```
ren chap10 part10
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [重命名命令](rename.md)
