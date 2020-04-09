---
title: type
description: 用于显示文本文件的内容的 "类型" 的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c44fe905-a865-4c97-8cc5-fb95fec7d4d5
author: coreyp-at-msft
ms.author: coreyp
manager: dansimp
ms.openlocfilehash: 3163601d118df315edcae540917313703f677d52
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832410"
---
# <a name="type"></a>type

在 Windows 命令行界面中，**键入**"内置命令"，其中显示文本文件的内容。 使用**type**命令查看文本文件，而不进行修改。

在 PowerShell 中，**键入**是 **[获取内容](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content)** cmdlet 的内置别名，它还显示文件的内容，但使用不同的语法。

有关如何在 Windows 命令行界面（Cmd.exe）中使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
type [<Drive>:][<Path>]<FileName>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[\<驱动器 >：][\<路径 >]\<文件名 >|指定要查看的一个或哪些文件的位置和名称。 用空格分隔多个文件名。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   如果*FileName*包含空格，则用引号将其引起来（例如，文件名包含空格 .txt）。
-   如果显示的是由程序创建的二进制文件或文件，则屏幕上可能会出现奇怪的字符，包括换页符字符和转义序列符号。 这些字符表示二进制文件中使用的控制代码。 通常，应避免使用**type**命令显示二进制文件。

## <a name="examples"></a><a name=BKMK_examples></a>示例

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
