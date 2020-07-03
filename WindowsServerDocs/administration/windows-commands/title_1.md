---
title: title
description: 标题参考文章，用于为 "命令提示符" 窗口创建标题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0bbe8bd-201a-4b6c-b617-5d9809881dc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 732a0de30b9495e6281248120d2a90f85734ad8b
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930060"
---
# <a name="title"></a>title

创建 "命令提示符" 窗口的标题。



## <a name="syntax"></a>语法

```
title [<String>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<String>|指定 "命令提示符" 窗口的标题。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   若要为批处理程序创建窗口标题，请在批处理程序的开头包含**title**命令。
-   设置窗口标题后，只能使用**title**命令对其进行重置。

## <a name="examples"></a>示例

在下面的示例脚本中，命令提示符窗口的标题将更改为在批处理文件执行**复制**命令时更新文件。 执行命令后，将 `Files Updated` 显示文本，并且命令提示符窗口的标题将更改回命令提示符。
```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)