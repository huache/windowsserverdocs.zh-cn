---
title: bitsadmin cache 和 info
description: 用于转储特定缓存条目的 bitsadmin cache 和 info 命令的参考文章。
ms.topic: reference
ms.assetid: 15975cbf-dba6-49ca-a725-d15ce1952de5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cce96d25b3968c1f975b6426ce8c25e7420f7bd3
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028885"
---
# <a name="bitsadmin-cache-and-info"></a>bitsadmin cache 和 info

转储特定的缓存项。

## <a name="syntax"></a>语法

```
bitsadmin /cache /info recordID [/verbose]
```

### <a name="parameters"></a>参数

| Paramreter | 说明 |
| -------------- | -------------- |
| recordID | 与缓存项关联的 GUID。 |

## <a name="examples"></a>示例

若要转储 recordID 值为 {6511FB02-E195-40A2-B595-E8E2F8F47702} 的缓存条目：

```
bitsadmin /cache /info {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 缓存命令](bitsadmin-cache.md)
