---
title: ftp mput_1
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 489e18da937e12a1fc69e0ee84d9dda00309ccd6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843230"
---
# <a name="ftp-mput_1"></a>ftp： mput_1

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

使用当前文件传输类型将本地文件复制到远程计算机。   
## <a name="syntax"></a>语法  
```  
mput <LocalFile>[ ]  
```  
#### <a name="parameters"></a>参数  

|  参数  |                       说明                        |
|-------------|----------------------------------------------------------|
| <LocalFile> | 指定要复制到远程计算机的本地文件。 |

## <a name="examples"></a><a name=BKMK_Examples></a>示例  
使用当前文件传输类型将**Program1**和**program2.c**复制到远程计算机。  
```  
mput Program1.exe Program2.exe  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： ascii](ftp-ascii.md)  
-   [ftp：二进制](ftp-binary.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
