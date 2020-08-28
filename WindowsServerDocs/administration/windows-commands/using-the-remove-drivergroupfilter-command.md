---
title: DriverGroupFilter
description: DriverGroupFilter 的参考文章，用于从服务器上的驱动程序组中删除筛选规则。
ms.topic: reference
ms.assetid: 837bd5d4-c79d-4714-942d-9875bd8e61dc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f71c43af8fdf8b8e07e4d5b2422f9c06af33b43d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023261"
---
# <a name="remove-drivergroupfilter"></a>DriverGroupFilter



从服务器上的驱动程序组中删除筛选规则。

## <a name="syntax"></a>语法

```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/DriverGroup:\<Group Name>|指定驱动程序组的名称。|
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|
|[/FilterType： \<FilterType> ]|指定要从组中删除的筛选器的类型。 \<FilterType> 可以是下列其中一项：</br>**BiosVendor**</br>**BiosVersion**</br>**ChassisType**</br>**Manufacturer**</br>**Uuid**</br>**OsVersion**</br>**OsEdition**</br>**OsLanguage**|

## <a name="examples"></a>示例

若要删除筛选器，请键入下列内容之一：
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer
```
```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /FilterType:OSLanguage
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)