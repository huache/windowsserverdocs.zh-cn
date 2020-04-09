---
title: break
description: 适用于 break_1 的 Windows 命令主题，用于设置或清除对 MS-DOS 系统的扩展 CTRL + C 检查。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c89b7357-d69e-4141-826e-73c9ba0fc630
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 809a9321b8b4f8b2d201582f767da132076826d4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848360"
---
# <a name="break"></a>break

设置或清除对 MS-DOS 系统的扩展 CTRL + C 检查。 如果在没有参数的情况下使用，则**break**将显示当前设置。

> [!NOTE]
> 此命令已不再使用。 包括此功能的目的仅在于保持与现有 MS-DOS 文件的兼容性，而由于此功能是自动的，因此它对命令行没有任何影响。

## <a name="syntax"></a>语法

```
break=[on|off]
```

## <a name="remarks"></a>备注

如果命令扩展已在 Windows 平台上启用并运行，则在批处理文件中插入**break**命令将进入硬编码的断点，前提是调试器正在调试该断点。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)