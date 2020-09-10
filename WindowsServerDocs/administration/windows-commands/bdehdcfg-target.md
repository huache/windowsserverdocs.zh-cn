---
title: bdehdcfg target
description: Bdehdcfg 目标命令的参考文章，用于准备要由 BitLocker 和 Windows 恢复用作系统驱动器的分区。
ms.topic: reference
ms.assetid: f761d25d-8349-4ac7-ac46-6bb340a4348f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7cc13e3c224aa1af944c5e9c9550737addcb6980
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632817"
---
# <a name="bdehdcfg-target"></a>bdehdcfg：目标

准备要由 BitLocker 和 Windows 恢复用作系统驱动器的分区。 默认情况下，创建此分区时没有驱动器号。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge}
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| default | 指示命令行工具将遵循与 BitLocker 安装向导相同的过程。 |
| 分配 | 使用磁盘上的未分配空间创建系统分区。 |
| `<drive_letter>` 收缩 | 减少创建活动系统分区所需的驱动器数量。 若要使用此命令，指定的驱动器必须至少有5% 的可用空间。 |
| `<drive_letter>` merge | 使用指定为活动系统分区的驱动器。 操作系统驱动器不能是合并目标。 |

## <a name="examples"></a>示例

若要指定现有驱动器 (P) 作为系统驱动器：

```
bdehdcfg -target P: merge
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
