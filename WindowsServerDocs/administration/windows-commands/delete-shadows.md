---
title: delete shadows
description: 删除阴影命令的参考文章，用于删除卷影副本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6d541b50a78d738034204d14441352fff6c5d9fc
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929508"
---
# <a name="delete-shadows"></a>delete shadows

删除卷影副本。

## <a name="syntax"></a>语法

```
delete shadows [all | volume <volume> | oldest <volume> | set <setID> | id <shadowID> | exposed {<drive> | <mountpoint>}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---- | ---- |
| all | 删除所有卷影副本。 |
| 量`<volume>` | 删除给定卷的所有卷影副本。 |
| 古老`<volume>` | 删除给定卷的最旧的卷影副本。 |
| 字符集`<setID>` | 删除具有给定 ID 的卷影副本集中的卷影副本。 **%** 如果当前环境中存在别名，则可以使用符号指定别名。 |
| 识别`<shadowID>` | 删除给定 ID 的卷影副本。 **%** 如果当前环境中存在别名，则可以使用符号指定别名。 |
| 公开 {<drive> | <mountpoint>} |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [删除命令](delete.md)
