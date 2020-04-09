---
title: DriverPackage
description: DriverPackage 的 Windows 命令主题，用于向服务器中添加驱动程序包。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ac9e8d5-63ec-4ce8-86fc-85d28011050b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2ccdfcddd2f605eccd9cd32fed7b8c6921297fc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832010"
---
# <a name="add-driverpackage"></a>DriverPackage

向服务器中添加驱动程序包。

## <a name="syntax"></a>语法

```
WDSUTIL /Add-DriverPackage /InfFile:<Inf File path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>] [/Name:<Friendly Name>]
```

### <a name="parameters"></a>参数

|          参数           |                                                              说明                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|   InfFile：\<Inf 文件路径 >   |                                           指定要添加的 .inf 文件的完整路径。                                            |
|    /Server：\<Server name >    | 指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。 |
|      /Architecture： {x86      |                                                                 ia64                                                                  |
| [/DriverGroup：\<组名称 >] |                             指定应将包添加到的驱动程序组的名称。                              |
|   [/Name：\<友好名称 >]   |                                           指出驱动程序包的友好名称。                                            |

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要添加驱动程序包，请键入下列内容之一：
```
WDSUTIL /verbose /Add-DriverPackage /InfFile:C:\Temp\Display.inf
```
```
WDSUTIL /Add-DriverPackage /Server:MyWDSServer /InfFile:C:\Temp\Display.inf /Architecture:x86 /DriverGroup:x86Drivers /Name:Display Driver
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

