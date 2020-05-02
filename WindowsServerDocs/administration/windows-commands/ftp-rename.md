---
title: ftp 重命名
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5dc5006c82df8417a8652a9c0ba20f7f1a002e7f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725118"
---
# <a name="ftp-rename"></a>ftp：重命名

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

重命名远程文件。   
## <a name="syntax"></a>语法  
```  
rename <FileName> <NewFileName>  
```  
#### <a name="parameters"></a>参数  

|   参数   |                 描述                 |
|---------------|---------------------------------------------|
|  <FileName>   | 指定要重命名的文件。 |
| <NewFileName> |        指定新的文件名。         |

## <a name="examples"></a>示例  
将远程文件**示例 .txt**重命名为**示例 1**  
```  
rename example.txt example1.txt  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
