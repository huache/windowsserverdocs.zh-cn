---
title: 类型
description: 用于显示文本文件内容的类型的参考文章。
ms.topic: reference
ms.assetid: c44fe905-a865-4c97-8cc5-fb95fec7d4d5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.openlocfilehash: 7b944037c6dc73de89fa92b54a41b07ff09fcf69
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626667"
---
# <a name="type"></a>类型

在 Windows 命令行界面中， **键入** "内置命令"，其中显示文本文件的内容。 使用 **type** 命令查看文本文件，而不进行修改。

在 PowerShell 中， **键入** 是 **[获取内容](/powershell/module/microsoft.powershell.management/get-content)** cmdlet 的内置别名，它还显示文件的内容，但使用不同的语法。

## <a name="syntax"></a>语法

```
type [<Drive>:][<Path>]<FileName>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[\<Drive>:][\<Path>]\<FileName>|指定要查看的一个或哪些文件的位置和名称。 用空格分隔多个文件名。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   如果 *FileName* 包含空格，则用引号将其引起来 (例如，包含 Spaces.txt) 的文件名。
-   如果显示的是由程序创建的二进制文件或文件，则屏幕上可能会出现奇怪的字符，包括换页符字符和转义序列符号。 这些字符表示二进制文件中使用的控制代码。 通常，应避免使用 **type** 命令显示二进制文件。

## <a name="examples"></a>示例

若要显示名为 "假日" 的文件的内容，请键入：
```
type holiday.mar
```
若要显示名为 "假日" 的长文件的内容，请一次一个屏幕，键入：
```
type holiday.mar | more
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
