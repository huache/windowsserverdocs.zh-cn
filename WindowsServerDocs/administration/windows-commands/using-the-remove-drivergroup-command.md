---
title: DriverGroup
description: 用于从服务器中删除驱动程序组的 DriverGroup 的参考文章。
ms.topic: article
ms.assetid: 1fefe9df-9782-433c-8abe-3f1a35e50da2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a6b199e48ab5ffbe5945f8671f23b24629df3337
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87881256"
---
# <a name="remove-drivergroup"></a>DriverGroup

从服务器中删除驱动程序组。

## <a name="syntax"></a>语法

```
WDSUTIL /Remove-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```

### <a name="parameters"></a>参数

|参数|描述|
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