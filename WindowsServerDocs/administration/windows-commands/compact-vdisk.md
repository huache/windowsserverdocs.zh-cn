---
title: compact vdisk
description: Compact vdisk 命令的参考文章，可减少动态扩展虚拟硬盘（VHD）文件的物理大小。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 40ca0820-67de-4160-b62a-e9bf63fe2790
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7379975981c2df386b7180c814799f7129eee7da
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929057"
---
# <a name="compact-vdisk"></a>compact vdisk

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

减小动态扩展虚拟硬盘（VHD）文件的物理大小。 此参数非常有用，因为在添加文件时动态扩展 Vhd 大小增加，但在删除文件时，其大小不会自动减小。

## <a name="syntax"></a>语法

```
compact vdisk
```

### <a name="remarks"></a>备注

- 若要成功执行此操作，必须选择动态扩展的 VHD。 使用 "[选择 vdisk" 命令](select-vdisk.md)选择 VHD 并将焦点移动到该 VHD。

- 只能使用分离或附加为只读的压缩动态扩展 Vhd。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [附加 vdisk 命令](attach-vdisk.md)

- [detail vdisk 命令](detail-vdisk.md)

- [分离 vdisk 命令](detach-vdisk.md)

- [展开 vdisk 命令](expand-vdisk.md)

- [Merge vdisk 命令](merge-vdisk.md)

- [选择 vdisk 命令](select-vdisk.md)

- [list 命令](list.md)
