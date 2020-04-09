---
title: create volume simple
description: 创建卷 simple 的 Windows 命令主题，可在指定的动态磁盘上创建简单卷。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da0f208d-7fda-471a-9db2-5de5ba5207c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45c707a92692c5531a0e33c9537705558f2ac309
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846890"
---
# <a name="create-volume-simple"></a>create volume simple

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在指定的动态磁盘上创建简单卷。  
  
> [!IMPORTANT]  
> 对于 Windows Vista，此 DiskPart 命令仅适用于 Windows Vista 旗舰版、Windows Vista Enterprise 和 Windows Vista 商业版。
  
## <a name="syntax"></a>语法  
  
```  
create volume simple [size=<n>] [disk=<n>] [align=<n>] [noerr]  
```  
  
### <a name="parameters"></a>参数  
  
| 参数  |                                                                                                                            说明                                                                                                                            |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 大小\=<n>  |                                                                  卷的大小（以 mb 为单位） \(MB\)。 如果未指定卷大小，新建的卷就占用磁盘上剩余的可用空间。                                                                   |
| 磁盘\=<n>  |                                                                                创建卷的动态磁盘。 如果未指定磁盘，则使用当前磁盘。                                                                                |
| 对齐\=<n> | 将所有卷区与最接近的对齐边界对齐。 通常与硬件 RAID 逻辑单元号一起使用 \(LUN\) 阵列以提高性能。 *n*是从磁盘开始到最接近的对齐边界 \(kb\) 的千字节数。 |
|   noerr    |                               仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。                                |
  
## <a name="remarks"></a>备注  
  
-   创建卷完成后，焦点会自动移到新卷。  
  
## <a name="examples"></a><a name=BKMK_examples></a>示例  
若要创建大小为 1000 mb 的卷，请在磁盘1上键入：  
  
```  
create volume simple size=1000 disk=1  
```  
  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
  

  

