---
title: bdehdcfg 目标
description: 适用于**bdehdcfg 目标**的 Windows 命令主题，用于准备要由 BitLocker 和 Windows 恢复用作系统驱动器的分区。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f761d25d-8349-4ac7-ac46-6bb340a4348f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d0f3e90fbb8725360cf8db335e79721e2328ab3a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851010"
---
# <a name="bdehdcfg-target"></a>bdehdcfg：目标

准备要由 BitLocker 和 Windows 恢复用作系统驱动器的分区。 默认情况下，创建此分区时没有驱动器号。

有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge}
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| default | 指示命令行工具将遵循与 BitLocker 安装向导相同的过程。 |
| 分配 | 使用磁盘上的未分配空间创建系统分区。 |
| `<DriveLetter>` 收缩 | 减少创建活动系统分区所需的驱动器数量。 若要使用此命令，指定的驱动器必须至少有5% 的可用空间。 |
| `<DriveLetter>` 合并 | 使用指定为活动系统分区的驱动器。 操作系统驱动器不能是合并目标。 |

## <a name="examples"></a><a name=BKMK_Examples></a>示例

以下示例描述了如何使用**target**命令将现有驱动器（P）指定为系统驱动器。

```
bdehdcfg -target P: merge
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Bdehdcfg](bdehdcfg.md)