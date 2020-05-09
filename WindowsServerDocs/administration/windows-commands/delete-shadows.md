---
title: 删除阴影
description: 删除阴影命令的参考主题，用于删除卷影副本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6b757314c96024741795c6770a98d10ac23b5bd0
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993114"
---
# <a name="delete-shadows"></a>删除阴影

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
| 字符集`<setID>` | 删除具有给定 ID 的卷影副本集中的卷影副本。 如果当前环境中存在别名，则**%** 可以使用符号指定别名。 |
| 识别`<shadowID>` | 删除给定 ID 的卷影副本。 如果当前环境中存在别名，则**%** 可以使用符号指定别名。 |
| 公开 {<drive> | <mountpoint>} |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [删除命令](delete.md)
