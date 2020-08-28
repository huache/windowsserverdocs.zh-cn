---
title: select
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 9eeb40c0-4258-46e2-8dbc-94f63497e771
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6fb6230c24f723e20b09449967b157dd86347202
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032219"
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

## <a name="remarks"></a>注解

-   如果选择了包含相应分区的卷，则会自动选择该分区。
-   如果使用相应的卷选择了分区，则会自动选择该卷。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

