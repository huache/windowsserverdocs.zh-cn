---
title: ftp 引号
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1bf13704150d602fbfa4e3b1a3fb1774d3bf7363
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843030"
---
# <a name="ftp-quote"></a>ftp：引用

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将原义参数发送到远程 ftp 服务器。 返回单个 ftp 答复代码。   
## <a name="syntax"></a>语法  
```  
quote <Argument>[ ]  
```  
#### <a name="parameters"></a>参数  

| 参数  |                    说明                    |
|------------|---------------------------------------------------|
| <Argument> | 指定要发送到 ftp 服务器的参数。 |

## <a name="remarks"></a>备注  
**Quote**命令与**文本**命令完全相同。  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
向远程 ftp 服务器发送**quit**命令。  
```  
quote quit  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： literal_1](ftp-literal_1.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
