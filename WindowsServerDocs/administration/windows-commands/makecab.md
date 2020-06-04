---
title: makecab
description: Makecab 命令的参考主题，它将现有文件打包到 cabinet （.cab）文件中。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4da95297-c593-427b-9f76-2f389c46cbf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 192471e6045a530e9deedec70cc957b9362b3ae7
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354657"
---
# <a name="makecab"></a>makecab

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将现有文件打包到 cab （.cab）文件中。


> [!NOTE]
> 此命令与[diantz 命令](diantz.md)相同。

## <a name="syntax"></a>语法

```
makecab [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
makecab [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<source>` | 要压缩的文件。 |
| `<destination>` | 用于指定压缩文件的文件名。 如果省略，则使用下划线（_）替换源文件名称的最后一个字符，并将其用作目标。 |
| /f `<directives_file>` | 具有**makecab**指令的文件（可以重复）。 |
| /d var =`<value>` | 定义带有指定值的变量。 |
| /l`<dir>` | 目标位置（默认为当前目录）。 |
| /v [ `<n>` ] | 设置调试详细级别（0 = 无,..., 3 = 完全）。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [diantz 命令](diantz.md)

- [Microsoft Cabinet 格式](https://docs.microsoft.com/previous-versions/bb417343(v=msdn.10))
