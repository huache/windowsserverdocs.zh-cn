---
title: DriverPackage
description: DriverPackage 的参考文章，用于显示有关服务器上的驱动程序包的信息。
ms.topic: reference
ms.assetid: 94d231e4-ff01-48e7-9bc8-7b0d97a4339e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: aa8ce1a8a989dd5e3551a3beccd11944f237c6b5
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640091"
---
# <a name="get-driverpackage"></a>DriverPackage

显示有关服务器上的驱动程序包的信息。

## <a name="syntax"></a>语法

```
WDSUTIL /Get-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>} [/Show:{Drivers | Files | All}]
```

### <a name="parameters"></a>参数

|        参数         |                                                                           说明                                                                            |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server： \<Server name> ] |              指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。               |
| [/DriverPackage： \<Name> ] |                                                        指定要显示的驱动程序包的名称。                                                         |
|    [/PackageId： \<ID> ]    | 指定要显示的驱动程序包的 Windows 部署服务 ID。 如果无法按名称唯一地标识驱动程序包，则必须指定 ID。 |
|     [/Show： {驱动程序     |                                                                              文件                                                                               |

## <a name="examples"></a>示例

若要查看有关驱动程序包的信息，请键入下列内容之一：
```
WDSUTIL /Get-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Get-DriverPackage /DriverPackage:MyDriverPackage /Show:All
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)