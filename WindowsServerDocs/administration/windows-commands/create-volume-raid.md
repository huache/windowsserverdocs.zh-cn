---
title: create volume raid
description: 使用三个或更多指定的动态磁盘创建一个 RAID-5 卷的卷 raid 的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9f257950-9240-4d5f-9537-8ad653d48ebf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 15a165439d0b19023fa5270eb372a17af8d558a4
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716936"
---
# <a name="create-volume-raid"></a>create volume raid

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用三个或更多指定的动态磁盘创建一个 RAID-5 卷。  

> [!IMPORTANT]  
> 在任何版本的 Windows Vista 中，此 DiskPart 命令均不可用。

## <a name="syntax"></a>语法  
  
```  
create volume raid [size=<n>] disk=<n>,<n>,<n>[,<n>,...] [align=<n>] [noerr]  
```  
  
### <a name="parameters"></a>参数  
  
|           参数           |                                                                                                                                                                                                                                              描述                                                                                                                                                                                                                                              |
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           规格\=<n>           | 卷在每个磁盘上占用的\(磁盘\)空间量（以 mb 为单位）。 如果没有给定大小，则将创建最大\-的 RAID 5 卷。 具有最小可用连续可用空间的磁盘确定 RAID\-5 卷的大小，并从每个磁盘分配相同的空间量。 RAID\-5 卷中的实际可用磁盘空间量小于磁盘空间的合并量，因为某些磁盘空间对于奇偶校验是必需的。 |
| disk\=<n>、<n><n>、\[、<n>,.。。\] |                                                                                                                                               要在其上创建 RAID\-5 卷的动态磁盘。 若要创建 RAID\-5 卷，至少需要三个动态磁盘。 在每个磁盘上分配**大小\=等于大小**的空间。                                                                                                                                                |
|          垂直\=<n>           |                                                                                                                   将所有卷区与最接近的对齐边界对齐。 通常与硬件 RAID 逻辑单元号\(LUN\)阵列一起使用以提高性能。 *n*是从磁盘开始到\(最\)接近的对齐边界的 kb kb 数。                                                                                                                   |
|             noerr             |                                                                                                                                                 仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。                                                                                                                                                  |
  
## <a name="remarks"></a>备注  
  
-   创建卷完成后，焦点会自动移到新卷。  
  
## <a name="examples"></a>示例  
若要创建大小\-为 1000 MB 的 RAID 5，请使用磁盘1、2和3，键入：  
  
```  
create volume raid size=1000 disk=1,2,3  
```  
  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
  

  

