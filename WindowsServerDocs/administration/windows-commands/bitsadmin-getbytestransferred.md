---
title: bitsadmin getbytestransferred
description: Bitsadmin getbytestransferred 命令的参考文章，它检索为指定作业传输的字节数。
ms.topic: reference
ms.assetid: 47bbf184-e06f-4be0-b2ba-d32b10d82002
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c67185ff147611436dcb75803e2282542f376019
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632299"
---
# <a name="bitsadmin-getbytestransferred"></a>bitsadmin getbytestransferred

检索为指定作业传输的字节数。

## <a name="syntax"></a>语法

```
bitsadmin /getbytestransferred <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索为名为 *myDownloadJob*的作业传输的字节数，请执行以下操作：

```
bitsadmin /getbytestransferred myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
