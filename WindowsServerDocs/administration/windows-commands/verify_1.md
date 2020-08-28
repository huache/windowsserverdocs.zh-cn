---
title: 验证
description: 用于 "验证" 的参考文章，告诉 **cmd** 是否验证文件已正确写入磁盘。
ms.topic: reference
ms.assetid: dfe8bc91-d948-4e47-84ad-a79a60506ffa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b6d20cd114f523919dc3fadaf223ce9d93d0fdbd
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023021"
---
# <a name="verify"></a>验证



告诉 **cmd** 是否验证文件是否已正确写入磁盘。 如果不使用参数，则 **验证** 将显示当前设置。



## <a name="syntax"></a>语法

```
verify [on | off]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[ \| 关闭时]|打开或关闭 **验证** 设置。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要显示当前 **验证** 设置，请键入：
```
verify
```
若要启用 **验证** 设置，请键入：
```
Verify on
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)