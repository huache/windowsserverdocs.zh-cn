---
title: 非活跃
description: 在基本主启动记录上将具有焦点的系统分区或启动分区标记为非活动的非活动命令的参考文章 (MBR) 磁盘。
ms.topic: reference
ms.assetid: f4fb4695-4e66-4166-b4ab-2c86a4605580
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 50b9145b809eb7a0f8605a27db97b2c7ac36d539
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037975"
---
# <a name="inactive"></a>非活跃

在基本主启动记录上将具有焦点的系统分区或启动分区标记为非活动状态 (MBR) 磁盘。

必须选择一个活动系统分区或启动分区，此操作才能成功。 使用 " [选择分区命令](select-partition.md) " 命令可选择活动分区，并将焦点移动到该分区。

> [!CAUTION]
> 若没有活动分区，计算机可能不会启动。 请勿将系统分区或启动分区标记为非活动，除非你是一个全面了解 Windows 系列操作系统的经验丰富的用户。<p>如果将系统分区或启动分区标记为非活动状态后无法启动计算机，请将 Windows 安装程序 CD 插入 cd-rom 驱动器中，重新启动计算机，然后使用恢复控制台中的 **fixmbr** 和 **fixboot** 命令修复该分区。
>
> 将系统分区或启动分区标记为非活动后，计算机将从 BIOS 中指定的下一个选项启动，例如 CD-ROM 驱动器或预启动执行环境 (PXE) 。

## <a name="syntax"></a>语法

```
inactive
```

### <a name="examples"></a>示例

```
inactive
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [选择分区命令](select-partition.md)

- [有关 Windows 启动问题的高级疑难解答](/windows/client-management/advanced-troubleshooting-boot-problems)
