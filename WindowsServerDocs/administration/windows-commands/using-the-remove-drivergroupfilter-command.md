---
title: DriverGroupFilter
description: DriverGroupFilter 的参考主题，用于从服务器上的驱动程序组中删除筛选规则。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 837bd5d4-c79d-4714-942d-9875bd8e61dc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dd6fcbc8f87539ac687927b9e58ed15edb524ef6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720413"
---
# <a name="remove-drivergroupfilter"></a>DriverGroupFilter



从服务器上的驱动程序组中删除筛选规则。

## <a name="syntax"></a>语法

```
WDSUTIL /Remove-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|/DriverGroup：\<组名>|指定驱动程序组的名称。|
|[/Server：\<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|
|[/FilterType：\<FilterType>]|指定要从组中删除的筛选器的类型。 \<FilterType> 可以是以下项之一：</br>**BiosVendor**</br>**BiosVersion**</br>**ChassisType**</br>**制造商**</br>**Uuid**</br>**OsVersion**</br>**OsEdition**</br>**OsLanguage**|

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