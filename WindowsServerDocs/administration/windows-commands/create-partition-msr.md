---
title: create partition msr
description: 创建分区 msr 的参考文章，它在 GUID 分区表 (gpt) 磁盘上创建 Microsoft 保留 (MSR) 分区。
ms.topic: reference
ms.assetid: 04fba033-23cb-4521-bd5d-db96131f2e73
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 25187f6bfee63b7b7b39519db9eddd82900a19c3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629123"
---
# <a name="create-partition-msr"></a>create partition msr

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在 GUID 分区表 (gpt) 磁盘上创建 Microsoft 保留 (MSR) 分区。 每个 gpt 磁盘上都需要 Microsoft 保留分区。 此分区的大小取决于 gpt 磁盘的总大小。 Gpt 磁盘的大小必须至少为 32 MB 才能创建 Microsoft 保留分区。

> [!IMPORTANT]
> 使用此命令时要非常小心。 因为 gpt 磁盘需要特定分区布局，所以创建 Microsoft 保留分区可能会导致磁盘不可读。
>
> 若要成功执行此操作，必须选择一个基本 gpt 磁盘。 必须使用 " [选择磁盘](select-disk.md) " 命令选择基本 gpt 磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
create partition msr [size=<n>] [offset=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 大小 =`<n>` | 分区大小以 mb (MB) 为单位。 分区的字节数至少与指定的数字相同 `<n>` 。 如果未给出分区大小，则分区会一直继续，直至当前区域中没有可用空间为止。 |
| offset =`<n>` | 指定在其中创建分区 (KB) 的偏移量（kb）。 偏移量向上舍入，以完全填充所使用的任何扇区大小。 如果未给出偏移量，则将分区放置在能容纳它的第一个磁盘区域中。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

#### <a name="remarks"></a>备注

- 在用于启动 Windows 操作系统的 gpt 磁盘上，可扩展固件接口 (EFI) 系统分区是磁盘上的第一个分区，后跟 Microsoft 保留分区。 仅用于数据存储的 gpt 磁盘没有 EFI 系统分区，在这种情况下，Microsoft 保留分区为第一个分区。

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
