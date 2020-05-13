---
title: bitsadmin cache 和 setexpirationtime
description: 用于设置缓存过期时间的 bitsadmin cache 和 setexpirationtime 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eeb1dbd0439a1a39711e2a074ada4c772b9ca016
ms.sourcegitcommit: aed942d11f1a361fc1d17553a4cf190a864d1268
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83235039"
---
# <a name="bitsadmin-cache-and-setexpirationtime"></a>bitsadmin cache 和 setexpirationtime

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

设置缓存过期时间。

## <a name="syntax"></a>语法

```
bitsadmin /cache /setexpirationtime secs
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| secs | 缓存过期前等待的秒数。 |

## <a name="examples"></a>示例

若要将缓存设置为在60秒后过期：

```
bitsadmin /cache / setexpirationtime 60
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 缓存命令](bitsadmin-cache.md)
