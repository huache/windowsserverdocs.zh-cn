---
title: bitsadmin cache 和 delete
description: 用于删除特定缓存条目的 bitsadmin cache 和 delete 命令的参考文章。
ms.topic: reference
ms.assetid: 22540273-55a5-46ea-869b-6df2aa6808a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b7a7c00013833df121219f3e4f17e55a1d1e7d4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034895"
---
# <a name="bitsadmin-cache-and-delete"></a>bitsadmin cache 和 delete

删除特定的缓存条目。

## <a name="syntax"></a>语法

```
bitsadmin /cache /delete recordID
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| recordID | 与缓存项关联的 GUID。 |

## <a name="examples"></a>示例

若要删除 RecordID 为 {6511FB02-E195-40A2-B595-E8E2F8F47702} 的缓存条目：

```
bitsadmin /cache /delete {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 缓存命令](bitsadmin-cache.md)
