---
title: ImageGroup
description: ImageGroup 的参考文章，用于检索有关映像组及其图像的信息。
ms.topic: article
ms.assetid: 0fc25aca-a529-44ee-bc8e-96bc8affb458
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bfe2c804d24914b500703476d28e5281fdaef8c0
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87879305"
---
# <a name="get-imagegroup"></a>ImageGroup

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

检索有关映像组及其内图像的信息。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/detailed]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
mediaGroup:<Image group name>|指定映像组的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
|[/detailed]|返回每个图像的图像元数据。 如果未使用此参数，则默认行为是只返回映像名称、说明和文件名。|
## <a name="examples"></a>示例
若要查看有关映像组的信息，请键入：
```
wdsutil /Get-ImageGroumediaGroup:ImageGroup1
```
若要查看包括元数据的信息，请键入：
```
wdsutil /verbose /Get-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /detailed
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 ImageGroup 命令](using-the-add-imagegroup-command.md) 
[使用 AllImageGroups 命令](using-the-get-allimagegroups-command.md) 
[使用 ImageGroup 命令](using-the-remove-imagegroup-command.md) 
[子命令： set-ImageGroup](subcommand-set-imagegroup.md)
