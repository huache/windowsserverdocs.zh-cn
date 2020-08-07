---
title: bitsadmin cache 和 info
description: 用于转储特定缓存条目的 bitsadmin cache 和 info 命令的参考文章。
ms.topic: article
ms.assetid: 15975cbf-dba6-49ca-a725-d15ce1952de5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 537c6173718d8c7deb421915b2ef9697472600a2
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894798"
---
# <a name="bitsadmin-cache-and-info"></a>bitsadmin cache 和 info

转储特定的缓存项。

## <a name="syntax"></a>语法

```
bitsadmin /cache /info recordID [/verbose]
```

### <a name="parameters"></a>参数

| Paramreter | 描述 |
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
