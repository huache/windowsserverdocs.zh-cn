---
title: bitsadmin getfilestransferred
description: Bitsadmin getfilestransferred 命令的参考文章，用于检索为指定作业传输的文件数。
ms.topic: reference
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e86e35d80e8e6b00d973b60e314f22068f7d115b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033585"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred

检索指定的作业传输的文件数。

## <a name="syntax"></a>语法

```
bitsadmin /getfilestransferred <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索在名为 *myDownloadJob*的作业中传输的文件数：

```
bitsadmin /getfilestransferred myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
