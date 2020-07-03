---
title: create partition logical
description: Create partition 逻辑命令的参考文章，它在现有扩展分区中创建逻辑分区。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1f59b79a-d690-4d0e-ad38-40df5a0ce38e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4860f61d23c9ae51732c1fb0e127047c4944d2ed
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929675"
---
# <a name="create-partition-logical"></a>create partition logical

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在现有扩展分区中创建逻辑分区。 创建分区之后，焦点会自动转移到新分区上。

>[!IMPORTANT]
> 只能对主启动记录（MBR）磁盘使用此命令。 必须使用 "[选择磁盘](select-disk.md)" 命令选择基本 MBR 磁盘，并将焦点移动到该磁盘。
>
> 必须先创建[扩展分区](create-partition-extended.md)，然后才能创建逻辑驱动器。

## <a name="syntax"></a>语法

```
create partition logical [size=<n>] [offset=<n>] [align=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 大小 =`<n>` | 指定逻辑分区的大小（以兆字节（MB）为单位），该值必须小于扩展分区。 如果没有给定大小，则分区会一直继续，直到扩展分区中没有可用空间为止。 |
| offset =`<n>` | 指定在其中创建分区的偏移量（kb）。 偏移量向上舍入，以完全填充所使用的任何柱面大小。 如果未给出偏移量，则将该分区放置在可以足够容纳它的第一个磁盘区域中。 分区至少与**size = `<n>` **指定的数字一样长。 如果为逻辑分区指定大小，则它必须小于扩展分区。 |
| align =`<n>` | 将所有卷或分区区与最接近的对齐边界对齐。 通常与硬件 RAID 逻辑单元号（LUN）阵列一起使用以提高性能。 `<n>`从磁盘开始到最接近的对齐边界的千字节（KB）数。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

#### <a name="remarks"></a>备注

- 如果未指定**size**和**offset**参数，则会在扩展分区中可用的最大磁盘区中创建逻辑分区。

## <a name="examples"></a>示例

若要创建大小为 1000 mb 的逻辑分区，请在所选磁盘的扩展分区中键入：

```
create partition logical size=1000
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [create 命令](create.md)

- [select disk](select-disk.md)
