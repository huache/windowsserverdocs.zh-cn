---
title: DriverGroupFilter
description: DriverGroupFilter 的参考文章，用于从服务器上的驱动程序组中删除筛选规则。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 837bd5d4-c79d-4714-942d-9875bd8e61dc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 98d2253cc5148ba4581399d688b74cd426a649fb
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936329"
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
|[/FilterType： \<FilterType> ]|指定要从组中删除的筛选器的类型。 \<FilterType>可以是下列其中一项：</br>**BiosVendor**</br>**BiosVersion**</br>**ChassisType**</br>**制造商**</br>**Uuid**</br>**OsVersion**</br>**OsEdition**</br>**OsLanguage**|

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