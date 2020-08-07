---
title: compact vdisk
description: Compact vdisk 命令的参考文章，可减小动态扩展虚拟硬盘 (VHD) 文件的物理大小。
ms.topic: article
ms.assetid: 40ca0820-67de-4160-b62a-e9bf63fe2790
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0e8f29cf7188d2630f15bee9bde2910c64f325b5
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892623"
---
# <a name="compact-vdisk"></a>compact vdisk

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

减小动态扩展虚拟硬盘 (VHD) 文件的物理大小。 此参数非常有用，因为在添加文件时动态扩展 Vhd 大小增加，但在删除文件时，其大小不会自动减小。

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
