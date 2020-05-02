---
title: expand
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 66de0488-a0c4-40c2-9b03-e40c107ba343
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b757f630e08249b1c716803a07cd9a163d7398d2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82725683"
---
# <a name="expand"></a>expand

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

展开一个或多个压缩文件。 可以使用此命令从分发磁盘中检索压缩的文件。  
## <a name="syntax"></a>语法  
```  
expand [/r] <source> <destination>  
expand /r <source> [<destination>]  
expand /i <source> [<destination>]  
expand /d <source>.cab [/f:<files>]  
expand <source>.cab /f:<files> <destination>  
```  
#### <a name="parameters"></a>参数  

|  参数  |                                                                                                                                                                   描述                                                                                                                                                                    |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     /r      |                                                                                                                                                             重命名展开的文件。                                                                                                                                                              |
|   source    |                                                                              指定要展开的文件。 *源*可以包含驱动器号和冒号、目录名称、文件名或它们的组合。 您可以使用通配符（**\\** \*或 **？**）。                                                                               |
| destination | 指定文件展开的位置。<p>如果*源*包含多个文件，并且你未指定 **/r**，则*目标*必须是目录。<p>*目标*可以包含驱动器号和冒号、目录名称、文件名或它们的组合。<p>目标文件 &#124; 路径规范。 |
|     /i      |                                                                                                   重命名扩展的文件，但忽略目录结构。<p>此参数适用于： Windows Server 2008 R2 和 Windows 7。                                                                                                    |
|     /d      |                                                                                                                              显示源位置中的文件列表。 不展开或解压缩文件。                                                                                                                              |
|     /f:     |                                                                                                                 指定 cab （.cab）文件中要展开的文件。 您可以使用通配符（**\\** \*或 **？**）。                                                                                                                 |
|     /?      |                                                                                                                                                       在命令提示符下显示帮助。                                                                                                                                                       |

## <a name="remarks"></a>备注  
- 在恢复控制台中使用**expand**  
  可从恢复控制台获取带有不同参数的**expand**命令。 有关恢复控制台的详细信息，请参阅 Microsoft 知识库中的[文章 314058](https://support.microsoft.com/kb/314058) 。  
  ## <a name="additional-references"></a>其他参考  
  - [命令行语法项](command-line-syntax-key.md)  
