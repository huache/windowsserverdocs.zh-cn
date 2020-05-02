---
title: ftp get
description: Ftp get 的参考主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d70355c4-58ef-43e0-916b-c7ecf77e6ee4 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 37423f81fd72e79cebcdf169160ad3e8033b69b2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725297"
---
# <a name="ftp-get"></a>ftp： get

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将远程文件复制到本地计算机。   
## <a name="syntax"></a>语法  
```  
get <remoteFile> [<LocalFile>]  
```  
#### <a name="parameters"></a>参数  

|   参数   |                                                              描述                                                               |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------|
| <remoteFile>  |                                                   指定要复制的远程文件。                                                   |
| [<LocalFile>] | 指定要在本地计算机上使用的文件的名称。 如果未指定*LocalFile* ，则会为该文件提供*remoteFile*名称。 |

## <a name="remarks"></a>备注  
**Get**命令与 "**接收**" 命令完全相同。  
## <a name="examples"></a>示例  
使用当前文件传输类型将**test.txt**复制到本地计算机。  
```  
get test.txt  
```  
使用当前文件传输类型将**test.txt**复制到本地**计算机。**  
```  
Get test.txt test1.txt  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： ascii](ftp-ascii.md)  
-   [ftp：二进制](ftp-binary.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
