---
title: 修复
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9f84f661-f3cd-48c8-bf08-87819cf626fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 89c09608e64b408db9c7c79269046195e005c187
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722394"
---
# <a name="repair"></a>修复

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过将故障\-磁盘区域替换为指定的动态磁盘，使用焦点修复 RAID 5 卷。  
  
  
  
## <a name="syntax"></a>语法  
  
```  
repair disk=<n> [align=<n>] [noerr]  
```  
  
### <a name="parameters"></a>参数  
  
| 参数  |                                                                                             描述                                                                                              |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 磁盘\=<n>  |                                                                 指定将替换出现故障的磁盘区域的动态磁盘。                                                                 |
| 垂直\=<n> |          将所有卷或分区区与最接近的对齐边界对齐。 *n*是从磁盘开始到\(最\)接近的对齐边界的 kb kb 数。           |
|   noerr    | 仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |
  
## <a name="remarks"></a>备注  
  
-   指定的动态磁盘的可用空间必须大于或等于 RAID\-5 卷中发生故障的磁盘区域的总大小。  
  
-   必须选择 RAID\-5 阵列中的卷，此操作才能成功。 使用 "**选择音量**" 命令选择卷并将焦点移动到该卷。  
  
## <a name="examples"></a>示例  
若要通过将其替换为动态磁盘4来替换具有焦点的卷，请键入：  
  
```  
repair disk=4  
```  
  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
  

  

