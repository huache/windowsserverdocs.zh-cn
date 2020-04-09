---
title: DriverPackage
description: 用于删除 DriverPackage 的 Windows 命令主题，用于从服务器中删除驱动程序包。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6b201e91-0d44-4e4a-8252-8b0235df1002
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f9eeebd0fd560f18aa49ac46f7eea30d8a9cc958
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830400"
---
# <a name="remove-driverpackage"></a>DriverPackage

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 

从服务器中删除驱动程序包。

## <a name="syntax"></a>语法
```
wdsutil /remove-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```
### <a name="parameters"></a>参数

|        参数        |                                                                            说明                                                                             |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server：<Server name>] |              指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。              |
| [/DriverPackage：<Name>] |                                                        指定要删除的驱动程序包的名称。                                                         |
|    [/PackageId：<ID>]    | 指定要删除的驱动程序包的 Windows 部署服务 ID。 如果无法按名称唯一地标识驱动程序包，则必须指定 ID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例
若要查看有关图像的信息，请键入下列内容之一：
```
wdsutil /remove-DriverPackage /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
```
wdsutil /remove-DriverPackage /Server:MyWdsServer /DriverPackage:MyDriverPackage
```
## <a name="additional-references"></a>其他参考
- [使用 DriverPackages 命令
的](using-the-remove-driverpackages-command.md)[命令行语法键](command-line-syntax-key.md)
