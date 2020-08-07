---
title: diskperf
description: Diskperf 命令的参考文章，可用于在运行 Windows 的计算机上远程启用或禁用物理或逻辑磁盘性能计数器。
ms.topic: article
ms.assetid: f06916e8-069b-4ec8-a6eb-59f1d9f77111
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 81cefe217abaa7b2d4ee843f3887076f66484422
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890866"
---
# <a name="diskperf"></a>diskperf

**Diskperf**命令远程启用或禁用运行 Windows 的计算机上的物理或逻辑磁盘性能计数器。

## <a name="syntax"></a>语法

```
diskperf [-y[d|v] | -n[d|v]] [\\computername]
```

## <a name="options"></a>选项

| 选项 | 描述 |
| ------ | ----------- |
| -y | 计算机重新启动时，启动所有磁盘性能计数器。 |
| -yd | 计算机重新启动时，为物理驱动器启用磁盘性能计数器。 |
| -yv | 计算机重新启动时，为逻辑驱动器或存储卷启用磁盘性能计数器。 |
| -n | 在计算机重新启动时禁用所有磁盘性能计数器。 |
| -nd | 计算机重新启动时，禁用物理驱动器的磁盘性能计数器。 |
| -nv | 计算机重新启动时，禁用逻辑驱动器或存储卷的磁盘性能计数器。 |
| `\\<computername>` | 指定要在其中启用或禁用磁盘性能计数器的计算机的名称。 |
| -? | 显示上下文相关的帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
