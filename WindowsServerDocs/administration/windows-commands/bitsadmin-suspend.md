---
title: bitsadmin suspend
description: Bitsadmin 挂起命令的参考文章，用于挂起指定的作业。
ms.topic: reference
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ad4ca877ac9e5548f3d3ec830f8fc2822f781218
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033385"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

挂起指定的作业。 如果错误地挂起了作业，则可以使用 [bitsadmin resume](bitsadmin-resume.md) 开关来重新启动作业。

## <a name="syntax"></a>语法

```
bitsadmin /suspend <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ---------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="example"></a>示例

若要挂起名为 *myDownloadJob*的作业：


```
bitsadmin /suspend myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin resume 命令](bitsadmin-resume.md)

- [bitsadmin 命令](bitsadmin.md)
