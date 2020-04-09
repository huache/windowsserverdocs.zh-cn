---
title: ftp mget
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 72b45f84622fcd6abf7a743f606fb514def584cd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843350"
---
# <a name="ftp-mget"></a>ftp： mget

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

使用当前文件传输类型将远程文件复制到本地计算机。   
## <a name="syntax"></a>语法  
```  
mget <remoteFile>[ ]  
```  
#### <a name="parameters"></a>参数  

|  参数   |                        说明                        |
|--------------|-----------------------------------------------------------|
| <remoteFile> | 指定要复制到本地计算机的远程文件。 |

## <a name="examples"></a><a name=BKMK_Examples></a>示例  
使用当前文件传输类型将远程文件 **.exe**和 **.exe**复制到本地计算机。  
```  
mget a.exe b.exe  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： ascii](ftp-ascii.md)  
-   [ftp：二进制](ftp-binary.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
