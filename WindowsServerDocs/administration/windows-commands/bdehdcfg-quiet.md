---
title: bdehdcfg quiet
description: Bdehdcfg quiet 命令的参考文章，它指示 bdehdcfg 不显示所有操作和错误。
ms.topic: article
ms.assetid: 7f75b702-890b-4ff9-805c-edf5cadd8822
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7ddd6e2cb63b6af0ea0c50b5260436c184ee6aa6
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87895089"
---
# <a name="bdehdcfg-quiet"></a>bdehdcfg： quiet

通知 bdehdcfg 命令行工具所有操作和错误不会显示在命令行界面中。 在驱动器准备过程中显示的任何 "是/否 (Y/N) 提示将假定为" 是 "。 若要查看驱动器准备过程中出现的任何错误，请查看**DrivePreparationTool**事件提供程序下的系统事件日志。

## <a name="syntax"></a>语法

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -quiet
```

#### <a name="parameters"></a>参数

此命令没有其他参数。

## <a name="examples"></a>示例

使用**quiet**命令：

```
bdehdcfg -target default -quiet
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
