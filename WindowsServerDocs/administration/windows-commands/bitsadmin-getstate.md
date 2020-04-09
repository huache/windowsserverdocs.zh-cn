---
title: bitsadmin getstate
description: 用于**bitsadmin getstate**的 Windows 命令主题，它检索指定作业的状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 43cd8c8e614cce65f55b16fc5395b1d37de0cf95
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850460"
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
| 作业 | 作业的显示名称或 GUID。 |

## <a name="output"></a>Output

输出值包括：

| State | 说明 |
| --------------- | ----------- |
| 已排队 | 作业正在等待运行。 |
| 正在连接 | BITS 正在联系服务器。 |
| 转移 | BITS 正在传输数据。 |
| 此前 | BITS 已成功传输作业中的所有文件。 |
| Suspended | 作业已暂停。 |
| 错误 | 发生了不可恢复的错误;将不会重试传输。 |
| Transient_Error | 发生了可恢复的错误;当最小重试延迟到期时，将重试传输。 |
| 承认 | 作业已完成。 |
| Canceled | 已取消作业。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将检索名为*myDownloadJob*的作业的状态。

```
C:\>bitsadmin /getstate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
