---
title: bitsadmin cache 和 setlimit
description: 用于设置缓存大小限制的 bitsadmin cache 和 setlimit 命令的参考文章。
ms.topic: reference
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7547a2a51104285b10af6b02c1962c89f75d51fa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632483"
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
