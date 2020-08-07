---
title: bdehdcfg newdriveletter
description: Bdehdcfg newdriveletter 命令的参考文章，它将新的驱动器号分配给用作系统驱动器的驱动器部分。
ms.topic: article
ms.assetid: f1f200a0-6850-4f0d-9047-f9f982a590f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b13bae914f06af4b282ed558384c9cdc14f5bc11
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87895109"
---
# <a name="bdehdcfg-newdriveletter"></a>bdehdcfg： newdriveletter

将新的驱动器号分配给用作系统驱动器的驱动器部分。 作为最佳做法，我们建议不要将驱动器号分配给系统驱动器。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -newdriveletter <drive_letter>
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| ---------| ----------- |
| `<drive_letter>` | 定义将分配给指定的目标驱动器的驱动器号。 |

## <a name="examples"></a>示例

若要为默认驱动器分配驱动器号，请 `P` 执行以下操作：

```
bdehdcfg -target default -newdriveletter P:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
