---
title: 掩码
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 816bcd932091b33ed897add5a13603e3a1eea925
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724010"
---
# <a name="mask"></a>掩码



删除使用**import**命令导入的硬件卷影副本。



## <a name="syntax"></a>语法

```
mask <ShadowSetID>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|ShadowSetID|删除属于指定卷影副本集 ID 的卷影副本。|

## <a name="remarks"></a>备注

-   您可以使用现有的别名或环境变量来代替*ShadowSetID*。 使用**add**而不使用参数查看现有别名。

## <a name="examples"></a>示例

若要删除导入的卷影副本% Import_1%，请键入：
```
mask %Import_1%
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)