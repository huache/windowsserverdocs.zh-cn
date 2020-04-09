---
title: ftp 用户
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 29081bd8c5d537e1f060e4c848b720a60b4c8aea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842850"
---
# <a name="ftp-user"></a>ftp：用户

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定远程计算机的用户。   
## <a name="syntax"></a>语法  
```  
user <UserName> [<Password>] [<Account>]  
```  
#### <a name="parameters"></a>参数  

|  参数   |                                                                      说明                                                                      |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <UserName>  |                                          指定登录到远程计算机时使用的用户名。                                           |
| [<Password>] |               指定*用户名*的密码。 如果未指定密码，但需要密码， **ftp**会提示输入密码。               |
| [<Account>]  | 指定用于登录到远程计算机的帐户。 如果未指定*帐户*，但它是必需的，则**ftp**会提示输入帐户。 |

## <a name="examples"></a><a name=BKMK_Examples></a>示例  
指定包含密码 Password1 的 User1。  
```  
user User1 Password1  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
