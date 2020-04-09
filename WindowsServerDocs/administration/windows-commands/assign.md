---
title: assign
description: 用于**分配**的 Windows 命令主题，它将驱动器号或装入点分配给具有焦点的卷。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 57912b73-622e-489b-b053-a369021ba8e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4745b0472e2c8ee7a4034d9a06d395d6089db6f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851300"
---
# <a name="assign"></a>assign

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

给选中的卷分配一个驱动器号或装入点。

## <a name="syntax"></a>语法

```
assign [{letter=<d> | mount=<path>}] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `letter=<d>` | 要分配给卷的驱动器号。 |
| `mount=<path>` | 要分配给卷的装入点路径。 有关如何使用此命令的说明，请参阅[向驱动器分配装入点文件夹路径](https://go.microsoft.com/fwlink/?LinkId=207059)。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="remarks"></a>备注

- 如果未指定驱动器号或装载点，则将分配为下一个可用的驱动器号。 如果驱动器号或装入点正在使用，则会发生错误。

- 通过使用 assign 命令，可以更改与可移动驱动器关联的驱动器号。

- 无法将驱动器号分配给系统卷、启动卷或包含页面文件的卷。 此外，不能将驱动器号分配给原始设备制造商（OEM）分区或除基本数据分区以外的任何 GUID 分区表（gpt）分区。

- 必须选择卷，此操作才能成功。 使用 "**选择音量**" 命令选择卷并将焦点移动到该卷。

## <a name="examples"></a><a name=BKMK_examples></a>示例
若要将字母 E 分配给焦点的卷，请键入：
```
assign letter=e
```

## <a name="additional-references"></a>其他参考

- [命令行语法键]（command-line-syntax-key.md

