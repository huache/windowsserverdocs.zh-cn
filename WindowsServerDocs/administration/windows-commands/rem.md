---
title: rem
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1a45b585-a83c-4ff6-badd-ff40f34cec23
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d115548f15ff45087a771458062da8a3ef919eb3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722456"
---
# <a name="rem"></a>rem



在批处理文件或配置中记录注释（备注）。系统. 如果未指定任何注释，则**rem**将增加垂直间距。



## <a name="syntax"></a>语法

```
rem [<Comment>]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<注释>|指定要包含为注释的字符串。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   **Rem**命令不在屏幕上显示注释。 你必须在批处理或配置中使用**echo on**命令。SYS 文件，用于在屏幕上显示注释。
-   不能在批处理文件注释中**<** 使用**>** 重定向字符（**|** 或）或竖线（）。
-   尽管可以使用不带注释的**rem**来向批处理文件添加垂直间距，但也可以使用空行。 处理批处理程序时，将忽略空白行。

## <a name="examples"></a>示例

若要显示使用注释和垂直间距的批处理文件，请执行以下操作：
```
@echo off
rem  This batch program formats and checks new disks.
rem  It is named Checknew.bat.
rem
rem echo Insert new disk in Drive B.
pause 
format b: /v chkdsk b: 
```
在配置中的**prompt**命令之前包含解释性注释。SYS 文件中，将以下行添加到 CONFIG。系统
```
rem Set prompt to indicate current directory
prompt $p$g
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)