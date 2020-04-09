---
title: 子命令集-DriverGroup
description: DriverGroup 的 Windows 命令主题，用于设置服务器上现有驱动程序组的属性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e4ba9b1c-8c52-4fd5-969b-f7905611b364
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c49381dc65f3b2ffc9a04e4fb2699818515a931f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834030"
---
# <a name="subcommand-set-drivergroup"></a>子命令： set-DriverGroup

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

设置服务器上的现有驱动程序组的属性。

## <a name="syntax"></a>语法
```
wdsutil /Set-DriverGroup /DriverGroup:<Group Name> [/Server:<Server Name>] [/Name:<New Group Name>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/DriverGroup：<Group Name>|指定驱动程序组的名称。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|
|[/Name：<New Group Name>]|指定驱动程序组的新名称。|
|[/Enabled： {Yes &#124; No}|启用或禁用驱动程序组。|
|[/Applicability： {全部&#124;匹配}]|如果满足筛选条件，则指定要安装的程序包。 **匹配**意味着仅安装与客户端硬件匹配的驱动程序包。 **All**表示将所有程序包安装到客户端，而不考虑其硬件。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要设置驱动程序组的属性，请键入下列内容之一：
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```
```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Name:colorprinterdrivers /Applicability:All
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[子命令： DriverGroupFilter](subcommand-set-drivergroupfilter.md)
