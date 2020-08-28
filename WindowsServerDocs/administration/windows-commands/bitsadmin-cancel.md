---
title: bitsadmin cancel
description: Bitsadmin cancel 命令的参考文章，此命令从传输队列中删除作业，并删除与该作业关联的所有临时文件。
ms.topic: reference
ms.assetid: 7374b544-6a16-4d3e-872c-dcf4c02ad89d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: da7a858603875affc7acc8bcb60d02451a641690
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024431"
---
# <a name="bitsadmin-cancel"></a>bitsadmin cancel

从传输队列中删除该作业并删除与作业关联的所有临时文件。

## <a name="syntax"></a>语法

```
bitsadmin /cancel <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

从传输队列中删除 *myDownloadJob* 作业：

```
bitsadmin /cancel myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
