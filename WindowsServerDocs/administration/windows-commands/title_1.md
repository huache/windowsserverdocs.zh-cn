---
title: title
description: 用于标题的 Windows 命令主题，用于创建 "命令提示符" 窗口的标题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0bbe8bd-201a-4b6c-b617-5d9809881dc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aae18e97daaef226443c5f18c6c401a4e2b82b59
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832800"
---
# <a name="title"></a>title

创建 "命令提示符" 窗口的标题。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
title [<String>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<字符串 >|指定 "命令提示符" 窗口的标题。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   若要为批处理程序创建窗口标题，请在批处理程序的开头包含**title**命令。
-   设置窗口标题后，只能使用**title**命令对其进行重置。

## <a name="examples"></a><a name=BKMK_examples></a>示例

在下面的示例脚本中，命令提示符窗口的标题将更改为在批处理文件执行**复制**命令时更新文件。 执行命令后，将显示文本 "`Files Updated`"，并将 "命令提示符" 窗口的标题更改回命令提示符。
```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)