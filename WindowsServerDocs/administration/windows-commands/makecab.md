---
title: makecab
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4da95297-c593-427b-9f76-2f389c46cbf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 46efbae1d59a85071622df51fc018d0bf73dc504
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840260"
---
# <a name="makecab"></a>makecab

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将现有文件打包到 cab （.cab）文件中。
## <a name="syntax"></a>语法
```
makecab [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
makecab [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```
#### <a name="parameters"></a>参数

|      参数       |                                                                        说明                                                                        |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|       <source>       |                                                                     要压缩的文件。                                                                     |
|    <destination>     | 用于指定压缩文件的文件名。 如果省略，则使用下划线（_）替换源文件名称的最后一个字符，并将其用作目标。 |
| /f < directives_file > |                                                   具有**makecab**指令的文件（可以重复）。                                                   |
|    /d var =<value>    |                                                          定义带有指定值的变量。                                                           |
|       /l <dir>       |                                               目标位置（默认为当前目录）。                                               |
|       /v [<n>]        |                                                    设置调试详细级别（0 = 无,..., 3 = 完全）。                                                     |
|          /?          |                                                           在命令提示符下显示帮助。                                                            |

## <a name="remarks"></a>备注
-   有关 directive_file 的信息，请参阅 MSDN 上的[Microsoft Cabinet 格式](https://go.microsoft.com/fwlink/?LinkId=226852)。

## <a name="additional-references"></a>其他参考
-   - [命令行语法项](command-line-syntax-key.md)

