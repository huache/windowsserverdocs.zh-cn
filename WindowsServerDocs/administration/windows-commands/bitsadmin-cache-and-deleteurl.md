---
title: bitsadmin 缓存和 deleteURL
description: Bitsadmin cache 和 deleteURL 命令的参考文章，用于删除给定 URL 的所有缓存条目。
ms.topic: reference
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6e1c3af4cfbb6c1ef21a86ead6d3975bf1f44cf6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632621"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>bitsadmin 缓存和 deleteURL

删除给定 URL 的所有缓存条目。

## <a name="syntax"></a>语法

```
bitsadmin /deleteURL URL
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| URL | 标识远程文件的统一资源定位器。 |

## <a name="examples"></a>示例

删除的所有缓存条目 `https://www.contoso.com/en/us/default.aspx` ：

```
bitsadmin /deleteURL https://www.contoso.com/en/us/default.aspx
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 缓存命令](bitsadmin-cache.md)
