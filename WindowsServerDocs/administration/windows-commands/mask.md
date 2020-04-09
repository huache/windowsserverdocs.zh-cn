---
title: mask
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a1cb92caacb955449c1baaad411fdbe4cdf05b73
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839640"
---
# <a name="mask"></a>mask



删除使用**import**命令导入的硬件卷影副本。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
mask <ShadowSetID>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|ShadowSetID|删除属于指定卷影副本集 ID 的卷影副本。|

## <a name="remarks"></a>备注

-   您可以使用现有的别名或环境变量来代替*ShadowSetID*。 使用**add**而不使用参数查看现有别名。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要删除导入的卷影副本% Import_1%，请键入：
```
mask %Import_1%
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)