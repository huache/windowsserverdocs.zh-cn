---
title: bitsadmin cache 和 setlimit
description: Bitsadmin cache 和 setlimit 命令的参考主题，用于设置缓存大小限制。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a4c41102bfb87ff6d48113c4e85a821b821b5b01
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718290"
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
