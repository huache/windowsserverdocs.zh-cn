---
title: diskperf
description: Diskperf 命令的参考主题，可用于在运行 Windows 的计算机上远程启用或禁用物理或逻辑磁盘性能计数器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f06916e8-069b-4ec8-a6eb-59f1d9f77111
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 092518f414d6e27436c46ffd6f9f15b6e6c0407e
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992429"
---
# <a name="diskperf"></a>diskperf

**Diskperf**命令远程启用或禁用运行 Windows 的计算机上的物理或逻辑磁盘性能计数器。

## <a name="syntax"></a>语法

```
diskperf [-y[d|v] | -n[d|v]] [\\computername]
```

## <a name="options"></a>选项

| 选项 | 说明 |
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
