---
title: ftp 重命名
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bbe159f2833ce52921b46e46881a1d7aed8c5df8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843020"
---
# <a name="ftp-rename"></a>ftp：重命名

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

重命名远程文件。   
## <a name="syntax"></a>语法  
```  
rename <FileName> <NewFileName>  
```  
#### <a name="parameters"></a>参数  

|   参数   |                 说明                 |
|---------------|---------------------------------------------|
|  <FileName>   | 指定要重命名的文件。 |
| <NewFileName> |        指定新的文件名。         |

## <a name="examples"></a><a name=BKMK_Examples></a>示例  
将远程文件**示例 .txt**重命名为**示例 1**  
```  
rename example.txt example1.txt  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
