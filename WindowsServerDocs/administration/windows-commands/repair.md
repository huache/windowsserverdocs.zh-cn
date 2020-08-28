---
title: 修复
description: "\"修复\" 命令的参考文章，可通过将故障磁盘区域替换为指定的动态磁盘来修复 RAID-5 卷。"
ms.topic: reference
ms.assetid: 9f84f661-f3cd-48c8-bf08-87819cf626fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a0768a82f2de22a424b4979aa8844e9fbb4f67e5
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027285"
---
# <a name="repair"></a>修复

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过将故障磁盘区域替换为指定的动态磁盘，修复具有焦点的 RAID-5 卷。

若要成功执行此操作，必须选择 RAID-5 阵列中的卷。 使用 " **选择音量** " 命令选择卷并将焦点移动到该卷。

## <a name="syntax"></a>语法

```
repair disk=<n> [align=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| 磁盘 =`<n>` | 指定将替换出现故障的磁盘区域的动态磁盘。 其中， *n* 的可用空间必须大于或等于 raid-5 卷中发生故障的磁盘区域的总大小。 |
| align =`<n>` | 将所有卷或分区区与最接近的对齐边界对齐。 其中， *n* 是从磁盘开始到最接近的对齐边界 (kb) 的千字节数。 |
| noerr | 仅用于脚本编写。 遇到错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

### <a name="examples"></a>示例

若要通过将其替换为动态磁盘4来替换具有焦点的卷，请键入：

```
repair disk=4
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [选择卷命令](select-volume.md)