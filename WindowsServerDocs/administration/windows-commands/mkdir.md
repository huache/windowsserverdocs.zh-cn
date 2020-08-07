---
title: mkdir
description: 用于创建目录或子目录的 mkdir 命令的参考文章。
ms.topic: article
ms.assetid: 033a57a2-5deb-4c98-aa78-61ce8df2a330
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: afff7a7985c5934a8566162da7307ad8676a50f9
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87886453"
---
# <a name="mkdir"></a>mkdir

创建目录或子目录。 默认情况下启用的命令扩展允许你使用单个**mkdir**命令在指定路径中创建中间目录。

> [!NOTE]
> 此命令与[md 命令](md.md)相同。

## <a name="syntax"></a>语法

```
mkdir [<drive>:]<path>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<drive>`: | 指定要在其上创建新目录的驱动器。 |
| `<path>` | 指定新目录的名称和位置。 任何单个路径的最大长度由文件系统确定。 这是必需参数。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要在当前目录中创建名为*Directory1*的目录，请键入：

```
mkdir Directory1
```

若要在启用了命令扩展的情况下在根目录中创建目录树*Taxes\Property\Current* ，请键入：

```
mkdir \Taxes\Property\Current
```

如前面的示例所示，若要在根目录中创建目录树*Taxes\Property\Current* ，但禁用了命令扩展，请键入以下命令序列：

```
mkdir \Taxes
mkdir \Taxes\Property
mkdir \Taxes\Property\Current
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [md 命令](md.md)