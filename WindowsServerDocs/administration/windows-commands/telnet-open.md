---
title: telnet 打开
description: Telnet open 的参考主题，它连接到 telnet 服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
s.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6c4529670ef934cfa19c9864ac59f5317eb2887a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721515"
---
# <a name="telnet-open"></a>telnet：打开

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

连接到 telnet 服务器。    

## <a name="syntax"></a>语法  
```  
o[pen] <hostname> [<Port>]  
```  
#### <a name="parameters"></a>参数  

| 参数  |                                        描述                                         |
|------------|--------------------------------------------------------------------------------------------|
| <hostname> |                         指定计算机名称或 IP 地址。                         |
|  [<Port>]  | 指定 telnet 服务器正在侦听的 TCP 端口。 默认值为 TCP 端口23。 |

## <a name="examples"></a>示例  
在 telnet.microsoft.com 连接到 telnet 服务器。  
```  
o telnet.microsoft.com  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
