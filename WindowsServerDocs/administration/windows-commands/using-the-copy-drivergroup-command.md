---
title: 复制-DriverGroup
description: DriverGroup 的 Windows 命令主题，它复制服务器上的现有驱动程序组，包括筛选器、驱动程序包和启用/禁用状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0aaf6fa5-8b5b-4a1e-ae9b-8b5c6d89f571
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 277903150a25555b03b51c980436250656c597b1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831730"
---
# <a name="copy-drivergroup"></a>复制-DriverGroup

复制服务器上的现有驱动程序组，包括筛选器、驱动程序包和启用/禁用状态。

## <a name="syntax"></a>语法

```
WDSUTIL /Copy-DriverGroup [/Server:<Server name>] /DriverGroup:<Source Group Name> /GroupName:<New Group Name>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[/Server：\<Server name >]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|
|/DriverGroup：\<源组名称 >|指定源驱动程序组的名称。|
|/GroupName：\<新的组名 >|指定新驱动程序组的名称。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要复制驱动程序组，请键入下列内容之一：
```
WDSUTIL /Copy-DriverGroup /Server:MyWdsServer /DriverGroup:PrinterDrivers /GroupName:X86PrinterDrivers
```
```
WDSUTIL /Copy-DriverGroup /DriverGroup:PrinterDrivers /GroupName:ColorPrinterDrivers
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)