---
title: bdehdcfg newdriveletter
description: 适用于**bdehdcfg newdriveletter**的 Windows 命令主题，它将新的驱动器号分配给用作系统驱动器的驱动器部分。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f1f200a0-6850-4f0d-9047-f9f982a590f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a8757e7d0684912525817708fbe34953b049582
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851050"
---
# <a name="bdehdcfg-newdriveletter"></a>bdehdcfg： newdriveletter

将新的驱动器号分配给用作系统驱动器的驱动器部分。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -newdriveletter <DriveLetter>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------| ----------- |
|`<DriveLetter>`|定义将分配给指定的目标驱动器的驱动器号。|

## <a name="remarks"></a>备注

最佳做法是，建议不要将驱动器号分配给系统驱动器。

## <a name="examples"></a><a name="BKMK_Examples"></a>示例

以下示例显示了向默认驱动器分配驱动器号 P。

```
bdehdcfg -target default -newdriveletter P:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Bdehdcfg](bdehdcfg.md)