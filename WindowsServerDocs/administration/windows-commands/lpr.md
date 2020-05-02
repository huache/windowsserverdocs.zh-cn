---
title: lpr
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: afc8790b-8b52-45c4-acdf-be0ffa9da534 jpjofre
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f523c55f5974599c152f4fbae7d8143d5362af62
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724245"
---
# <a name="lpr"></a>lpr

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将文件发送到运行行打印机后台程序（LPD）服务的计算机或打印机共享设备，以便为打印做准备。  

## <a name="syntax"></a>语法  
```  
lpr [-S <ServerName>] -P <printerName> [-C <BannerContent>] [-J <JobName>] [-o | -o l] [-x] [-d] <filename>  
```  
### <a name="parameters"></a>参数  

|     参数      |                                                                                                           描述                                                                                                           |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  -S<ServerName>   |                                    使用要显示的状态指定（按名称或 IP 地址）承载 LPD 打印队列的计算机或打印机共享设备。 必需。                                    |
|  -P<printerName>  |                                                              用要显示的状态指定（按名称）打印队列的打印机。 必需。                                                              |
| -C<BannerContent> |                指定打印作业的标题页上要打印的内容。 如果不包含此参数，则将打印作业发送到的计算机的名称将显示在标题页上。                 |
|    -J<JobName>    |                           指定将在标题页上打印的打印作业名称。 如果不包含此参数，则要打印的文件的名称将显示在标题页上。                            |
| [-o&#124;-o l]  | 指定要打印的文件类型。 参数 **-o**指定要打印文本文件。 参数 **-o l**指定要打印二进制文件（如 PostScript 文件）。 |
|         -d         |              指定数据文件必须在控制文件之前发送。 如果你的打印机需要首先发送数据文件，请使用此参数。 有关详细信息，请参阅打印机文档。               |
|         -X         |                               指定**lpr**命令必须与 Microsystems 的 Sun 的操作系统（称为 SunOS）兼容，最多释放4.1。4_u1。                                |
|     <FileName>     |                                                                                      指定要打印的文件（按名称）。 必需。                                                                                      |
|         /?         |                                                                                              在命令提示符下显示帮助。                                                                                               |

## <a name="remarks"></a>备注  
- 若要查找打印机的名称，请打开 "打印机" 文件夹。  
- **-S**、 **-P**、 **-C**和 **-J**参数区分大小写，并且必须以大写字母形式键入。  
  ## <a name="examples"></a>示例  
  此示例演示如何在10.0.0.45 上将文档 .txt 文本文件打印到 LPD 主机上的 Laserprinter1 打印机队列：  
  ```  
  lpr -S 10.0.0.45 -P Laserprinter1 -o Document.txt  
  ```  
  此示例演示如何将 PostScript_file 的 ps Adobe PostScript 文件打印到10.0.0.45 上的 LPD 主机上的 Laserprinter1 打印机队列：  
  ```  
  lpr -S 10.0.0.45 -P Laserprinter1 -o l PostScript_file.ps  
  ```  

## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
-   [打印命令参考](print-command-reference.md)  
