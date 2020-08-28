---
title: bitsadmin cache 和 setlimit
description: 用于设置缓存大小限制的 bitsadmin cache 和 setlimit 命令的参考文章。
ms.topic: reference
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: edcd83ace72e301471b03ac0c1fc85439a1c4d94
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028785"
---
# <a name="bitsadmin-cache-and-setlimit"></a>bitsadmin cache 和 setlimit

设置缓存大小限制。

## <a name="syntax"></a>语法

```
bitsadmin /cache /setlimit percent
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| % | 缓存限制定义为总硬盘空间的百分比。 |

## <a name="examples"></a>示例

若要将缓存大小限制设置为50%：

```
bitsadmin /cache /setlimit 50
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 缓存命令](bitsadmin-cache.md)
