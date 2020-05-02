---
title: ftp mget
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a71fbfb60ae012b5e65af04e6f3e21ec796996a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725238"
---
# <a name="ftp-mget"></a>ftp： mget

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将远程文件复制到本地计算机。   
## <a name="syntax"></a>语法  
```  
mget <remoteFile>[ ]  
```  
#### <a name="parameters"></a>参数  

|  参数   |                        描述                        |
|--------------|-----------------------------------------------------------|
| <remoteFile> | 指定要复制到本地计算机的远程文件。 |

## <a name="examples"></a>示例  
使用当前文件传输类型将远程文件 **.exe**和 **.exe**复制到本地计算机。  
```  
mget a.exe b.exe  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： ascii](ftp-ascii.md)  
-   [ftp：二进制](ftp-binary.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
