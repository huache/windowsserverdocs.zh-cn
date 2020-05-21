---
title: ftype
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6fb53cee-9bed-44dd-af5d-bc7cec1dd114
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eb4a9fa3105247695f1a50e5fc483ce608cd4816
ms.sourcegitcommit: 7116460855701eed4e09d615693efa4fffc40006
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83433121"
---
# <a name="ftype"></a>ftype



显示或修改在文件扩展名关联中使用的文件类型。 如果在没有赋值运算符（）的情况 **=** 下使用，则**ftype**将显示指定文件类型的当前打开的命令字符串。 如果在没有参数的情况下使用，则**ftype**将显示已定义打开命令字符串的文件类型。

> [!NOTE]
> 只有 CMD 中支持此命令。EXE 和无法从 PowerShell 中获取。  
> 尽管可以使用 `cmd /c ftype` 作为解决方法。


## <a name="syntax"></a>语法

```
ftype [<FileType>[=[<OpenCommandString>]]]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<类型>|指定要显示或更改的文件类型。|
|\<OpenCommandString>|指定打开指定文件类型的文件时要使用的 open 命令字符串。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

下表说明了**ftype**如何在打开的命令字符串内替换变量：

|变量|替换值|
|--------|-----------------|
|%0或 %1|替换为通过关联启动的文件名。|
|%*|获取所有参数。|
|%2，%3，.。。|获取第一个参数（%2）、第二个参数（%3）等。|
|%~\<N>|获取以第*n*个参数开头的所有剩余参数，其中*N*可以是从2到9的任意数字。|

## <a name="examples"></a>示例

若要显示已定义打开命令字符串的当前文件类型，请键入：
```
ftype
```
若要显示*txtfile*文件类型的当前打开的命令字符串，请键入：
```
ftype txtfile
```
该命令生成类似下面的输出：
```
txtfile=%SystemRoot%\system32\NOTEPAD.EXE %1
```
若要删除名为 " *Example*" 的文件类型的 "打开命令字符串"，请键入：
```
ftype example=
```
若要将 pl 文件扩展名与 PerlScript 文件类型相关联，并启用 PerlScript 文件类型以运行 PERL。EXE，键入以下命令：
```
assoc .pl=PerlScript 
ftype PerlScript=perl.exe %1 %*
```
若要在调用 Perl 脚本时不再需要键入 pl 文件扩展名，请键入：
```
set PATHEXT=.pl;%PATHEXT%
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
