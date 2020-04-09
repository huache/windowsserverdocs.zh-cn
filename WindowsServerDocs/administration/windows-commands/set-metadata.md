---
title: 设置元数据
description: 用于设置元数据的 Windows 命令主题，用于设置用于将卷影副本从一台计算机传输到另一台计算机的卷影创建元数据文件的名称和位置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5bd728650cf163f98a82ff1e6f88755c4cc1aea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834520"
---
# <a name="set-metadata"></a>设置元数据

设置用于将卷影副本从一台计算机传输到另一台计算机的卷影创建元数据文件的名称和位置。 如果在没有参数的情况下使用，则**设置元数据将**在命令提示符下显示帮助。

## <a name="syntax"></a>语法

```
set metadata [<Drive>:][<Path>]<MetaData.cab>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[\<驱动器 >：][<Path>]|指定元数据文件的创建位置。|
|\<元数据 .cab >|指定用于存储卷影创建元数据的 cab 文件的名称。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)