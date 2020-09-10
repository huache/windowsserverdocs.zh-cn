---
title: select
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 9eeb40c0-4258-46e2-8dbc-94f63497e771
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: da601731f9abe1f84f082fd91528db03e6a8b05a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639000"
---
# <a name="select"></a>select



将焦点移到磁盘、分区、卷或虚拟硬盘 (VHD) 。

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

