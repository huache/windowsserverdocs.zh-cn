---
title: ftp 引号
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1101dd6a5fa163df8d43d182e9d0dfe66e340b60
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725144"
---
# <a name="ftp-quote"></a>ftp：引用

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将原义参数发送到远程 ftp 服务器。 返回单个 ftp 答复代码。   
## <a name="syntax"></a>语法  
```  
quote <Argument>[ ]  
```  
#### <a name="parameters"></a>参数  

| 参数  |                    描述                    |
|------------|---------------------------------------------------|
| <Argument> | 指定要发送到 ftp 服务器的参数。 |

## <a name="remarks"></a>备注  
**Quote**命令与**文本**命令完全相同。  
## <a name="examples"></a>示例  
向远程 ftp 服务器发送**quit**命令。  
```  
quote quit  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp： literal_1](ftp-literal_1.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
