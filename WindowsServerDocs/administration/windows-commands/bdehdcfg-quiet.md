---
title: bdehdcfg quiet
description: 适用于**bdehdcfg quiet**的 Windows 命令主题，它指示 bdehdcfg 不显示所有操作和错误。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7f75b702-890b-4ff9-805c-edf5cadd8822
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e9c24d8861476e6c1578af8245236d699b6ef6db
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851040"
---
# <a name="bdehdcfg-quiet"></a>bdehdcfg： quiet

通知 Bdehdcfg 命令行工具所有操作和错误不会显示在命令行界面中。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<DriveLetter> shrink|<DriveLetter> merge} -quiet
```

#### <a name="parameters"></a>参数

此命令不使用其他参数。

## <a name="remarks"></a>备注

如果在驱动器准备过程中显示 "是/否（Y/N）" 提示，则假定为 "是" 答案。 若要查看驱动器准备过程中出现的任何错误，请查看**DrivePreparationTool**事件提供程序下的系统事件日志。

## <a name="examples"></a><a name="BKMK_Examples"></a>示例

下面的示例演示如何使用**quiet**命令。

```
bdehdcfg -target default -quiet
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Bdehdcfg](bdehdcfg.md)