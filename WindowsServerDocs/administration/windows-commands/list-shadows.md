---
title: list shadows
description: 列出隐藏命令的参考文章，其中列出了系统上持久的和现有的非持久卷影副本。
ms.topic: article
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d06c529740d7137fb1bdc4cb8d7661eb3f69ffb7
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887577"
---
# <a name="list-shadows"></a>list shadows

列出系统上持久的和现有的非持久卷影副本。

## <a name="syntax"></a>语法

```
list shadows {all | set <setID> | id <shadowID>}
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| ---------- | ---------- |
| all | 列出所有卷影副本。 |
| 字符集`<setID>` | 列出属于指定卷影副本集 ID 的卷影副本。 |
| 识别`<shadowID>` | 列出具有指定卷影副本 ID 的所有卷影副本。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)