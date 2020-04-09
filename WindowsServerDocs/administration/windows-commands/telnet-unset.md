---
title: 未设置 telnet
description: 用于 telnet unset 的 Windows 命令主题，这会关闭先前设置的选项。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 34d52eedb2a5547ad0e3f2912dbe2a250eaf8fc5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833140"
---
# <a name="telnet-unset"></a>telnet： unset

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

关闭先前设置的选项。   

## <a name="syntax"></a>语法  
```  
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]  
```  
#### <a name="parameters"></a>参数  
|参数|说明|  
|-------|--------|  
|bsasdel|以**backspace**形式发送**backspace** 。|  
|crlf|以 CR 形式发送**Enter**键。 也称为 "换行符" 模式。|  
|delasbs|将**删除**作为**删除**发送。|  
|转义符|删除转义符设置。|  
|localecho|关闭 localecho。|  
|日志记录|关闭日志记录。|  
|ntlm|关闭 NTLM 身份验证。|  
|?|显示此命令的帮助。|  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
关闭日志记录。  
```  
u logging  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
