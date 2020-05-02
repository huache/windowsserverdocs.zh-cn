---
title: ftp mdelete_1
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8a80a8f5-e880-40a8-abc9-29a41836844f vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f578a50207439f9bfb21c2607f0aa60a20fad292
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725030"
---
# <a name="ftp-mdelete_1"></a>ftp： mdelete_1

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除远程计算机上的文件。   
## <a name="syntax"></a>语法  
```  
mdelete <remoteFile>[ ]  
```  
#### <a name="parameters"></a>参数  

|  参数   |             描述              |
|--------------|--------------------------------------|
| <remoteFile> | 指定要删除的远程文件。 |

## <a name="examples"></a>示例  
删除远程文件 **.exe**和 **.exe**。  
```  
mdelete a.exe b.exe  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
