---
title: 回到
description: "\"还原\" 命令的参考文章，它将卷恢复到指定的卷影副本。"
ms.topic: reference
ms.assetid: 75ad40e4-502a-401e-b11e-8b31e00424b5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3c909cec1e503552f68cad55489529585a5eaf51
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640628"
---
# <a name="revert"></a>回到

将卷恢复到指定的卷影副本。 仅在 CLIENTACCESSIBLE 上下文中对卷影副本支持此项。 这些卷影副本是持久的，只能由系统提供程序进行。 如果不使用参数，则 **revert** 会在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
revert <shadowcopyID>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<shadowcopyID>` | 指定卷的卷影副本 ID。 如果不使用此参数，则命令会在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
