---
title: ftp remotehelp_1
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ef23adf3-ead4-44c8-ac1d-c8a6f4b2bf73 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3c4a4ffec01fce5cde8b2aa9dd1fa0704f3a85ff
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843050"
---
# <a name="ftp-remotehelp_1"></a>ftp： remotehelp_1

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示远程命令的帮助。   
## <a name="syntax"></a>语法  
```  
remotehelp [<Command>]  
```  
#### <a name="parameters"></a>参数  
|参数|说明|  
|-------|--------|  
|[<Command>]|指定需要帮助的命令的名称。 如果未指定*命令*， **ftp**将显示所有远程命令的列表。|  
## <a name="remarks"></a>备注  
可以使用**引号**或**文本**运行远程命令。  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
显示远程命令的列表。  
```  
remotehelp  
```  
显示 "**特征**" 远程命令的语法。  
```  
remotehelp feat  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp：引用](ftp-quote.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
