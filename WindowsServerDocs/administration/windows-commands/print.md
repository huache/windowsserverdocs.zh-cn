---
title: print
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa2325d5-a993-4ed3-b996-255165452db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 36966d8d3beb032ee0dcee50d9bd5bc0111bf4f5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837370"
---
# <a name="print"></a>print



向打印机发送文本文件。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
Print [/d:<PrinterName>] [<Drive>:][<Path>]<FileName>[ ...]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/d：\<PrinterName >|指定要打印作业的打印机。 若要打印到本地连接的打印机，请在计算机上指定连接打印机的端口。</br>-并行端口的有效值为 LPT1、LPT2 和 LPT3。</br>-串行端口的有效值为 COM1、COM2、COM3 和 COM4。</br>还可以通过使用其队列名称（\\\\*ServerName*\*PrinterName *）来指定网络打印机。 如果未指定打印机，则默认情况下会将打印作业发送到 LPT1。|
|\<驱动器 >：|指定要打印的文件所在的逻辑或物理驱动器。 如果要打印的文件位于当前驱动器上，则不需要此参数。|
|\<路径 >|指定要打印的文件的位置。 如果要打印的文件位于当前目录中，则此参数不是必需的。|
|\<FileName > [...]|必需。 指定要打印的文件。 可以在一个命令中包含多个文件。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   如果将文件发送到连接到本地计算机上的串行端口或并行端口的打印机，则可以在后台打印该文件。
-   您可以通过使用**Mode**命令从命令提示符执行许多配置任务。

    有关详细信息，请参阅[模式](mode.md)：  
    -   配置连接到并行端口的打印机
    -   配置连接到串行端口的打印机
    -   显示打印机的状态
    -   为代码页切换准备打印机

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将当前目录中的文件 Report .txt 发送到本地计算机上连接到 LPT2 的打印机，请键入：
```
print /d:lpt2 report.txt
```
若要将 c:\Accounting 目录中的文件 Report .txt 发送到 \\\\CopyRoom 服务器上的 Printer1 打印队列，请键入：
```
print /d:\\copyroom\printer1 c:\accounting\report.txt 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

[打印命令参考](print-command-reference.md)

[模式](mode.md)