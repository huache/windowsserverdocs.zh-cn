---
title: create partition extended
description: "\"创建分区\" 的 Windows 命令主题，用于在具有焦点的磁盘上创建扩展分区。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4ad7cb66-9c66-4153-b94e-1030a7225070
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7071ed16d8ddbd1e37c9dd49bac8bb2b032b0b24
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847070"
---
# <a name="create-partition-extended"></a>create partition extended

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在具有焦点的磁盘上创建扩展分区。 只能对主启动记录（MBR）磁盘使用此命令。

## <a name="syntax"></a>语法  
  
```  
create partition extended [size=<n>] [offset=<n>] [align=<n>] [noerr]  
```  
  
### <a name="parameters"></a>参数  
  
|  参数  |                                                                                                                             说明                                                                                                                              |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  大小\=<n>  |                                                  以 mb 为单位指定分区大小 \(MB\)。 如果没有给定大小，则分区会一直继续，直到扩展分区中没有可用空间为止。                                                  |
| 偏移量\=<n> |                     指定在其中创建分区 \(KB\)的偏移量（kb）。 如果未给出偏移量，分区将从磁盘上可用空间的开始处开始，该空间足以容纳新的分区。                      |
| 对齐\=<n>  | 将所有分区区区对齐到最接近的对齐边界。 通常与硬件 RAID 逻辑单元号一起使用 \(LUN\) 阵列以提高性能。 <n> 是从磁盘开始到最接近的对齐边界的 kb \(KB\) 数。 |
|    noerr    |                                 仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。                                 |
  
## <a name="remarks"></a>备注  
  
-   创建分区之后，焦点会自动转移到新分区上。  
  
-   每个磁盘上只能创建一个扩展分区。  
  
-   如果试图在其他扩展分区内创建扩展分区，则此命令会失败。  
  
-   创建逻辑驱动器之前，必须创建扩展分区。  
  
-   必须选择基本 MBR 磁盘，此操作才能成功。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。  
  
## <a name="examples"></a><a name=BKMK_examples></a>示例  
若要创建大小为 1000 mb 的扩展分区，请键入：  
  
```  
create partition extended size=1000  
```  
  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
  

  

