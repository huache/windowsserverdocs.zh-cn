---
title: diantz
description: Diantz 命令的参考主题，它将现有文件打包到 cabinet （.cab）文件中。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 218ed5d7-1203-4d68-ad9b-65cdd022d54f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e45c0c4f71bc7faf6d5de0fa198ac872f6ff2597
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992502"
---
# <a name="diantz"></a>diantz

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将现有文件打包到 cab （.cab）文件中。 此命令执行与更新的[makecab 命令](makecab.md)相同的操作。

## <a name="syntax"></a>语法

```
diantz [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
diantz [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<source>` | 要压缩的文件。 |
| `<destination>` | 用于指定压缩文件的文件名。 如果省略，则使用下划线（_）替换源文件名称的最后一个字符，并将其用作目标。 |
| /f `<directives_file>` | 具有**diantz**指令的文件（可以重复）。 |
| /d var =`<value>` | 定义带有指定值的变量。 |
| /l`<dir>` | 目标位置（默认为当前目录）。 |
| /v [`<n>`] | 设置调试详细级别（0 = 无,..., 3 = 完全）。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Microsoft Cabinet 格式](https://docs.microsoft.com/previous-versions/bb417343(v=msdn.10))
