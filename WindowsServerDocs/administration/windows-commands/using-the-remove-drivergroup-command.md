---
title: DriverGroup
description: 用于从服务器中删除驱动程序组的 DriverGroup 的参考文章。
ms.topic: reference
ms.assetid: 1fefe9df-9782-433c-8abe-3f1a35e50da2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b2e0112ab1b85f37d148cb3f2b1c26b217b1047d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038105"
---
# <a name="remove-drivergroup"></a>DriverGroup

从服务器中删除驱动程序组。

## <a name="syntax"></a>语法

```
WDSUTIL /Remove-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/DriverGroup:\<Group Name>|指定要删除的驱动程序组的名称。|
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|

## <a name="examples"></a>示例

若要删除驱动程序组，请键入下列内容之一：
```
WDSUTIL /Remove-DriverGroup /DriverGroup:PrinterDrivers
```
```
WDSUTIL /Remove-DriverGroup /DriverGroup:PrinterDrivers /Server:MyWdsServer
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)