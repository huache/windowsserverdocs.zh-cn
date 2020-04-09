---
title: 活动
description: "\"**活动**\" 的 \"Windows 命令\" 主题（在基本磁盘上）会将焦点标记为 \"活动\"。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1f25da2e-87fc-4392-a7ee-f38d09b7873c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42f2e0d367344355e8f9a570f37cfbdc5dfc4590
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851370"
---
# <a name="active"></a>活动

在基本磁盘上，将选中的分区标记为活动的。

> [!CAUTION]
> DiskPart 只验证分区是否能够包含操作系统启动文件。 DiskPart 不检查分区内容。 如果错误地将某个分区标记为活动，并且它不包含操作系统启动文件，则您的计算机可能无法启动。

## <a name="syntax"></a>语法

```
active
```- 

## Remarks

-   This informs the basic input/output system (BIOS) or Extensible Firmware Interface (EFI) that the partition or volume is a valid system partition or system volume.

-   Only partitions can be marked as active.

-   A partition must be selected for this operation to succeed. Use the **select partition** command to select a partition and shift the focus to it.

## <a name=BKMK_examples></a>Examples

To mark the partition with focus as the active partition, type:

```
活动
```
## Additional References

- [Command-Line Syntax Key](command-line-syntax-key.md)