---
title: bitsadmin cache 和 setlimit
description: 用于设置缓存大小限制的 bitsadmin cache 和 setlimit 命令的参考文章。
ms.topic: article
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 41a1331a19f66e7d84dc3eb57b04d42596a40628
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894705"
---
# <a name="bitsadmin-cache-and-setlimit"></a>bitsadmin cache 和 setlimit

设置缓存大小限制。

## <a name="syntax"></a>语法

```
bitsadmin /cache /setlimit percent
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
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
