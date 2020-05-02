---
title: exit
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 23d1044b-f5c1-4180-ae6d-f553b48da4d9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e47dfa42f2bacb3fe9f12d1da9163bcf828e9488
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725708"
---
# <a name="exit"></a>exit

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

退出 Cmd.exe 程序（命令解释器）或当前批处理脚本。  
  
## <a name="syntax"></a>语法  
```  
exit [/b] [<exitCode>]  
```  
### <a name="parameters"></a>参数  

| 参数  |                                                                                         描述                                                                                          |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     /b     |                                      退出当前的批处理脚本，而不是退出 Cmd.exe。 如果从批处理脚本外部执行，则退出 Cmd.exe。                                      |
| `<exitCode>` | 指定数值。 如果指定了 **/b** ，则 ERRORLEVEL 环境变量设置为该数字。 如果要退出**cmd.exe**，进程退出代码将设置为该数字。 |
|     /?     |                                                                             在命令提示符下显示帮助。                                                                             |

## <a name="examples"></a>示例  
若要关闭命令解释器 Cmd.exe，请键入：  
```  
exit  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  

