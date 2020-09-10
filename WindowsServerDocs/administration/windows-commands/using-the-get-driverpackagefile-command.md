---
title: DriverPackageFile
description: DriverPackageFile 的参考文章，其中显示了有关驱动程序包的信息，其中包括驱动程序包包含的驱动程序和文件。
ms.topic: reference
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9ab52e1040651398d4789ea51ef9b6dc40dc6d54
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624627"
---
# <a name="get-driverpackagefile"></a>DriverPackageFile

显示有关驱动程序包的信息，包括其包含的驱动程序和文件。

## <a name="syntax"></a>语法

```
WDSUTIL /Get-DriverPackageFile /InfFile:<Inf File path> [/Architecture:{x86 | ia64 | x64}] [/Show:{Drivers | Files | All}]
```

### <a name="parameters"></a>参数

|         参数         |                              说明                               |
|---------------------------|------------------------------------------------------------------------|
| /InfFile:\<Inf File path> | 指定驱动程序包 .inf 文件的完整路径和文件名。 |
|    [/Architecture： {x86    |                                  ia64                                  |
|     [/Show： {驱动程序      |                                 文件                                  |

## <a name="examples"></a>示例

若要查看有关驱动程序文件的信息，请键入：
```
WDSUTIL /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)