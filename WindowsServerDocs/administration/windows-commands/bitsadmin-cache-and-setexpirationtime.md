---
title: bitsadmin cache 和 setexpirationtime
description: 用于设置缓存过期时间的 bitsadmin cache 和 setexpirationtime 命令的参考文章。
ms.topic: reference
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e07e862d8577c33daec24bbc93fe5859f13944db
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028805"
---
# <a name="bitsadmin-cache-and-setexpirationtime"></a>bitsadmin cache 和 setexpirationtime

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

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
