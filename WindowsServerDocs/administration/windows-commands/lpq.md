---
title: lpq
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bb6abcc4-310a-4fa4-927b-4084b62ca02e vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 051b1983fcc0fddd7b69e561c0a27a120f78d998
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840390"
---
# <a name="lpq"></a>lpq

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示运行 Line printer Daemon （LPD）的计算机上打印队列的状态。  

## <a name="syntax"></a>语法  
```  
lpq -S <ServerName> -P <printerName> [-l]  
```  
### <a name="parameters"></a>参数  

|    参数     |                                                                        说明                                                                        |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| -S <ServerName>  | 使用要显示的状态指定（按名称或 IP 地址）承载 LPD 打印队列的计算机或打印机共享设备。 必需。 |
| -P <printerName> |                           用要显示的状态指定（按名称）打印队列的打印机。 必需。                           |
|        -l        |                                      指定您希望显示有关打印队列状态的详细信息。                                      |
|        /?        |                                                           在命令提示符下显示帮助。                                                            |

## <a name="remarks"></a>备注  
**-S**和 **-P**参数区分大小写，并且必须以大写字母形式键入。  
## <a name="examples"></a><a name=BKMK_examples></a>示例  
此示例演示如何在10.0.0.45 上显示 LPD 主机上的 Laserprinter1 打印机队列的状态：  
```  
lpq -S 10.0.0.45 -P Laserprinter1  
```  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
[打印命令参考](print-command-reference.md)  
