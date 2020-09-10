---
title: 设置元数据
description: 用于设置用于将卷影副本从一台计算机传输到另一台计算机的卷影创建元数据文件的名称和位置的参考文章。
ms.topic: reference
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b680ac538f7c2593871137b07d045ef150b68b1f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637681"
---
# <a name="set-metadata"></a>设置元数据

设置用于将卷影副本从一台计算机传输到另一台计算机的卷影创建元数据文件的名称和位置。 如果在没有参数的情况下使用，则 **设置元数据将** 在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
set metadata [<Drive>:][<Path>]<MetaData.cab>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[\<Drive>:][<Path>]|指定元数据文件的创建位置。|
|\<MetaData.cab>|指定用于存储卷影创建元数据的 cab 文件的名称。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)