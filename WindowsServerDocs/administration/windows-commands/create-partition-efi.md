---
title: create partition efi
description: Windows 命令主题，用于创建分区 efi，这会在基于 Itanium 的计算机上的 GUID 分区表（gpt）磁盘上创建可扩展固件接口（EFI）系统分区。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3cfc1fca-6515-4a4d-bfae-615fa8045ea9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a1c61f103fc719c8144e942f64172e3be554a414
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847040"
---
# <a name="create-partition-efi"></a>create partition efi

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在基于 Itanium 的计算机上，在 GUID 分区表（gpt）磁盘上创建可扩展固件接口（EFI）系统分区。

## <a name="syntax"></a>语法  
  
```  
create partition efi [size=<n>] [offset=<n>] [noerr]  
```  
  
### <a name="parameters"></a>参数  
  
|  参数  |                                                                                             说明                                                                                              |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  大小\=<n>  |                         分区大小以 mb \(MB\)为单位。 如果未给出分区大小，则分区会一直继续，直至当前区域中没有可用空间为止。                         |
| 偏移量\=<n> |             在其中创建分区 \(KB\)的偏移量（kb）。 如果未给出偏移量，则将分区放置在能容纳它的第一个磁盘区域中。              |
|    noerr    | 仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |
  
## <a name="remarks"></a>备注  
  
-   创建分区后，将选中该新分区。  
  
-   若要成功执行此操作，必须选择 gpt 磁盘。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。  
  
## <a name="examples"></a><a name=BKMK_examples></a>示例  
若要在所选磁盘上创建 1000 mb 的 EFI 分区，请键入：  
  
```  
create partition efi size=1000  
```  
  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
  

  

