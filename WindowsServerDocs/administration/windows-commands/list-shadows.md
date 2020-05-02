---
title: 列表阴影
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d22fc3bbe644983eaf072a430e565a0d34d1c4dd
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724477"
---
# <a name="list-shadows"></a>列表阴影



列出系统上持久的和现有的非持久卷影副本。

## <a name="syntax"></a>语法

```
list shadows {all | set <SetID> | id <ShadowID>}
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|all|列出所有卷影副本。|
|设置\<SetID>|列出属于指定卷影副本集 ID 的卷影副本。|
|id \<ShadowID>|列出具有指定卷影副本 ID 的所有卷影副本。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)