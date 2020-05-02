---
title: AllDriverGroups
description: AllDriverGroups 的参考主题，用于显示服务器上所有驱动程序组的相关信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f245ba53-f150-41b1-8418-38dcf0410a05
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c4ac3e0c7b05c96383714c3a702cffd6aa8df18a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720893"
---
# <a name="get-alldrivergroups"></a>AllDriverGroups

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示服务器上所有驱动程序组的相关信息。

## <a name="syntax"></a>语法
```
wdsutil /Get-AllDriverGroups [/Server:<Server name>] [/Show:{PackageMetaData | Filters | All}]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。|
|[/Show： {PackageMetaData &#124; 筛选器 &#124; All}]|显示指定组中所有驱动程序包的元数据。 **PackageMetaData**显示有关驱动程序组的所有筛选器的信息。 **筛选器**显示组的所有驱动程序包和筛选器的元数据。|
## <a name="examples"></a>示例
若要查看有关驱动程序文件的信息，请键入：
```
wdsutil /Get-AllDriverGroups /Server:MyWdsServer /Show:All
```
```
wdsutil /Get-AllDriverGroups [/Show:PackageMetaData]
```
## <a name="additional-references"></a>其他参考
- [Command-Line Syntax Key](command-line-syntax-key.md)
[使用 DriverGroup 命令的](using-the-get-drivergroup-command.md)命令行语法关键字
