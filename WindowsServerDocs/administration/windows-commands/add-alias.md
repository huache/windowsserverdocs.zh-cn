---
title: add alias
description: 添加别名命令的参考文章，它将别名添加到别名环境。
ms.topic: reference
ms.assetid: 5fe12f5d-11e9-4f3d-b7f9-40b26c8685e5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1cc9b7c5395c29ac917a0b25b97fb091dc66a699
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633552"
---
# <a name="add-alias"></a>add alias

向别名环境添加别名。 如果在没有参数的情况下使用，则 " **添加别名** " 会在命令提示符下显示帮助。 别名保存在元数据文件中，并将通过 **加载元数据** 命令加载。

## <a name="syntax"></a>语法

```
add alias <aliasname> <aliasvalue>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<aliasname>` | 指定别名的名称。 |
| `<aliasvalue>` | 指定别名的值。 |
| `? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要列出所有阴影（包括其别名），请键入：

```
list shadows all
```

以下摘录显示了已为其分配默认别名 *VSS_SHADOW_x*的卷影副本：

```
* Shadow Copy ID = {ff47165a-1946-4a0c-b7f4-80f46a309278}
%VSS_SHADOW_1%
```

若要将名为 *System1* 的新别名分配到此卷影副本，请键入：

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
