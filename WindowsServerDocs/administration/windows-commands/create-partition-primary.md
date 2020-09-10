---
title: create partition primary
description: Create partition primary 命令的参考文章，用于在基本磁盘上创建具有焦点的主分区。
ms.topic: reference
ms.assetid: 6d652d8e-3935-4a91-8ced-b17c0e7937be
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 567dd32abc7b34bc6d5f9b4cbfb579672422df06
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629115"
---
# <a name="create-partition-primary"></a>create partition primary

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在基本磁盘上创建一个具有焦点的主分区。 创建分区之后，焦点会自动转移到新分区上。

> [!IMPORTANT]
> 若要成功执行此操作，必须选择基本磁盘。 必须使用 " [选择磁盘](select-disk.md) " 命令选择基本磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
create partition primary [size=<n>] [offset=<n>] [id={ <byte> | <guid> }] [align=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 大小 =`<n>` | 指定分区的大小，以兆字节 (MB) 为单位。 如果未给出分区大小，则分区会一直继续，直至当前区域中没有未分配空间为止。 |
| offset =`<n>` | 在其中创建分区 (KB) 的偏移量（kb）。 如果未给出偏移量，分区将从最大磁盘区的开头开始，该空间足以容纳它。 |
| align =`<n>` | 将所有分区区区对齐到最接近的对齐边界。 通常与硬件 RAID 逻辑单元号一起使用 (LUN) 阵列以提高性能。 `<n>` 从磁盘开始到最接近的对齐边界 (KB) 的千字节数。 |
| id = { `<byte>  | <guid>` } | 指定分区类型。 此参数适用于原始设备制造商 (OEM 仅) 使用。 任何分区类型 byte 或 GUID 都可以与此参数一起指定。 DiskPart 不会检查分区类型的有效性，这只是为了确保它是十六进制格式的字节或 GUID。 **警告：** 创建具有此参数的分区可能会导致计算机出现故障或无法启动。 除非你是使用 gpt 磁盘的 OEM 或 IT 专业人员，否则不要使用此参数在 gpt 磁盘上创建分区。 相反，请始终使用 [create partition efi](create-partition-efi.md) 命令创建 efi 系统分区，使用 [create partition Msr](create-partition-msr.md) 命令创建 Microsoft 保留分区，并使用 [create partition primary](create-partition-primary.md)) 命令 (不使用 `id={ <byte>  | <guid>` 参数) 在 gpt 磁盘上创建主分区。<p>**对于主启动记录 (MBR) 磁盘**，必须为分区指定以十六进制形式表示的分区类型字节。 如果未指定此参数，则命令将创建类型为的分区 `0x06` ，该分区指定未安装文件系统。 示例包括：<ul><li>**LDM 数据分区：** 0x42</li><li>**恢复分区：** 0x27</li><li>**可识别的 OEM 分区：** 0x12、0X84、0XDE、0XFE、0xA0</li></ul><p>**对于 GUID 分区表 (gpt) 磁盘**，可以为要创建的分区指定分区类型 GUID。 可识别的 Guid 包括：<ul><li>**EFI 系统分区：** c12a7328-f81f-11d2-ba4b-00a0c93ec93b</li><li>**Microsoft 保留分区：** e3c9e316-0b5c-4db8-817d-f92df00215ae</li><li>**基本数据分区：** ebd0a0a2-b9e5-4433-87c0-68b6b72699c7</li><li>**LDM 元数据分区 (动态磁盘) ：** 5808c8aa-7e8f-42e0-85d2-e1e90434cfb3</li><li>**LDM 数据分区 (动态磁盘) ：** af9b60a0-1431-4f62-bc68-3311714a69ad</li><li>**恢复分区：** de94bba4-06d1-4d40-a16a-bfd50179d6ac<p>如果没有为 gpt 磁盘指定此参数，则该命令将创建一个基本数据分区。</li></ul> |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有 noerr 参数，则错误会导致 DiskPart 退出并提供一个错误代码。 |

## <a name="examples"></a>示例

若要创建大小为 1000 mb 的主分区，请键入：

```
create partition primary size=1000
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [assign 命令](assign.md)

- [create 命令](create.md)

- [select disk](select-disk.md)
