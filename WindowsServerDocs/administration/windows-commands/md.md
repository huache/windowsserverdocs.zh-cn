---
title: md
description: 用于创建目录或子目录的 md 命令的参考文章。
ms.topic: reference
ms.assetid: 82162d00-cc34-4776-9e55-4b4836dbd6a9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f3da07c6e9d2e6fd7499f74e8ef10fdf3ba85586
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037845"
---
# <a name="md"></a>md

创建目录或子目录。 默认情况下启用的命令扩展允许你使用单个 **md** 命令在指定路径中创建中间目录。

> [!NOTE]
> 此命令与 [mkdir 命令](mkdir.md)相同。

## <a name="syntax"></a>语法

```
md [<drive>:]<path>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>`: | 指定要在其上创建新目录的驱动器。 |
| `<path>` | 指定新目录的名称和位置。 任何单个路径的最大长度由文件系统确定。 这是必需参数。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要在当前目录中创建名为 *Directory1* 的目录，请键入：

```
md Directory1
```

若要在启用了命令扩展的情况下在根目录中创建目录树 *Taxes\Property\Current* ，请键入：

```
md \Taxes\Property\Current
```

如前面的示例所示，若要在根目录中创建目录树 *Taxes\Property\Current* ，但禁用了命令扩展，请键入以下命令序列：

```
md \Taxes
md \Taxes\Property
md \Taxes\Property\Current
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [mkdir 命令](mkdir.md)