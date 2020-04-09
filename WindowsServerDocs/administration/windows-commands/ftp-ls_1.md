---
title: ftp ls_1
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5e03c7db-1e2b-419c-acb2-8a68f3db9615 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5ff63272fe3c5e59965b04bef258a06fee2da0c4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843360"
---
# <a name="ftp-ls_1"></a>ftp： ls_1

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012
> 
> 
> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示远程计算机上的文件和子目录的缩写列表。   
## <a name="syntax"></a>语法  
```  
ls [<remotedirectory>] [<LocalFile>]  
```  
#### <a name="parameters"></a>参数  

|      参数      |                                                                       说明                                                                        |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<remotedirectory>] | 指定要查看其列表的目录。 如果未指定目录，则使用远程计算机上的当前工作目录。 |
|    [<LocalFile>]    |               指定要在其中存储列表的本地文件。 如果未指定本地文件，则结果将显示在屏幕上。               |

## <a name="examples"></a><a name=BKMK_Examples></a>示例  
显示远程计算机上的文件和子目录的简短列表。  
```  
ls  
```  
获取远程计算机上的**dir1**的缩略目录列表，并将其保存到名为**dirlist**的本地文件中  
```  
ls dir1 dirlist.txt   
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
