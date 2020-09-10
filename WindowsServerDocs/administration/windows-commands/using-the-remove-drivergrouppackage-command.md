---
title: DriverGroupPackage
description: DriverGroupPackage 的参考文章，用于从服务器上的驱动程序组中删除驱动程序包。
ms.topic: reference
ms.assetid: 2e48616d-d6a4-45f0-a5c6-efe62bf6a0ed
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2cddeca84ba4993d8d77a4b55062d6ba4255abf9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635065"
---
# <a name="remove-drivergrouppackage"></a>DriverGroupPackage



从服务器上的驱动程序组中删除驱动程序包。

## <a name="syntax"></a>语法

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|
|[/DriverPackage： \<Name> ]|指定要删除的驱动程序包的名称。|
|[/PackageId： \<ID> ]|指定要删除的驱动程序包的 Windows 部署服务 ID。 如果无法按名称唯一地标识驱动程序包，则必须指定此选项。|

## <a name="examples"></a>示例

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /DriverPackage:XYZ
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)