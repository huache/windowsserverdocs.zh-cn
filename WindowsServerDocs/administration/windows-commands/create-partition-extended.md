---
title: create partition extended
description: Create partition 扩展命令的参考文章，用于在具有焦点的磁盘上创建扩展分区。
ms.topic: article
ms.assetid: 4ad7cb66-9c66-4153-b94e-1030a7225070
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7475eca6395c2f0cdc29fcadefe3bb8905761c99
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87879989"
---
# <a name="create-partition-extended"></a>create partition extended

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在具有焦点的磁盘上创建扩展分区。 创建分区之后，焦点会自动转移到新分区上。

>[!IMPORTANT]
> 只能在主启动记录上使用此命令 (MBR) 磁盘。 必须使用 "[选择磁盘](select-disk.md)" 命令选择基本 MBR 磁盘，并将焦点移动到该磁盘。
>
> 创建逻辑驱动器之前，必须创建扩展分区。 每个磁盘上只能创建一个扩展分区。 如果试图在其他扩展分区内创建扩展分区，则此命令会失败。

## <a name="syntax"></a>语法

```
create partition extended [size=<n>] [offset=<n>] [align=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 大小 =`<n>` | 指定分区的大小，以兆字节 (MB) 为单位。 如果没有给定大小，则分区会一直继续，直到扩展分区中没有可用空间为止。 |
| offset =`<n>` | 指定在其中创建分区 (KB) 的偏移量（kb）。 如果未给出偏移量，分区将从磁盘上可用空间的开始处开始，该空间足以容纳新的分区。 |
| align =`<n>` | 将所有分区区区对齐到最接近的对齐边界。 通常与硬件 RAID 逻辑单元号一起使用 (LUN) 阵列以提高性能。 `<n>`从磁盘开始到最接近的对齐边界 (KB) 的千字节数。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要创建大小为 1000 mb 的扩展分区，请键入：

```
create partition extended size=1000
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [create 命令](create.md)

- [select disk](select-disk.md)
