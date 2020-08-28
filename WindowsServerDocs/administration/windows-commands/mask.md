---
title: 掩码
description: Mask 命令的参考文章，该命令删除使用 import 命令导入的硬件卷影副本。
ms.topic: reference
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c5d8f86de3019e47da3aff56aa370972de3288fa
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037865"
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

#### <a name="remarks"></a>注解

- 您可以使用现有的别名或环境变量来代替 *ShadowSetID*。 使用 **add** 而不使用参数查看现有别名。

### <a name="examples"></a>示例

若要删除导入的卷影副本 *% Import_1%*，请键入：

```
mask %Import_1%
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)