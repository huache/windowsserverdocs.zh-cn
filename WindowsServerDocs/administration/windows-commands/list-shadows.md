---
title: list shadows
description: 列出隐藏命令的参考文章，其中列出了系统上持久的和现有的非持久卷影副本。
ms.topic: reference
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4781587fd7bb82525746184c3fee2f0f9258c510
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635278"
---
# <a name="list-shadows"></a>list shadows

列出系统上持久的和现有的非持久卷影副本。

## <a name="syntax"></a>语法

```
list shadows {all | set <setID> | id <shadowID>}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| 全部 | 列出所有卷影副本。 |
| 字符集 `<setID>` | 列出属于指定卷影副本集 ID 的卷影副本。 |
| 识别 `<shadowID>` | 列出具有指定卷影副本 ID 的所有卷影副本。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)