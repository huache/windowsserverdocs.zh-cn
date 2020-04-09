---
title: ftp 追加
description: Ftp 追加的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 44ce1d6e7259dc8745da35ed462e6378f0fce8ba
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843820"
---
# <a name="ftp-append"></a>ftp：追加

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

使用 "当前文件类型" 设置将本地文件追加到远程计算机上的文件。   
## <a name="syntax"></a>语法  
```  
append <LocalFile> [remoteFile]  
```  
#### <a name="parameters"></a>参数  

|  参数   |                               说明                                |
|--------------|--------------------------------------------------------------------------|
| <LocalFile>  |                     指定要添加的本地文件。                     |
| [remoteFile] | 指定远程计算机上 <LocalFile> 添加到的文件。 |

## <a name="remarks"></a>备注  
如果省略*remoteFile* ，则使用*LocalFile*名称代替远程文件名。  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
将 file1 附加到远程计算机上的 file2。  
```  
append file1.txt file2.txt  
```  
将本地 file1 附加到远程计算机上名为 file1 的文件中。  
```  
append file1.txt  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
