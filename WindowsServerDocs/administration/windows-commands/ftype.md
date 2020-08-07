---
title: ftype
description: Ftype 命令的参考文章，其中显示或修改在文件扩展名关联中使用的文件类型。
ms.topic: article
ms.assetid: 6fb53cee-9bed-44dd-af5d-bc7cec1dd114
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed4a8a698328737259f830118fa9c6a482247884
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87888717"
---
# <a name="ftype"></a>ftype

显示或修改在文件扩展名关联中使用的文件类型。 如果在没有赋值运算符的情况下使用 (=) ，则此命令将显示指定文件类型的当前打开的命令字符串。 如果在没有参数的情况下使用，则此命令将显示已定义打开命令字符串的文件类型。

> [!NOTE]
> 此命令仅在 cmd.exe 中受支持，并且在 PowerShell 中不可用。
> 尽管可以使用 `cmd /c ftype` 作为解决方法。

## <a name="syntax"></a>语法

```
ftype [<filetype>[=[<opencommandstring>]]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<filetype>` | 指定要显示或更改的文件类型。 |
| `<opencommandstring>` | 指定打开指定文件类型的文件时要使用的 open 命令字符串。|
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

下表说明了**ftype**如何在打开的命令字符串内替换变量：

| 变量 | 替换值 |
| -------- | ----------------- |
| `%0` 或 `%1` | 替换为通过关联启动的文件名。 |
| `%*` | 获取所有参数。 |
| `%2`, `%3`, ... | 获取 () 的第一个参数 `%2` ，第二个参数 (`%3`) ，依此类推。 |
| `%~<n>` | 获取以第*n*个参数开头的所有剩余参数，其中*n*可以是从2到9的任意数字。 |

### <a name="examples"></a>示例

若要显示已定义打开命令字符串的当前文件类型，请键入：

```
ftype
```

若要显示*txtfile*文件类型的当前打开的命令字符串，请键入：

```
ftype txtfile
```

该命令生成类似下面的输出：

`txtfile=%SystemRoot%\system32\NOTEPAD.EXE %1`

若要删除名为 " *example*" 的文件类型的 "打开命令字符串"，请键入：

```
ftype example=
```

若要将 pl 文件扩展名与 PerlScript 文件类型关联并使 PerlScript 文件类型 PERL.EXE 运行，请键入以下命令：

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
