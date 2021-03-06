---
title: add
description: 添加命令的参考文章，可将卷添加到要进行卷影复制的卷集中，或将别名添加到别名环境。
ms.topic: reference
ms.assetid: 47efce7a-86d2-4872-ae31-baa108757afd
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ddd090323b45caa0cc7afa4c07c568793f2e268d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633492"
---
# <a name="add"></a>add

将卷添加到要进行卷影复制的卷集中，或将别名添加到别名环境。 如果在不使用子命令的情况下使用，则 **添加** 列出当前卷和别名。

> [!NOTE]
> 在创建卷影副本之前，不会将别名添加到别名环境中。 应立即使用 " **添加别名**" 添加所需的别名。

## <a name="syntax"></a>语法

```
add
add volume <volume> [provider <providerid>]
add alias <aliasname> <aliasvalue>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| 卷 | 将卷添加到卷影副本集，这是要进行卷影复制的卷集。 有关语法和参数，请参阅 [add volume](add-volume.md) 。 |
| alias | 向别名环境添加给定的名称和值。 请参阅为语法和参数 [添加别名](add-alias.md) 。 |
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