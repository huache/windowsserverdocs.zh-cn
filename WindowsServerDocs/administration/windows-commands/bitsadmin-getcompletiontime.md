---
title: bitsadmin getcompletiontime
description: Bitsadmin getcompletiontime 命令的参考文章，用于检索作业传输数据完成的时间。
ms.topic: reference
ms.assetid: 7a4b3c1c-9832-4724-86b2-cce3c01bfa28
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 660a28dcfe99bd5801ba2fc3ad909cec78a671ce
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632244"
---
# <a name="bitsadmin-getcompletiontime"></a>bitsadmin getcompletiontime

检索作业传输数据完成的时间。

## <a name="syntax"></a>语法

```
bitsadmin /getcompletiontime <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

检索名为 *myDownloadJob* 的作业完成传输数据的时间：

```
bitsadmin /getcompletiontime myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
