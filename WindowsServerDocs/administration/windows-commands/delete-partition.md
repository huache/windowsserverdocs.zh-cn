---
title: delete partition
description: 用于删除分区的 Windows 命令主题，用于删除具有焦点的分区。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 65752312-cb16-46f6-870f-1b95c507b101
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a24c18cf98f2899fbb57f1f5f2d2776824d637b7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846570"
---
# <a name="delete-partition"></a>delete partition

删除具有焦点的分区。

## <a name="syntax"></a>语法

```
delete partition [noerr] [override]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|override|允许 DiskPart 删除任何类型的分区。 通常，DiskPart 只允许删除已知的数据分区。|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

> [!CAUTION]
> 删除动态磁盘上的分区可能会删除该磁盘上的所有动态卷，因而会销毁所有数据，并使磁盘处于损坏状态。 若要删除动态卷，请始终改用**delete volume**命令。 可以从动态磁盘中删除分区，但不应创建分区。 例如，可以删除动态 GPT 磁盘上的未识别的 GUID 分区表 (GPT) 分区。 删除此类分区不会导致生成的可用空间可用。 此命令旨在允许在不能使用 DiskPart 中的**clean**命令的紧急情况下，reclame 损坏的脱机动态磁盘上的空间。
> -   不能删除系统分区、启动分区或任何包含活动页面文件或故障转储信息的分区。
> -   必须选择分区，此操作才能成功。 使用 "**选择分区**" 命令可选择分区，并将焦点移动到该分区。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要删除具有焦点的分区，请键入：
```
delete partition
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

