---
title: bitsadmin getstate
description: 适用于 bitsadmin getstate 的 Windows 命令主题
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2cff790c8787b1514e8523a4583184d6f6a59efc
ms.sourcegitcommit: 51e0b575ef43cd16b2dab2db31c1d416e66eebe8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2020
ms.locfileid: "76259102"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate


检索指定作业的状态。

## <a name="syntax"></a>语法

```
bitsadmin /GetState <Job>
```

## <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
|    作业    | 该作业的显示名称或 GUID |

## <a name="remarks"></a>备注

可能的状态包括：

|      State      | 描述 |
| --------------- | ----------- |
| 好          | 作业正在等待运行。 |
| 连接      | BITS 正在联系服务器。 |
| 转    | BITS 正在传输数据。 |
| 此前     | BITS 已成功传输作业中的所有文件。 |
| SUSPENDED       | 作业已暂停。 |
| 错误           | 发生了不可恢复的错误;将不会重试传输。 |
| TRANSIENT_ERROR | 发生了可恢复的错误;当最小重试延迟到期时，将重试传输。 |
| 已确认    | 作业已完成。 |
| 已取消        | 已取消作业。 |

## <a name="BKMK_examples"></a>示例

下面的示例将检索名为*myDownloadJob*的作业的状态。

```
C:\>bitsadmin /GetState myDownloadJob
```

#### <a name="additional-references"></a>其他参考

[命令行语法项](command-line-syntax-key.md)
