---
title: ftp literal_1
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f502bb56c94734870962f56cfb85dcc17ddc3f93
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843390"
---
# <a name="ftp-literal_1"></a>ftp： literal_1

>适用于： Windows Server （半年频道），Windows Server 2016，Windows Server 2012 R2，Windows Server 2012 将原义参数发送到远程 ftp 服务器。 返回单个 ftp 答复代码。   

## <a name="syntax"></a>语法  
```  
literal <Argument> [ ]  
```  
#### <a name="parameters"></a>参数  

| 参数  |                    说明                    |
|------------|---------------------------------------------------|
| <Argument> | 指定要发送到 ftp 服务器的参数。 |

## <a name="remarks"></a>备注  
**文本**命令与**引号**命令完全相同。  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
向远程 ftp 服务器发送**quit**命令。  
```  
literal quit  
```  
## <a name="additional-references"></a>其他参考  
-   [ftp：引用](ftp-quote.md)  
-   - [命令行语法项](command-line-syntax-key.md)  
