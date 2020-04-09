---
title: ftp mls_1
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4738fd49-0e80-4bdf-a773-0f973db3a710 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ca3b8e04dd4a152b2d1bf8ce1ca8006d70186116
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843290"
---
# <a name="ftp-mls_1"></a>ftp： mls_1

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示远程目录中的文件和子目录的简短列表。   
## <a name="syntax"></a>语法  
```  
mls <remoteFile>[ ] <LocalFile>  
```  
#### <a name="parameters"></a>参数  

|  参数   |                       说明                       |
|--------------|---------------------------------------------------------|
| <remoteFile> | 指定要查看其列表的文件。 |
| <LocalFile>  |  指定要在其中存储列表的本地文件。  |

## <a name="remarks"></a>备注  
- 指定*remoteFiles*  
  键入连字符（ **-** ）以使用远程计算机上的当前工作目录。  
- 指定*LocalFile*  
  键入连字号（ **-** ）以在屏幕上显示列表。  
  ## <a name="examples"></a><a name=BKMK_Examples></a>示例  
  显示**dir1**和**dir2**的文件和子目录的简短列表。  
  ```  
  mls dir1 dir2 -  
  ```  
  为本地文件**dirlist**中的**dir1**和**dir2**保存简短的文件和子目录列表  
  ```  
  mls dir1 dir2 dirlist.txt   
  ```  
  ## <a name="additional-references"></a>其他参考  
- - [命令行语法项](command-line-syntax-key.md)  
