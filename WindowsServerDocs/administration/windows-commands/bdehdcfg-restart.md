---
title: bdehdcfg restart
description: Bdehdcfg restart 命令的参考文章，它会告知 bdehdcfg 在驱动器准备结束后应重新启动计算机。
ms.topic: article
ms.assetid: a98b76bb-36f1-4790-b337-7dc35f606bc6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 67d2a3dd7b4304c26543840d6681b4ec6e655651
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87895099"
---
# <a name="bdehdcfg-restart"></a>bdehdcfg：重新启动

通知 bdehdcfg 命令行工具应在驱动器准备结束后重新启动计算机。 如果其他用户登录到计算机，但未指定**quiet**命令，则会出现一个提示，确认应重新启动计算机。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -restart
```

#### <a name="parameters"></a>参数

此命令没有其他参数。

## <a name="examples"></a>示例

使用**restart**命令：

```
bdehdcfg -target default -restart
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
