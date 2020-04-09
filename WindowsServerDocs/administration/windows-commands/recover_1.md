---
title: recover
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8cc3a73d-9456-41a0-b375-2b4cc37c3992
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4c9b691b2f0cbad101f7caeb63011724dcf7594d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836570"
---
# <a name="recover"></a>recover



刷新磁盘组中所有磁盘的状态，尝试恢复无效磁盘组中的磁盘，并重新同步已过时的镜像卷和 RAID-5 卷。

> [!IMPORTANT]
> 在任何版本的 Windows Vista 中，此 DiskPart 命令均不可用。

## <a name="syntax"></a>语法

```
recover [noerr]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

-   此命令对磁盘组进行操作。
-   此命令仅适用于动态磁盘组。 如果对具有基本磁盘的组使用此命令，则不会返回错误，而不会执行任何操作。
-   此命令在失败或失败的磁盘上操作。 它还对失败、失败或处于失败状态的卷进行操作。
-   必须选择磁盘组中的磁盘，才能成功执行此命令。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要恢复包含焦点磁盘的磁盘组，请键入：
```
recover
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

