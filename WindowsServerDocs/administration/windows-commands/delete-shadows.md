---
title: 删除阴影
description: 删除阴影的参考主题，用于删除卷影副本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1dd367d76ad1699321af9caf47a0ddc351088a05
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720801"
---
# <a name="delete-shadows"></a>删除阴影

删除卷影副本。

## <a name="syntax"></a>语法

```
delete shadows [all | volume <Volume> | oldest <Volume> | set <SetID> | id <ShadowID> | exposed {<Drive> | <MountPoint>}]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| ---- | ---- |
| all | 删除所有卷影副本。 |
| 卷\<卷> | 删除给定卷的所有卷影副本。 |
| 最\<早的卷> | 删除给定卷的最旧的卷影副本。 |
| 设置\<SetID> | 删除具有给定 ID 的卷影副本集中的卷影副本。 如果当前环境中存在别名，则**%** 可以使用符号指定别名。 |
| id \<ShadowID> | 删除给定 ID 的卷影副本。 如果当前环境中存在别名，则**%** 可以使用符号指定别名。 |
| 已公开\<{驱动器> | <MountPoint>} |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)