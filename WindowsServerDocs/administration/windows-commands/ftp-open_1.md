---
title: ftp open_1
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b61926a-dc60-4b4c-96d3-64e5c91c18ba vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 15a27d2f7512da352a0f4ddf02fa2511ffce7c1d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725198"
---
# <a name="ftp-open_1"></a>ftp： open_1

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

连接到指定的 ftp 服务器。   
## <a name="syntax"></a>语法  
```  
open <computer> [<Port>]  
```  
#### <a name="parameters"></a>参数  

| 参数  |                                           描述                                            |
|------------|--------------------------------------------------------------------------------------------------|
| <computer> |                指定您尝试连接到的远程计算机。                 |
|  [<Port>]  | 指定用于连接到 ftp 服务器的 TCP 端口号。 默认情况下，使用 TCP 端口21。 |

## <a name="remarks"></a>备注  
您可以使用 IP 地址或计算机名称（在这种情况下，DNS 服务器或主机文件必须可用）来指定**计算机**。  
## <a name="examples"></a>示例  
在**ftp.microsoft.com**连接到 ftp 服务器。  
```  
Open ftp.microsoft.com  
```  
在侦听 TCP 端口755的**ftp.microsoft.com**连接到 ftp 服务器。  
```  
open ftp.microsoft.com 755  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
