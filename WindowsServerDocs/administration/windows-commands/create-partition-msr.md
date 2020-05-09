---
title: create partition msr
description: Create partition msr 的参考主题，它在 GUID 分区表（gpt）磁盘上创建 Microsoft 保留（MSR）分区。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 04fba033-23cb-4521-bd5d-db96131f2e73
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d427e9f96023f8b66f72e3895b30519ab7cd2de1
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993263"
---
# <a name="create-partition-msr"></a>create partition msr

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在 GUID 分区表（gpt）磁盘上创建 Microsoft 保留（MSR）分区。 每个 gpt 磁盘上都需要 Microsoft 保留分区。 此分区的大小取决于 gpt 磁盘的总大小。 Gpt 磁盘的大小必须至少为 32 MB 才能创建 Microsoft 保留分区。

> [!IMPORTANT]
> 使用此命令时要非常小心。 因为 gpt 磁盘需要特定分区布局，所以创建 Microsoft 保留分区可能会导致磁盘不可读。
>
> 若要成功执行此操作，必须选择一个基本 gpt 磁盘。 必须使用 "[选择磁盘](select-disk.md)" 命令选择基本 gpt 磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
create partition msr [size=<n>] [offset=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 大小 =`<n>` | 分区的大小，以兆字节（MB）为单位。 分区的字节数至少与指定的数字相同`<n>`。 如果未给出分区大小，则分区会一直继续，直至当前区域中没有可用空间为止。 |
| offset =`<n>` | 指定在其中创建分区的偏移量（kb）。 偏移量向上舍入，以完全填充所使用的任何扇区大小。 如果未给出偏移量，则将分区放置在能容纳它的第一个磁盘区域中。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

#### <a name="remarks"></a>备注

- 在用于启动 Windows 操作系统的 gpt 磁盘上，可扩展固件接口（EFI）系统分区是磁盘上的第一个分区，后跟 Microsoft 保留分区。 仅用于数据存储的 gpt 磁盘没有 EFI 系统分区，在这种情况下，Microsoft 保留分区为第一个分区。

- Windows 不会装载 Microsoft 保留分区。 不能在其中存储数据，也不能将其删除。

## <a name="examples"></a>示例

若要创建大小为 1000 mb 的 Microsoft 保留分区，请键入：

```
create partition msr size=1000
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [create 命令](create.md)

- [select disk](select-disk.md)
