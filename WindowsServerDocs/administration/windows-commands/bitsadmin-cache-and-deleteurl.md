---
title: bitsadmin 缓存和 deleteURL
description: Bitsadmin cache 和 deleteURL 命令的参考文章，用于删除给定 URL 的所有缓存条目。
ms.topic: reference
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed804580c4435b612b91875ef59cf6eb8ca4275b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026705"
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
