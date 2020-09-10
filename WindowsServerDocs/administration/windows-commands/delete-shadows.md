---
title: delete shadows
description: 删除阴影命令的参考文章，用于删除卷影副本。
ms.topic: reference
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f8fe95ac21c36f4605a544c97036c0a02bddaf42
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628854"
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
| 全部 | 删除所有卷影副本。 |
| 量 `<volume>` | 删除给定卷的所有卷影副本。 |
| 古老 `<volume>` | 删除给定卷的最旧的卷影副本。 |
| 字符集 `<setID>` | 删除具有给定 ID 的卷影副本集中的卷影副本。 **%** 如果当前环境中存在别名，则可以使用符号指定别名。 |
| 识别 `<shadowID>` | 删除给定 ID 的卷影副本。 **%** 如果当前环境中存在别名，则可以使用符号指定别名。 |
| 公开 {<drive> | <mountpoint>} |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [删除命令](delete.md)
