---
title: 删除阴影
description: 用于删除阴影的 Windows 命令主题，用于删除卷影副本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cd109f7ddc0365d03737eddba31a1a4b7f34915b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846560"
---
# <a name="delete-shadows"></a>删除阴影

删除卷影副本。

## <a name="syntax"></a>语法

```
delete shadows [all | volume <Volume> | oldest <Volume> | set <SetID> | id <ShadowID> | exposed {<Drive> | <MountPoint>}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---- | ---- |
| 全部 | 删除所有卷影副本。 |
| 卷 \<卷 > | 删除给定卷的所有卷影副本。 |
| 最早 \<卷 > | 删除给定卷的最旧的卷影副本。 |
| 设置 \<SetID > | 删除具有给定 ID 的卷影副本集中的卷影副本。 如果当前环境中存在别名，则可以使用 **%** 符号指定别名。 |
| id \<ShadowID > | 删除给定 ID 的卷影副本。 如果当前环境中存在别名，则可以使用 **%** 符号指定别名。 |
| 公开 {\<驱动器 > | <MountPoint>} |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)