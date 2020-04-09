---
title: bdehdcfg 重新启动
description: 用于**bdehdcfg restart**的 Windows 命令主题，它会告知 bdehdcfg 在驱动器准备结束后应重新启动计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a98b76bb-36f1-4790-b337-7dc35f606bc6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ae6f8d31c09feddf8f994c28d34e4e1b08cc322
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851030"
---
# <a name="bdehdcfg-restart"></a>bdehdcfg：重新启动

通知 Bdehdcfg 命令行工具应在驱动器准备结束后重新启动计算机。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -restart
```

#### <a name="parameters"></a>参数

此命令不使用其他参数。

## <a name="remarks"></a>备注

如果其他用户登录到计算机，但未指定**quiet**命令，则将显示一条提示，确认应重新启动计算机。

## <a name="examples"></a><a name="BKMK_Examples"></a>示例

下面的示例演示如何使用**restart**命令。

```
bdehdcfg -target default -restart
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Bdehdcfg](bdehdcfg.md)