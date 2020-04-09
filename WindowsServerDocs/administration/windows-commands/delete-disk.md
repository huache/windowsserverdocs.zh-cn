---
title: delete disk
description: 用于删除磁盘的 Windows 命令主题，它从磁盘列表中删除丢失的动态磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 44079900-e4ed-49d0-81e4-d652c38cd636
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1a767e0689d5fbabb193df37528a0909ab63a1ab
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846650"
---
# <a name="delete-disk"></a>delete disk

从磁盘列表中删除丢失的动态磁盘。

有关如何使用此命令的说明，请参阅[删除丢失的动态磁盘](https://go.microsoft.com/fwlink/?LinkId=207055)（ https://go.microsoft.com/fwlink/?LinkId=207055)。

## <a name="syntax"></a>语法

```
delete disk [noerr] [override]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|
|override|允许 DiskPart 删除磁盘上的所有简单卷。 如果磁盘上包含半个镜像卷，则磁盘上的这半个镜像将被删除。 如果磁盘是 RAID-5 卷的一个成员，则 delete disk override 命令无效。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要从磁盘列表中删除丢失的动态磁盘，请键入：
```
delete disk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

