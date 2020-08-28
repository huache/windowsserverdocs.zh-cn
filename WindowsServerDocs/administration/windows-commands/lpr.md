---
title: lpr
description: Lpr 命令的参考文章，该命令会将文件发送到运行 Line printer Daemon (LPD) 服务的计算机或打印机共享设备，以便为打印做准备。
ms.topic: reference
ms.assetid: afc8790b-8b52-45c4-acdf-be0ffa9da534
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5ab663ab089c6727e7354accda5dc43b2d94c946
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036335"
---
# <a name="lpr"></a>lpr

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将文件发送到运行 Line printer Daemon (LPD) 服务的计算机或打印机共享设备，以便准备打印。

## <a name="syntax"></a>语法

```
lpr [-S <servername>] -P <printername> [-C <bannercontent>] [-J <jobname>] [-o | -o l] [-x] [-d] <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -S `<servername>` | 按名称或 IP 地址指定 () 使用要显示的状态承载 LPD 打印队列的计算机或打印机共享设备。  此参数是必需的，必须大写。 |
| -P `<printername> `| 按名称指定 () 要显示其状态的打印队列的打印机。 若要查找打印机的名称，请打开 " **打印机** " 文件夹。 此参数是必需的，必须大写。 |
| -C `<bannercontent>` | 指定打印作业的标题页上要打印的内容。 如果不包含此参数，则将打印作业发送到的计算机的名称将显示在标题页上。 此参数必须大写。 |
| -J `<jobname>` | 指定将在标题页上打印的打印作业名称。 如果不包含此参数，则要打印的文件的名称将显示在标题页上。 此参数必须大写。 |
| `[-o | -o l]` | 指定要打印的文件类型。 参数 **-o** 指定要打印文本文件。 参数 **-o l** 指定要打印二进制文件 (例如) 的 PostScript 文件。 |
| -d | 指定数据文件必须在控制文件之前发送。 如果你的打印机需要首先发送数据文件，请使用此参数。 有关详细信息，请参阅打印机文档。 |
| -X | 指定 **lpr** 命令必须与 Sun Microsystems 操作系统兼容， (称为 SunOS) ，最高可包含4.1 和更高版本。4_u1。 |
| `<filename>` | 按名称指定要打印的文件)  (。 此参数是必需的。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要在*10.0.0.45*上将*Document.txt*文本文件打印到 LPD 主机上的*Laserprinter1* printer queue，请键入：

```
lpr -S 10.0.0.45 -P Laserprinter1 -o Document.txt
```

若要在*10.0.0.45*上的 LPD 主机上将*PostScript_file 的 ps* Adobe PostScript 文件打印到*Laserprinter1*打印机队列，请键入：

```
lpr -S 10.0.0.45 -P Laserprinter1 -o l PostScript_file.ps
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
