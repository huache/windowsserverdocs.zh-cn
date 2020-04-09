---
title: convert basic
description: 用于转换 basic 的 Windows 命令主题，它将空的动态磁盘转换为基本磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 61329896-3b56-4959-8d58-45cbe18ba860
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8e0f6f5f04373042956d83bc9136c884c268e591
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847310"
---
# <a name="convert-basic"></a>convert basic

将空的动态磁盘转换为基本磁盘。

有关如何使用此命令的说明，请参阅[将动态磁盘改回为基本磁盘](https://go.microsoft.com/fwlink/?LinkId=207048)（ https://go.microsoft.com/fwlink/?LinkId=207048)。

## <a name="syntax"></a>语法

```
convert basic [noerr]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

> [!IMPORTANT]
> 若要将磁盘转换成基本磁盘，该磁盘必须为空。 转换磁盘之前，请备份数据，然后删除全部分区或卷。

-   若要成功执行此操作，必须选择一个动态磁盘。 使用 "**选择磁盘**" 命令选择动态磁盘并将焦点移动到该磁盘。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要将所选的动态磁盘转换为基本磁盘，请键入：
```
convert basic
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

