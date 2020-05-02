---
title: bitsadmin getstate
description: Bitsadmin getstate 命令的参考主题，它检索指定作业的状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ab014c96c6d5d62232243d704d41d33cfcfc50f0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717540"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate

检索指定作业的状态。

## <a name="syntax"></a>语法

```
bitsadmin /getstate <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>输出

返回的输出值可以是：

| 状态 | 描述 |
| --------------- | ----------- |
| 已排队 | 作业正在等待运行。 |
| Connecting | BITS 正在联系服务器。 |
| 转移 | BITS 正在传输数据。 |
| 此前 | BITS 已成功传输作业中的所有文件。 |
| Suspended | 作业已暂停。 |
| 错误 | 发生了不可恢复的错误;将不会重试传输。 |
| Transient_Error | 发生了可恢复的错误;当最小重试延迟到期时，将重试传输。 |
| 已确认 | 作业已完成。 |
| 已取消 | 已取消作业。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的状态：

```
bitsadmin /getstate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
