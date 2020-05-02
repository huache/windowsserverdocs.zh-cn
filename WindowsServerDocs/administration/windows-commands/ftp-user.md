---
title: ftp 用户
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cb4f0f47f23bec312c57266479c261c96535e8cc
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725068"
---
# <a name="ftp-user"></a>ftp：用户

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

指定远程计算机的用户。   
## <a name="syntax"></a>语法  
```  
user <UserName> [<Password>] [<Account>]  
```  
#### <a name="parameters"></a>参数  

|  参数   |                                                                      描述                                                                      |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <UserName>  |                                          指定登录到远程计算机时使用的用户名。                                           |
| [<Password>] |               指定*用户名*的密码。 如果未指定密码，但需要密码， **ftp**会提示输入密码。               |
| [<Account>]  | 指定用于登录到远程计算机的帐户。 如果未指定*帐户*，但它是必需的，则**ftp**会提示输入帐户。 |

## <a name="examples"></a>示例  
指定包含密码 Password1 的 User1。  
```  
user User1 Password1  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
