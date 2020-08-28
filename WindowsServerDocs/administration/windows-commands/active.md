---
title: 活动
description: 基本磁盘上的活动命令参考文章，将焦点标记为活动分区。
ms.topic: reference
ms.assetid: 1f25da2e-87fc-4392-a7ee-f38d09b7873c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6baad8bd60307eeddf7b777f059ab5ba3846e1d4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029473"
---
# <a name="active"></a>活动

在基本磁盘上，将选中的分区标记为活动的。 只能将分区标记为活动分区。 必须选择分区，此操作才能成功。 使用 " **选择分区** " 命令可选择分区，并将焦点移动到该分区。

> [!CAUTION]
> DiskPart 仅通知基本输入/输出系统 (BIOS) 或可扩展固件接口 (EFI) 分区或卷是有效的系统分区或系统卷，并且可以包含操作系统启动文件。 DiskPart 不检查分区内容。 如果错误地将某个分区标记为活动，并且它不包含操作系统启动文件，则您的计算机可能无法启动。

## <a name="syntax"></a>语法

```
active
```

## <a name="examples"></a>示例

若要将具有焦点的分区标记为活动分区，请键入：

```
active
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [选择分区命令](select-partition.md)
