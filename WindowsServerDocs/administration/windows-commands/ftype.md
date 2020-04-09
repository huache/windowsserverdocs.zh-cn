---
title: ftype
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6fb53cee-9bed-44dd-af5d-bc7cec1dd114
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f982f68f25a4decbc9c572b533fa1ecc5e893a8c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842700"
---
# <a name="ftype"></a>ftype



显示或修改在文件扩展名关联中使用的文件类型。 如果在没有赋值运算符（ **=** ）的情况下使用，则**ftype**将显示指定文件类型的当前打开命令字符串。 如果在没有参数的情况下使用，则**ftype**将显示已定义打开命令字符串的文件类型。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
ftype [<FileType>[=[<OpenCommandString>]]]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<类型 >|指定要显示或更改的文件类型。|
|\<OpenCommandString >|指定打开指定文件类型的文件时要使用的 open 命令字符串。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

下表说明了**ftype**如何在打开的命令字符串内替换变量：

|变量|替换值|
|--------|-----------------|
|%0或 %1|替换为通过关联启动的文件名。|
|%*|获取所有参数。|
|%2，%3，。|获取第一个参数（%2）、第二个参数（%3）等。|
|%~\<N >|获取以第*n*个参数开头的所有剩余参数，其中*N*可以是从2到9的任意数字。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要显示已定义打开命令字符串的当前文件类型，请键入：
```
ftype
```
若要显示*txtfile*文件类型的当前打开的命令字符串，请键入：
```
ftype txtfile
```
此命令生成类似于以下内容的输出：
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