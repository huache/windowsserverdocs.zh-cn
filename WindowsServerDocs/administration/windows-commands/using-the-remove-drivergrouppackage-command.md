---
title: DriverGroupPackage
description: DriverGroupPackage 的参考主题，用于从服务器上的驱动程序组中删除驱动程序包。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2e48616d-d6a4-45f0-a5c6-efe62bf6a0ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c63c6ef0ed9af49506d80a715f23111bfd62070f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720402"
---
# <a name="remove-drivergrouppackage"></a>DriverGroupPackage



从服务器上的驱动程序组中删除驱动程序包。

## <a name="syntax"></a>语法

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|[/Server：\<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|
|[/DriverPackage：\<Name>]|指定要删除的驱动程序包的名称。|
|[/PackageId：\<ID>]|指定要删除的驱动程序包的 Windows 部署服务 ID。 如果无法按名称唯一地标识驱动程序包，则必须指定此选项。|

## <a name="examples"></a>示例

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /DriverPackage:XYZ
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)