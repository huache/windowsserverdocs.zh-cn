---
title: break
description: 用于中断命令的参考文章，此命令将焦点分成两个简单卷的镜像卷。
ms.topic: reference
ms.assetid: ffc4901c-457b-46a6-a671-3052355f8a3c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e65ec0ad5a97578f0e6452e6225302a6ba053984
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630042"
---
# <a name="break"></a>break

> [!IMPORTANT]
> 此命令已不再使用。 包括该命令仅用于保持与现有 MS-DOS 文件的兼容性，但由于该命令的功能是自动的，因此在命令行上不起作用。

设置或清除对 MS-DOS 系统的扩展 CTRL + C 检查。 如果在没有参数的情况下使用，则 **break** 将显示现有设置值。

如果命令扩展已在 Windows 平台上启用并运行，则在批处理文件中插入 **break** 命令将进入硬编码的断点，前提是调试器正在调试该断点。

## <a name="syntax"></a>语法

```
break=[on|off]
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [break 命令](break.md)