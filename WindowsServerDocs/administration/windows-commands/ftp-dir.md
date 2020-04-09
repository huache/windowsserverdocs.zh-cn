---
title: ftp 目录
description: Ftp 目录的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a29a92a5-7b79-4e6e-95cf-2ccb38bb6fb2 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 64f227ea9806f169c2df1698382cfce6e7ac3257
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843570"
---
# <a name="ftp-dir"></a>ftp： dir

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示远程计算机上的目录文件和子目录的列表。   
## <a name="syntax"></a>语法  
```  
dir [<remotedirectory>] [<LocalFile>]  
```  
#### <a name="parameters"></a>参数  
|参数|说明|  
|-------|--------|  
|[<remotedirectory>]|指定要查看其列表的目录。 如果未指定目录，则使用远程计算机上的当前工作目录。|  
|[<LocalFile>]|指定要在其中存储目录列表的本地文件。 如果未指定本地文件，则结果将显示在屏幕上。|  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
在远程计算机上显示**dir1**的目录列表。  
```  
dir dir1  
```  
将远程计算机上的当前目录的列表保存在本地文件**dirlist**中。  
```  
dir . dirlist.txt  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
