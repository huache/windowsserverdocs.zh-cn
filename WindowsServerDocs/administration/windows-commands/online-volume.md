---
title: 联机卷
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5da073fd-578d-4691-ad0f-605ba66e0c7e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 476dd893e7899a2bd58336546a7881934f415f92
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837840"
---
# <a name="online-volume"></a>联机卷



使当前处于脱机状态的卷处于联机状态

> [!IMPORTANT]
> 此命令在任何版本的 Windows Vista 中都不可用。

> [!IMPORTANT]
> 如果在只读卷上使用此命令，则此命令将失败。

## <a name="syntax"></a>语法

```
online volume [noerr]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

-   此命令对已失败、发生故障或处于失败冗余状态的卷进行操作。
-   若要成功执行此命令，必须选择卷。 使用 "**选择音量**" 命令选择卷并将焦点移动到该卷。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将焦点置于联机状态，请键入：
```
online volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

