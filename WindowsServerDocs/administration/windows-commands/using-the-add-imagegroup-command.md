---
title: ImageGroup
description: ImageGroup 的参考主题，它将图像组添加到 Windows 部署服务服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6ca88671-51de-4924-b969-88f3dfd84270
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b08042ac6b33c0ccfe0b66bb0fec70805d55d75f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721054"
---
# <a name="add-imagegroup"></a>ImageGroup

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将映像组添加到 Windows 部署服务服务器。

## <a name="syntax"></a>语法
```
wdsutil [Options] /add-ImageGroumediaGroup:<Image group name> [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
mediaGroup:<Image group name>|指定要添加的映像组的名称。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要添加映像组，请键入下列内容之一：
```
wdsutil /add-ImageGroumediaGroup:ImageGroup2
wdsutil /verbose /add-ImageGroumediaGroup:My Image Group /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [Command-Line Syntax Key](command-line-syntax-key.md)
使用[AllImageGroups 命令](using-the-get-allimagegroups-command.md)
的命令行语法键使用[ImageGroup 命令](using-the-get-imagegroup-command.md)
，使用[ImageGroup 命令](using-the-remove-imagegroup-command.md)
[子命令： set-ImageGroup](subcommand-set-imagegroup.md)
