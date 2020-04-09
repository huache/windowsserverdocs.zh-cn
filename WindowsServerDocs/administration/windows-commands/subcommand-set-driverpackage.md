---
title: 子命令集-DriverPackage
description: DriverPackage 的 Windows 命令主题，用于重命名和/或启用或禁用服务器上的驱动程序包。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 11804bb6-ca29-4461-8c63-5131748cd742
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68d282b3338e67a33a55481658f55db69930b10e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834012"
---
# <a name="subcommand-set-driverpackage"></a>子命令： set-DriverPackage

重命名和/或启用或禁用服务器上的驱动程序包。

## <a name="syntax"></a>语法

```
WDSUTIL /Set-DriverPackage [/Server:<Server name>] {/DriverPackage:<Name> | /PackageId:<ID>} [/Name:<New Name>] [/Enabled:{Yes | No}
```

### <a name="parameters"></a>参数

|        参数         |                                                                                                                                                                                                               说明                                                                                                                                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server：\<Server name >] |                                                                                                                                                 指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。                                                                                                                                                 |
| [/DriverPackage：\<名称 >] |                                                                                                                                                                                       指定要修改的驱动程序包的当前名称。                                                                                                                                                                                        |
|    [/PackageId：\<ID >]    | 指定驱动程序包的 Windows 部署服务 ID。 如果无法按名称唯一地标识驱动程序包，则必须指定此选项。 若要为包查找此 ID，请单击包所在的驱动程序组（或 "**所有包**" 节点），右键单击该包，然后单击 "**属性**"。 包 ID 在 "**常规**" 选项卡上列出。例如： {DD098D20-1850-4FC8-8E35-EA24A1BEFF5E}。 |
|   [/Name：\<新名称 >]    |                                                                                                                                                                                              指定驱动程序包的新名称。                                                                                                                                                                                              |
|      [/Enabled： {Yes      |                                                                                                                                                                                                                   不                                                                                                                                                                                                                    |

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要更改包的设置，请键入下列内容之一：
```
WDSUTIL /Set-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318} /Name:MyDriverPackage
```
```
WDSUTIL /Set-DriverPackage /DriverPackage:MyDriverPackage /Name:NewName /Enabled:Yes
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)