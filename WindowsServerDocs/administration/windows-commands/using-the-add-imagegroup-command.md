---
title: ImageGroup
description: ImageGroup 的参考文章，可将映像组添加到 Windows 部署服务服务器。
ms.topic: reference
ms.assetid: 6ca88671-51de-4924-b969-88f3dfd84270
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 45edd86f62493cadbfbfd6e3f1e9bc86ea5bd9fc
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622213"
---
# <a name="add-imagegroup"></a>ImageGroup

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将映像组添加到 Windows 部署服务服务器。

## <a name="syntax"></a>语法
```
wdsutil [Options] /add-ImageGroumediaGroup:<Image group name> [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
mediaGroup:<Image group name>|指定要添加的映像组的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要添加映像组，请键入下列内容之一：
```
wdsutil /add-ImageGroumediaGroup:ImageGroup2
wdsutil /verbose /add-ImageGroumediaGroup:My Image Group /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllImageGroups 命令](using-the-get-allimagegroups-command.md) 
[使用 ImageGroup 命令](using-the-get-imagegroup-command.md) 
[使用 ImageGroup 命令](using-the-remove-imagegroup-command.md) 
[子命令： set-ImageGroup](subcommand-set-imagegroup.md)
