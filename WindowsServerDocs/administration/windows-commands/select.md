---
title: 选择
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9eeb40c0-4258-46e2-8dbc-94f63497e771
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f9ad7051978f4b509f54bf783f71943b65617bc7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834650"
---
# <a name="select"></a>选择



将焦点移到磁盘、分区、卷或虚拟硬盘（VHD）。

## <a name="syntax"></a>语法

```
select disk
select partition
select volume
select vdisk
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[选择磁盘](select-disk.md)|将焦点移到磁盘。|
|[选择分区](select-partition.md)|将焦点移到分区。|
|[选择卷](select-volume.md)|将焦点移至卷。|
|[选择 vdisk](select-vdisk.md)|将焦点移动到 VHD。|

## <a name="remarks"></a>备注

-   如果选择了包含相应分区的卷，则会自动选择该分区。
-   如果使用相应的卷选择了分区，则会自动选择该卷。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

