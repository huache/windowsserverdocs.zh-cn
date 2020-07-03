---
title: bitsadmin getfilestransferred
description: Bitsadmin getfilestransferred 命令的参考文章，用于检索为指定作业传输的文件数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 43257dcb8350974bfb258a9970c1a6fec787a226
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928250"
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

若要检索在名为*myDownloadJob*的作业中传输的文件数：

```
bitsadmin /getfilestransferred myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
