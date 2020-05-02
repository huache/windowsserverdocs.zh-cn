---
title: ImageGroup
description: ImageGroup 的参考主题，用于从服务器中删除映像组。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5b2c9813-5df2-4272-8449-26f3bb16f82b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f814d83a32a8c739e7462bc77251cf3f3f4fe20e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720355"
---
# <a name="using-the-remove-imagegroup-command"></a>使用 ImageGroup 命令

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从服务器中删除映像组。

## <a name="syntax"></a>语法
```
wdsutil [Options] /remove-ImageGroumediaGroup:<Image group name> [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
mediaGroup:<Image group name>|指定要删除的映像组的名称|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要删除映像组，请键入下列内容之一：
```
wdsutil /remove-ImageGroumediaGroup:ImageGroup1
wdsutil /verbose /remove-ImageGroumediaGroup:My Image Group /Server:MyWDSServer 
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)  
[使用 ImageGroup 命令](using-the-add-imagegroup-command.md)  
[使用 AllImageGroups 命令](using-the-get-allimagegroups-command.md)  
[使用 ImageGroup 命令](using-the-get-imagegroup-command.md)  
[子命令： set-ImageGroup](subcommand-set-imagegroup.md)  
