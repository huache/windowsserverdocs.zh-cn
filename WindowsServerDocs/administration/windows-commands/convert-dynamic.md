---
title: convert dynamic
description: 用于转换动态的 Windows 命令主题，将基本磁盘转换为动态磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7b8fa4b1-850f-4e48-b05f-871c883ea33c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6ad84cf2ecb6808b68110187b52f3fc13590b491
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847320"
---
# <a name="convert-dynamic"></a>convert dynamic

将基本磁盘转换为动态磁盘。

有关如何使用此命令的说明，请参阅[将基本磁盘更改为动态磁盘](https://go.microsoft.com/fwlink/?LinkId=207047)（ https://go.microsoft.com/fwlink/?LinkId=207047)。

## <a name="syntax"></a>语法

```
convert dynamic [noerr]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

-   基本磁盘上的任何现有分区都将成为简单卷。
-   若要成功执行此操作，必须选择基本磁盘。 使用 "**选择磁盘**" 命令选择基本磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将基本磁盘转换为动态磁盘，请键入：
```
convert dynamic
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

