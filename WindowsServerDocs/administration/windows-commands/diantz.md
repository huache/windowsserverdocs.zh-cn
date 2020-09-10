---
title: diantz
description: Diantz 命令的参考文章，可将现有文件打包到 cabinet ( .cab) 文件中。
ms.topic: reference
ms.assetid: 218ed5d7-1203-4d68-ad9b-65cdd022d54f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 033bfb59bbd33fee44bb307d1a905dc6c8d658c7
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635018"
---
# <a name="diantz"></a>diantz

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将现有文件打包到 cabinet ( .cab) 文件中。 此命令执行与更新的 [makecab 命令](makecab.md)相同的操作。

## <a name="syntax"></a>语法

```
diantz [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
diantz [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<source>` | 要压缩的文件。 |
| `<destination>` | 用于指定压缩文件的文件名。 如果省略，则使用下划线 (_ 替换源文件名称的最后一个字符，并将其用作目标) 。 |
| /f `<directives_file>` | 具有 **diantz** 指令的文件 (可能会重复) 。 |
| /d var =`<value>` | 定义带有指定值的变量。 |
| /l `<dir>` | 目标位置 (默认为当前目录) 。 |
| /v [ `<n>` ] | 设置调试详细级别 (0 = 无,..., 3 = 完整) 。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Microsoft Cabinet 格式](/previous-versions/bb417343(v=msdn.10))
