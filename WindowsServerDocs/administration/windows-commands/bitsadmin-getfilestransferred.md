---
title: bitsadmin getfilestransferred
description: Bitsadmin getfilestransferred 命令的参考主题，它检索为指定作业传输的文件数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed11739029338ecce5fc4efbe1918873a7f37f62
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717916"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred

检索指定的作业传输的文件数。

## <a name="syntax"></a>语法

```
bitsadmin /getfilestransferred <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索在名为*myDownloadJob*的作业中传输的文件数：

```
bitsadmin /getfilestransferred myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
