---
title: 掩码
description: Mask 命令的参考文章，该命令删除使用 import 命令导入的硬件卷影副本。
ms.topic: reference
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ee0e4207a7c5cf6ad81ece39e9134881ad3c0239
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633717"
---
# <a name="mask"></a>掩码

删除使用 **import** 命令导入的硬件卷影副本。

## <a name="syntax"></a>语法

```
mask <shadowsetID>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| shadowsetID | 删除属于指定卷影副本集 ID 的卷影副本。 |

#### <a name="remarks"></a>备注

- 您可以使用现有的别名或环境变量来代替 *ShadowSetID*。 使用 **add** 而不使用参数查看现有别名。

### <a name="examples"></a>示例

若要删除导入的卷影副本 *% Import_1%*，请键入：

```
mask %Import_1%
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)