---
title: ftp mls_1
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4738fd49-0e80-4bdf-a773-0f973db3a710 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 27f74d4c1d03cb4d9f665566f69485e80f8eccdc
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725205"
---
# <a name="ftp-mls_1"></a>ftp： mls_1

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示远程目录中的文件和子目录的简短列表。   
## <a name="syntax"></a>语法  
```  
mls <remoteFile>[ ] <LocalFile>  
```  
#### <a name="parameters"></a>参数  

|  参数   |                       描述                       |
|--------------|---------------------------------------------------------|
| <remoteFile> | 指定要查看其列表的文件。 |
| <LocalFile>  |  指定要在其中存储列表的本地文件。  |

## <a name="remarks"></a>备注  
- 指定*remoteFiles*  
  键入连字符（**-**）以使用远程计算机上的当前工作目录。  
- 指定*LocalFile*  
  键入连字号（**-**）可在屏幕上显示列表。  
  ## <a name="examples"></a>示例  
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
