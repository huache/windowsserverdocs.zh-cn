---
title: makecab
description: Makecab 命令的参考文章，可将现有文件打包到 cabinet ( .cab) 文件中。
ms.topic: reference
ms.assetid: 4da95297-c593-427b-9f76-2f389c46cbf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 560a2a75c756fb90b87da9f63a86a6dc887f836b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023681"
---
# <a name="makecab"></a>makecab

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将现有文件打包到 cabinet ( .cab) 文件中。


> [!NOTE]
> 此命令与 [diantz 命令](diantz.md)相同。

## <a name="syntax"></a>语法

```
makecab [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
makecab [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<source>` | 要压缩的文件。 |
| `<destination>` | 用于指定压缩文件的文件名。 如果省略，则使用下划线 (_ 替换源文件名称的最后一个字符，并将其用作目标) 。 |
| /f `<directives_file>` | 具有 **makecab** 指令的文件 (可能会重复) 。 |
| /d var =`<value>` | 定义带有指定值的变量。 |
| /l `<dir>` | 目标位置 (默认为当前目录) 。 |
| /v [ `<n>` ] | 设置调试详细级别 (0 = 无,..., 3 = 完整) 。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [diantz 命令](diantz.md)

- [Microsoft Cabinet 格式](/previous-versions/bb417343(v=msdn.10))
