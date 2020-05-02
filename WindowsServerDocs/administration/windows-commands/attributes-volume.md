---
title: 属性数量
description: "\"属性\" 卷命令的参考主题，其中显示、设置或清除卷的属性。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e40e8284-3d57-4de8-a46c-e4ade34a0d53
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bbe1d66584216875daa82a7e250f3d2f525c2280
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719183"
---
# <a name="attributes-volume"></a>属性数量

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示、设置或清除卷的属性。

## <a name="syntax"></a>语法  

```
attributes volume [{set | clear}] [{hidden | readonly | nodefaultdriveletter | shadowcopy}] [noerr]  
```  
  
### <a name="parameters"></a>参数  
  
| 参数 | 描述 |  
| ------- | -------- |  
| set | 设置具有焦点的卷的指定属性。 |  
| clear | 清除具有焦点的卷的指定属性。 |  
| readonly | 指定该卷为只读状态。 |  
| 隐藏 | 指定该卷为隐藏状态。 |  
| nodefaultdriveletter | 指定该卷在默认情况下不会接收驱动器号。 |  
| shadowcopy | 指定该卷是一个卷影副本卷。 |  
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |  
  
### <a name="remarks"></a>备注  
  
- 在基本主启动记录（MBR）磁盘上，**隐藏**、**只读**和**nodefaultdriveletter**参数适用于磁盘上的所有卷。  
  
- 在基本 GUID 分区表（GPT）磁盘上，以及在动态 MBR 和 GPT 磁盘上，**隐藏**、**只读**和**nodefaultdriveletter**参数仅适用于所选卷。  
  
- 必须选择一个卷，才能使 "**属性" 卷**命令成功。 使用 "**选择音量**" 命令选择卷并将焦点移动到该卷。  
  
## <a name="examples"></a>示例

若要在所选卷上显示当前属性，请键入：  
  
```
attributes volume  
```  
  
若要将所选卷设置为隐藏和只读，请键入：  
  
```
attributes volume set hidden readonly  
```  
  
若要删除所选卷上的隐藏属性和只读属性，请键入：  
  
```
attributes volume clear hidden readonly  
```  
  
## <a name="additional-references"></a>其他参考  

- [命令行语法项](command-line-syntax-key.md)

- [选择卷命令](select-volume.md)
