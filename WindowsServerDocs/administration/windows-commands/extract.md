---
title: extract
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 20dab03e-f6e1-4eb8-b8a1-fd6f1d97ee83
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d66682126f1cc3c924c42b4605a537a997e8ac52
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844770"
---
# <a name="extract"></a>extract



## <a name="syntax"></a>语法

```
EXTRACT [/Y] [/A] [/D | /E] [/L dir] cabinet [filename ...]
EXTRACT [/Y] source [newname]
EXTRACT [/Y] /C source destination
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|程序包|文件包含两个或多个文件。|
|filename|要从 cab 文件中提取的文件的名称。 可以使用通配符和多个文件名（由空格分隔）。|
|源程序|压缩文件（只有一个文件的文件柜）。|
|newname|用于为提取的文件指定的新文件名。 如果未提供，则使用原始名称。|
|/A|处理所有 cabinet。 从前面提到的第一个 cabinet 开始，遵循 cabinet 链。|
|/C|将源文件复制到目标（从 DMF 磁盘复制）。|
|/D|显示 cabinet 目录（与文件名一起使用以避免提取）。|
|/E|提取（使用而不是 *。* 提取所有文件）。|
|/L dir|要放置解压缩文件的位置（默认为当前目录）。|
|/Y|请不要在覆盖现有文件之前进行提示。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)