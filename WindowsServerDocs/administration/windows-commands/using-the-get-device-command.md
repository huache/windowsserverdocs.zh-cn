---
title: 获取-设备
description: 获取设备的参考文章，它检索有关预留计算机的 Windows 部署服务信息 (即，已排入到 active directory 域服务中的计算机帐户的物理计算机。
ms.topic: reference
ms.assetid: 1da79286-7e1d-45f2-aea2-d446e16a6911
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 118e14f738920527c61c8da25d19ab98126fc004
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029695"
---
# <a name="get-device"></a>获取-设备

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

检索有关预留计算机的 Windows 部署服务信息， (即已排入 active directory 域服务中的计算机帐户的物理计算机。

## <a name="syntax"></a>语法
```
wdsutil /Get-Device {/Device:<Device name> | /ID:<MAC or UUID>} [/Domain:<Domain>] [/forest:{Yes | No}]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|装置<Device name>|指定 (SAMAccountName) 计算机的名称。|
|识别<MAC or UUID>|指定计算机的 MAC 地址或 UUID (GUID) ，如以下示例中所示。 请注意，有效的 GUID 必须采用以下两种格式之一：二进制字符串或 GUID 字符串<p>-   **二进制字符串**：/ID： ACEFA3E81F20694E953EB2DAA1E8B1B6<br />-   **MAC 地址**： 00B056882FDC (没有短划线) 或 00-00-00-)  (2f-<br />-   **GUID 字符串**：/ID： E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6|
|[/Domain： <Domain> ]|指定要在其中搜索预留计算机的域。 此参数的默认值为本地域。|
|[/forest： {Yes &#124; No}]|指定 Windows 部署服务应搜索整个林还是搜索本地域。 默认值为 " **否**"，这意味着只会搜索本地域。|
## <a name="examples"></a>示例
若要使用计算机名称获取信息，请键入：
```
wdsutil /Get-Device /Device:computer1
```
若要使用 MAC 地址获取信息，请键入：
```
wdsutil /verbose /Get-Device /ID:00-B0-56-88-2F-DC /Domain:MyDomain
```
若要使用 GUID 字符串获取信息，请键入：
```
wdsutil /verbose /Get-Device /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6 /forest:Yes
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[子命令：设置-设备](subcommand-set-device.md) 
[使用 "添加设备" 命令](using-the-add-device-command.md) 
[使用 AllDevices 命令](using-the-get-alldevices-command.md)
