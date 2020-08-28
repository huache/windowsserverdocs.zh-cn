---
title: bdehdcfg size
description: Bdehdcfg size 命令的参考文章，它指定在创建新系统驱动器时系统分区的大小。
ms.topic: reference
ms.assetid: 80f55b1d-a28d-4edf-9997-1fb918b7b5a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f4aaedbbac5783fdf54814d7cf97ef9c70c9d346
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031475"
---
# <a name="bdehdcfg-size"></a>bdehdcfg： size

指定在创建新的系统驱动器时的系统分区大小。 如果未指定大小，则该工具将使用默认值 300 MB。 系统驱动器的最小大小为 100 MB。 如果要将系统恢复或其他系统工具存储在系统分区上，则应相应地增加大小。

> [!NOTE]
> **Size**命令不能与 `target <drive_letter> merge` 命令组合。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink} -size <size_in_mb>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<size_in_mb>` | 指示用于新分区的兆字节 (MB) 数。 |

## <a name="examples"></a>示例

将 500 MB 分配给默认系统驱动器：

```
bdehdcfg -target default -size 500
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
