---
title: ftp 删除
description: 用于 ftp 删除的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 067c45f3-e4e8-4450-b8b6-836994f6adfe vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4683e63700a22d8ac8016fb118475a341221e7f6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843560"
---
# <a name="ftp-delete"></a>ftp：删除

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

删除远程计算机上的文件。   
## <a name="syntax"></a>语法  
```  
delete <remoteFile>  
```  
#### <a name="parameters"></a>参数  

|  参数   |          说明          |
|--------------|-------------------------------|
| <remoteFile> | 指定要删除的文件。 |

## <a name="examples"></a><a name=BKMK_Examples></a>示例  
删除远程计算机上的文件 test.txt。  
```  
delete test.txt  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
