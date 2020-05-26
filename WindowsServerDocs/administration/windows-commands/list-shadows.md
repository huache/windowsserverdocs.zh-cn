---
title: 列表阴影
description: List shadows 命令的参考主题，其中列出了系统上持久的和现有的非持久卷影副本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9e0261a25c7a70a0c8690d578cadc9e73ff9a62e
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817167"
---
# <a name="list-shadows"></a>列表阴影

列出系统上持久的和现有的非持久卷影副本。

## <a name="syntax"></a>语法

```
list shadows {all | set <setID> | id <shadowID>}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ---------- |
| all | 列出所有卷影副本。 |
| 字符集`<setID>` | 列出属于指定卷影副本集 ID 的卷影副本。 |
| 识别`<shadowID>` | 列出具有指定卷影副本 ID 的所有卷影副本。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)