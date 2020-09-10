---
title: print
description: 用于向打印机发送文本文件的 "打印" 命令的参考文章。
ms.topic: reference
ms.assetid: aa2325d5-a993-4ed3-b996-255165452db8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7155056219fd080674885146f62a5aa4a033366d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638377"
---
# <a name="print"></a>print

向打印机发送文本文件。 如果将文件发送到连接到本地计算机上的串行端口或并行端口的打印机，则可以在后台打印该文件。

> [!NOTE]
> 您可以通过命令提示符使用 " [模式" 命令](mode.md)执行许多配置任务，包括配置连接到并行或串行端口的打印机、显示打印机状态或准备打印机以进行代码页切换。

## <a name="syntax"></a>语法

```
print [/d:<printername>] [<drive>:][<path>]<filename>[ ...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /d`<printername>` | 指定要打印作业的打印机。 若要打印到本地连接的打印机，请在计算机上指定连接打印机的端口。 并行端口的有效值为 **LPT1**、 **LPT2**和 **LPT3**。 串行端口的有效值为 **COM1**、 **COM2**、 **COM3**和 **COM4**。 你还可以使用 () 来指定网络打印机的队列名称 `\\server_name\printer_name` 。 如果未指定打印机，则默认情况下会将打印作业发送到 **LPT1** 。 |
| `<drive>`: | 指定要打印的文件所在的逻辑或物理驱动器。 如果要打印的文件位于当前驱动器上，则不需要此参数。 |
| `<path>` | 指定要打印的文件的位置。 如果要打印的文件位于当前目录中，则不需要此参数。 |
| `<filename>[ ...]` | 必需。 指定要打印的文件。 可以在一个命令中包含多个文件。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要将当前目录中的 **report.txt** 文件发送到连接到本地计算机上的 **lpt2** 的打印机，请键入：

```
print /d:lpt2 report.txt
```

若要将**c:\accounting**目录中的**report.txt**文件发送到 **/d： \\ copyroom**服务器上的**printer1**打印队列，请键入：

```
print /d:\\copyroom\printer1 c:\accounting\report.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)

- [Mode 命令](mode.md)