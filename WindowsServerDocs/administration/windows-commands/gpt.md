---
title: gpt
description: Gpt 命令的参考文章，它将 gpt 属性分配给具有焦点的分区。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1d6f9029-807f-4420-a336-36669b5361bc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 40d3536f5a6be0bf520095e3ba61f75b7a2addc7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924614"
---
# <a name="gpt"></a>gpt

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在基本 GUID 分区表（gpt）磁盘上，此命令将 gpt 属性分配给具有焦点的分区。 Gpt 分区属性给出了有关分区使用的其他信息。 一些属性特定于分区类型 GUID。

你必须选择一个基本 gpt 分区，此操作才能成功。 使用 "[选择分区" 命令](select-partition.md)可选择基本 gpt 分区，并将焦点移动到该分区。

> [!CAUTION]
> 更改 gpt 属性可能会导致基本数据卷无法分配驱动器号，或阻止文件系统安装。 我们强烈建议您不要更改 gpt 属性，除非您是原始设备制造商（OEM）或使用 gpt 磁盘经验丰富的 IT 专业人员。

## <a name="syntax"></a>语法

```
gpt attributes=<n>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 属性 =`<n>` | 指定要应用于具有焦点的分区的属性的值。 "Gpt 属性" 字段是包含两个子字段的64位字段。 较大的字段只能在分区 ID 的上下文中解释, 而较小的字段常用于所有分区 ID。 接受的值包括：<ul><li>**0x0000000000000001** -指定计算机正确运行所需的分区。</li><li>**0x8000000000000000** -指定在将磁盘移到另一台计算机时，或在计算机首次看到磁盘时，分区不会接收驱动器号。</li><li>**0x4000000000000000** -隐藏分区的卷，使其不会被装载管理器检测到。</li><li>**0x2000000000000000** -指定分区为另一分区的卷影副本。</li><li>**0x1000000000000000** -指定分区为只读。 此属性可防止将卷写入到中。</li></ul><p>有关这些属性的详细信息，请参阅 "属性" 部分的[Create_PARTITION_PARAMETERS 结构](https://docs.microsoft.com/windows/win32/api/vds/ns-vds-create_partition_parameters)。 |

#### <a name="remarks"></a>备注

- EFI 系统分区只包含启动操作系统所需的二进制文件。 这使特定于操作系统的 OEM 二进制文件或二进制文件可以放在其他分区中。

### <a name="examples"></a>示例

若要防止计算机自动向分区分配驱动器号，请在移动 gpt 磁盘时，键入：

```
gpt attributes=0x8000000000000000
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [选择分区命令](select-partition.md)

- [create_PARTITION_PARAMETERS 结构](https://docs.microsoft.com/windows/win32/api/vds/ns-vds-create_partition_parameters)
