---
title: DriverGroupPackage
description: DriverGroupPackage 的 Windows 命令主题，用于向驱动程序组添加驱动程序包。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7cd323ae-9049-448e-a460-6c7d6462d4c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6753baeb03b99ee149250d41844469a5008f5ecd
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832070"
---
# <a name="add-drivergrouppackage"></a>DriverGroupPackage

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

向驱动程序组添加驱动程序包。

## <a name="syntax"></a>语法
```
wdsutil /add-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```
### <a name="parameters"></a>参数

|         参数         |                                                                                                                                               说明                                                                                                                                               |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /DriverGroup：<Group Name> |                                                                                                                                 指定驱动程序组的名称。                                                                                                                                 |
|   /Server：<Server name>   |                                                                                  指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。                                                                                  |
|   /DriverPackage：<Name>   |                                                                      指定要添加到组的驱动程序包的名称。 如果无法按名称唯一地标识驱动程序包，则必须指定此选项。                                                                       |
|      /PackageId：<ID>      | 指定包的 ID。 若要查找包 ID，请单击包所在的驱动程序组（或 "**所有包**" 节点），右键单击该包，然后单击 "**属性**"。 包 ID 列在 "**常规**" 选项卡上，例如： **{DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}** 。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例
若要添加驱动程序包，请键入下列内容之一：
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /DriverPackage:XYZ
```
## <a name="additional-references"></a>其他参考
- 使用[DriverGroupPackages 命令](using-the-add-drivergrouppackages-command.md)的[命令行语法密钥](command-line-syntax-key.md)
使用[AllDriverPackages 子](using-the-add-alldriverpackages-subcommand.md)命令
使用[DriverPackage 命令](using-the-add-driverpackage-command.md)

