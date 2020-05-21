---
title: exec
description: Exec 命令的参考主题，它在本地计算机上运行脚本文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 956f3d4a7c5992980aea0fc0f5933ee7def48381
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436103"
---
# <a name="exec"></a>exec

在本地计算机上运行脚本文件。 此命令还在备份或还原顺序中复制或还原数据。 如果脚本失败，将返回错误，并且 DiskShadow 将退出。

该文件可以是**cmd**脚本。

## <a name="syntax"></a>语法

```
exec <scriptfile.cmd>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<scriptfile.cmd>` | 指定要运行的脚本文件。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [diskshadow 命令](diskshadow.md)
