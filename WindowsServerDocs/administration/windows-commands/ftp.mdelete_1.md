---
title: ftp mdelete_1
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8a80a8f5-e880-40a8-abc9-29a41836844f vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b64fa691a9ac890aad0e8d8dc93bd73e53478fc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842720"
---
# <a name="ftp-mdelete_1"></a>ftp： mdelete_1

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

删除远程计算机上的文件。   
## <a name="syntax"></a>语法  
```  
mdelete <remoteFile>[ ]  
```  
#### <a name="parameters"></a>参数  

|  参数   |             说明              |
|--------------|--------------------------------------|
| <remoteFile> | 指定要删除的远程文件。 |

## <a name="examples"></a><a name=BKMK_Examples></a>示例  
删除远程文件 **.exe**和 **.exe**。  
```  
mdelete a.exe b.exe  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
