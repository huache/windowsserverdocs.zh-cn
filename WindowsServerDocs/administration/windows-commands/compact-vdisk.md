---
title: compact vdisk
description: Windows 命令主题 forcompact vdisk，它可减少动态扩展虚拟硬盘（VHD）文件的物理大小。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 40ca0820-67de-4160-b62a-e9bf63fe2790
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9691be21c188fbc2c3b2e782acde127270decf56
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847420"
---
# <a name="compact-vdisk"></a>compact vdisk

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

减小动态扩展虚拟硬盘（VHD）文件的物理大小。 此参数非常有用，因为在添加文件时动态扩展 Vhd 大小增加，但在删除文件时，其大小不会自动减小。

> [!NOTE]
> 此命令仅适用于 Windows 7 和 Windows Server 2008 R2。

## <a name="syntax"></a>语法
```
compact vdisk
```

## <a name="remarks"></a>备注

- 若要成功执行此操作，必须选择动态扩展的 VHD。 使用 "**选择 vdisk** " 命令选择 VHD 并将焦点移动到该 VHD。

- 只能压缩已分离或附加为只读的已动态扩展 Vhd。

## <a name="examples"></a><a name=BKMK_Examples></a>示例
若要压缩动态扩展的 VHD，请键入：
```
compact vdisk
```

## <a name="additional-references"></a>其他参考
- - [命令行语法项](command-line-syntax-key.md)
- [附加 vdisk](attach-vdisk.md)
- [详细信息 vdisk](detail-vdisk.md)
- [分离 vdisk](detach-vdisk.md)
- [展开 vdisk](expand-vdisk.md)
- [Merge vdisk](merge-vdisk.md)
- [选择 vdisk](select-vdisk.md)
- [list_1](list_1.md)
