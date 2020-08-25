---
title: assoc
description: 关联命令的参考文章，其中显示或修改文件扩展名关联。
ms.topic: article
ms.assetid: 237bedda-b24c-4fec-a39c-9b7eacf96417
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 682375733bdd269150cb6d557db730283ee3267e
ms.sourcegitcommit: a868f7d8bb9c5becffc688fd9b75c80802af71ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778598"
---
# <a name="assoc"></a>assoc

显示或修改文件扩展名关联。 如果在没有参数的情况下使用， **assoc** 将显示所有当前文件扩展名关联的列表。

> [!NOTE]
> 此命令仅在 cmd.exe 中受支持，并且在 PowerShell 中不可用。
> 尽管可以使用 `cmd /c assoc` 作为解决方法。

## <a name="syntax"></a>语法

```
assoc [<.ext>[=[<filetype>]]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<.ext>` | 指定文件扩展名。 |
| `<filetype>` | 指定与指定的文件扩展名关联的文件类型。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="remarks"></a>注解

- 若要删除文件扩展名的文件类型关联，请按空格键，在等号后面添加一个空格。

- 若要查看已定义打开的命令字符串的当前文件类型，请使用 **ftype** 命令。

- 若要将 **assoc** 的输出重定向到文本文件，请使用 `>` 重定向运算符。

## <a name="examples"></a>示例

若要查看文件扩展名为 .txt 的当前文件类型关联，请键入：

```
assoc .txt
```

若要删除文件扩展名 .bak 的文件类型关联，请键入：

```
assoc .bak=
```

> [!NOTE]
> 请确保在等号后面添加一个空格。

若要查看每次 **显示一个屏幕的输出** ，请键入：

```
assoc | more
```

若要将 **assoc** 的输出发送到 assoc.txt 的文件，请键入：

```
assoc>assoc.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftype 命令](ftype.md)
