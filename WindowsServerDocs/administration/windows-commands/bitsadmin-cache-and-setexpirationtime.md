---
title: bitsadmin 缓存和 setexpirationtime
description: 用于设置缓存过期时间的**bitsadmin cache 和 setexpirationtime**的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf283a0a8b94fd55c591609e3dcd1d127a2be81a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850880"
---
>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

# <a name="bitsadmin-cache-and-setexpirationtime"></a>bitsadmin 缓存和 setexpirationtime

设置缓存过期时间。

## <a name="syntax"></a>语法

```
bitsadmin /cache /setexpirationtime secs
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| secs | 缓存过期前等待的秒数。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例在60秒内将缓存过期。

```
C:\>bitsadmin /cache / setexpirationtime 60
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
