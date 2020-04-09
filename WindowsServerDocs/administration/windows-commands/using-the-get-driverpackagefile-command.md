---
title: DriverPackageFile
description: 适用于 DriverPackageFile 的 Windows 命令主题，其中显示有关驱动程序包的信息，包括驱动程序包的驱动程序和文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d485a24479aa857270968a1bff7bd55a014347a3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831030"
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
| /InfFile：\<Inf 文件路径 > | 指定驱动程序包 .inf 文件的完整路径和文件名。 |
|    [/Architecture： {x86    |                                  ia64                                  |
|     [/Show： {驱动程序      |                                 Files                                  |

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要查看有关驱动程序文件的信息，请键入：
```
WDSUTIL /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)