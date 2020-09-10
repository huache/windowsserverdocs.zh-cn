---
title: setlocal
description: Setlocal 的参考文章，用于开始批处理文件中的环境变量的本地化。
ms.topic: reference
ms.assetid: e4e4b6d3-3f1a-4851-a782-25ee2470e16e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 807bcb1d5694617f9632e88a4bc200a714048cc9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639461"
---
# <a name="setlocal"></a>setlocal

开始批处理文件中的环境变量的本地化。 在遇到匹配的 **endlocal** 命令或到达批处理文件的末尾之前，本地化将继续。



## <a name="syntax"></a>语法

```
setlocal [enableextensions | disableextensions] [enabledelayedexpansion | disabledelayedexpansion]
```

## <a name="arguments"></a>参数

|参数|说明|
|--------|-----------|
|enableextensions|在遇到匹配的 **endlocal** 命令之前启用命令扩展，而不考虑在运行 **setlocal** 命令之前的设置。|
|disableextensions|在遇到匹配的 **endlocal** 命令之前禁用命令扩展，而不考虑在运行 **setlocal** 命令之前的设置。|
|enabledelayedexpansion|在遇到匹配的 **endlocal** 命令之前，启用延迟环境变量扩展，而不考虑运行 **setlocal** 命令之前的设置。|
|disabledelayedexpansion|在遇到匹配的 **endlocal** 命令之前，禁用延迟的环境变量扩展，而不考虑在运行 **setlocal** 命令之前的设置。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   使用 **setlocal**

    在脚本或批处理文件外使用 **setlocal** 时，它不起作用。
-   更改环境变量

    运行批处理文件时，请使用 **setlocal** 更改环境变量。 运行 **setlocal** 后所做的环境更改是批处理文件的本地环境。 Cmd.exe 程序将在遇到 **endlocal** 命令或到达批处理文件末尾时还原以前的设置。
-   嵌套命令

    批处理程序中可以有多个 **setlocal** 或 **endlocal** 命令 (也就是说，) 的嵌套命令。
-   在批处理文件中测试命令扩展

    **Setlocal**命令设置 ERRORLEVEL 变量。 如果传递 {**enableextensions**  |  **disableextensions**} 或 {**enabledelayedexpansion**  |  **disabledelayedexpansion**}，则 ERRORLEVEL 变量将设置为**0** (零) 。 否则，将其设置为 **1**。 可以在批处理脚本中使用此信息来确定扩展是否可用，如以下示例中所示：
    ```
    setlocal enableextensions
    verify other 2>nul
    if errorlevel 1 echo Unable to enable extensions
    ```
    由于 **cmd** 在禁用命令扩展时未设置 ERRORLEVEL 变量，因此当你将 ERRORLEVEL 变量与无效参数一起使用时， **verify** 命令会将其初始化为非零值。 此外，如果你将**setlocal**命令与参数 {**enableextensions**  |  **disableextensions**} 或 {**enabledelayedexpansion**  |  **disabledelayedexpansion**} 一起使用，并且它未将 ERRORLEVEL 变量设置为**1**，则命令扩展不可用。

## <a name="examples"></a>示例

可以在批处理文件中本地化环境变量，如下面的示例脚本所示：
```
rem *******Begin Comment**************
rem This program starts the superapp batch program on the network,
rem directs the output to a file, and displays the file
rem in Notepad.
rem *******End Comment**************
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)