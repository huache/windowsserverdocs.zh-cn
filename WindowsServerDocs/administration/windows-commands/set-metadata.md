---
title: 设置元数据
description: 用于设置用于将卷影副本从一台计算机传输到另一台计算机的卷影创建元数据文件的名称和位置的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 683e54a7efc072d8709d6257771ba6bc5bde206e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721906"
---
# <a name="set-metadata"></a>设置元数据

设置用于将卷影副本从一台计算机传输到另一台计算机的卷影创建元数据文件的名称和位置。 如果在没有参数的情况下使用，则**设置元数据将**在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
set metadata [<Drive>:][<Path>]<MetaData.cab>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|[\<驱动器>：][<Path>]|指定元数据文件的创建位置。|
|\<MetaData .cab>|指定用于存储卷影创建元数据的 cab 文件的名称。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)