---
title: bdehdcfg 大小
description: Bdehdcfg size 命令的参考主题，它指定在创建新的系统驱动器时系统分区的大小。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 80f55b1d-a28d-4edf-9997-1fb918b7b5a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 27662a46045a8701b40697198cddf1dcb1b51c1e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718616"
---
# <a name="bdehdcfg-size"></a>bdehdcfg： size

指定在创建新的系统驱动器时的系统分区大小。 如果未指定大小，则该工具将使用默认值 300 MB。 系统驱动器的最小大小为 100 MB。 如果要将系统恢复或其他系统工具存储在系统分区上，则应相应地增加大小。

> [!NOTE]
> **Size**命令不能与`target <drive_letter> merge`命令组合。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink} -size <size_in_mb>
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<size_in_mb>` | 指示用于新分区的兆字节数（MB）。 |

## <a name="examples"></a>示例

将 500 MB 分配给默认系统驱动器：

```
bdehdcfg -target default -size 500
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
