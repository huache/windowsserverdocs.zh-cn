---
title: bitsadmin getstate
description: Bitsadmin getstate 命令的参考文章，可检索指定作业的状态。
ms.topic: reference
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2faf05bd245f0b59eb9f10d0d46d96e8e1d3e11c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631657"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate

检索指定作业的状态。

## <a name="syntax"></a>语法

```
bitsadmin /getstate <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>输出

返回的输出值可以是：

| 状态 | 说明 |
| --------------- | ----------- |
| 已排队 | 作业正在等待运行。 |
| Connecting | BITS 正在联系服务器。 |
| 转移 | BITS 正在传输数据。 |
| 此前 | BITS 已成功传输作业中的所有文件。 |
| 已挂起 | 作业已暂停。 |
| 错误 | 发生了不可恢复的错误;将不会重试传输。 |
| Transient_Error | 发生了可恢复的错误;当最小重试延迟到期时，将重试传输。 |
| 已确认 | 作业已完成。 |
| 已取消 | 已取消作业。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的状态：

```
bitsadmin /getstate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
