---
title: add alias
description: 添加别名命令的参考文章，它将别名添加到别名环境。
ms.topic: article
ms.assetid: 5fe12f5d-11e9-4f3d-b7f9-40b26c8685e5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cc2cddd53c99cc63fd53a5ab828a868e34632a97
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87895602"
---
# <a name="add-alias"></a>add alias

向别名环境添加别名。 如果在没有参数的情况下使用，则 "**添加别名**" 会在命令提示符下显示帮助。 别名保存在元数据文件中，并将通过**加载元数据**命令加载。

## <a name="syntax"></a>语法

```
add alias <aliasname> <aliasvalue>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<aliasname>` | 指定别名的名称。 |
| `<aliasvalue>` | 指定别名的值。 |
| `? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要列出所有阴影（包括其别名），请键入：

```
list shadows all
```

以下摘录显示了已为其分配默认别名*VSS_SHADOW_x*的卷影副本：

```
* Shadow Copy ID = {ff47165a-1946-4a0c-b7f4-80f46a309278}
%VSS_SHADOW_1%
```

若要将名为*System1*的新别名分配到此卷影副本，请键入：

```
add alias System1 %VSS_SHADOW_1%
```

或者，您可以使用卷影副本 ID 指定别名：

```
add alias System1 {ff47165a-1946-4a0c-b7f4-80f46a309278}
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [加载元数据命令](load-metadata.md)
