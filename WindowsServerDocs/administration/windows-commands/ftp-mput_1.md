---
title: ftp mput_1
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b3fb654d5a2f44b9b63238abdbaee8d6a0294861
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725219"
---
# <a name="ftp-mput_1"></a>ftp： mput_1

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将本地文件复制到远程计算机。   
## <a name="syntax"></a>语法  
```  
mput <LocalFile>[ ]  
```  
#### <a name="parameters"></a>参数  

|  参数  |                       描述                        |
|-------------|----------------------------------------------------------|
| <LocalFile> | 指定要复制到远程计算机的本地文件。 |

## <a name="examples"></a>示例  
使用当前文件传输类型将**Program1**和**program2.c**复制到远程计算机。  
```  
mput Program1.exe Program2.exe  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： ascii](ftp-ascii.md)  
-   [ftp：二进制](ftp-binary.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
