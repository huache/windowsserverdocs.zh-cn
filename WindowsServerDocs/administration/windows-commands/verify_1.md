---
title: 验证
description: Verify 的参考主题，它告诉**cmd**是否验证文件已正确写入磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dfe8bc91-d948-4e47-84ad-a79a60506ffa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f7fc35b37d5e0a429e1ecc2ebefc117804a0c645
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720293"
---
# <a name="verify"></a>验证



告诉**cmd**是否验证文件是否已正确写入磁盘。 如果不使用参数，则**验证**将显示当前设置。



## <a name="syntax"></a>语法

```
verify [on | off]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|[关闭\|时]|打开或关闭**验证**设置。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要显示当前**验证**设置，请键入：
```
verify
```
若要启用**验证**设置，请键入：
```
Verify on
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)