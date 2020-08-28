---
title: bitsadmin getbytestransferred
description: Bitsadmin getbytestransferred 命令的参考文章，它检索为指定作业传输的字节数。
ms.topic: reference
ms.assetid: 47bbf184-e06f-4be0-b2ba-d32b10d82002
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 67e1432f2fbef32ac47320d87993f5d62053bb71
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028735"
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
