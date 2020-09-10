---
title: DriverGroup
description: DriverGroup 的参考文章，用于显示有关服务器上的驱动程序组的信息。
ms.topic: reference
ms.assetid: 7cfe10c3-a63f-48e7-bef9-f6b474b4ddbe
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ec0341403140a0aaab2ec43dab960e81935cefa8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622569"
---
# <a name="get-drivergroup"></a>DriverGroup

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关服务器上的驱动程序组的信息。

## <a name="syntax"></a>语法
```
wdsutil /Get-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/DriverGroup:<Group Name>|指定驱动程序组的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。  如果未指定服务器名称，则使用本地服务器。|
|[/Show： {PackageMetaData &#124; 筛选器 &#124; All}]|显示指定组中所有驱动程序包的元数据。 **PackageMetaData** 显示有关驱动程序组的所有筛选器的信息。 **筛选器** 显示组的所有驱动程序包和筛选器的元数据。|
## <a name="examples"></a>示例
若要查看有关驱动程序文件的信息，请键入：
```
wdsutil /Get-DriverGroup /DriverGroup:printerdrivers /Show:PackageMetaData
```
```
wdsutil /Get-DriverGroup /DriverGroup:printerdrivers /Server:MyWdsServer /Show:Filters
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllDriverGroups 命令](using-the-get-alldrivergroups-command.md)
