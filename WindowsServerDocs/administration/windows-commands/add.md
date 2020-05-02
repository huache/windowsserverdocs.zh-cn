---
title: add
description: 添加命令的参考主题，它将卷添加到要进行卷影复制的卷集，或将别名添加到别名环境。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 47efce7a-86d2-4872-ae31-baa108757afd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b621a3061c4e3366085c5cc44f91f26dd33d4e3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719009"
---
# <a name="add"></a>add

将卷添加到要进行卷影复制的卷集中，或将别名添加到别名环境。 如果在不使用子命令的情况下使用，则**添加**列出当前卷和别名。

> [!NOTE]
> 在创建卷影副本之前，不会将别名添加到别名环境中。 应立即使用 "**添加别名**" 添加所需的别名。

## <a name="syntax"></a>语法

```
add
add volume <volume> [provider <providerid>]
add alias <aliasname> <aliasvalue>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| ---------- | ----------- |
| 卷 | 将卷添加到卷影副本集，这是要进行卷影复制的卷集。 有关语法和参数，请参阅[add volume](add-volume.md) 。 |
| alias | 向别名环境添加给定的名称和值。 请参阅为语法和参数[添加别名](add-alias.md)。 |
| /? | 在命令行中显示帮助。 |

## <a name="examples"></a>示例

若要显示添加的卷和当前在环境中的别名，请键入：

```
add
```

以下输出显示驱动器 C 已添加到卷影副本集：

```
Volume c: alias System1    GUID \\?\Volume{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}\
1 volume in Shadow Copy Set.
No Diskshadow aliases in the environment.
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)