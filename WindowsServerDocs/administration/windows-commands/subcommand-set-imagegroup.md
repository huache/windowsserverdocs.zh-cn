---
title: 子命令集-ImageGroup
description: 子命令集的参考主题-ImageGroup，用于更改映像组的属性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4d86946a-e261-4d41-8b0c-1ab0ba2e3430
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 429a8fee5b0236d264eb421f110219a1bc037368
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721701"
---
# <a name="subcommand-set-imagegroup"></a>子命令： set-ImageGroup

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改映像组的属性。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Set-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
mediaGroup:<Image group name>|指定映像组的名称。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定，将使用本地服务器。|
|[/Name：<New image group name>]|指定映像组的新名称。|
|[/Security：<SDDL>]|以安全描述符定义语言（SDDL）格式指定映像组的新安全描述符。|
## <a name="examples"></a>示例
若要设置映像组的名称，请键入：
```
wdsutil /Set-ImageGroumediaGroup:ImageGroup1 /Name:New Image Group Name
```
若要为映像组指定各种设置，请键入：
```
wdsutil /verbose /Set-ImageGroumediaGroup:ImageGroup1 /Server:MyWDSServer /Name:New Image Group Name 
/Security:O:BAG:S-1-5-21-2176941838-3499754553-4071289181-513 D:AI(A;ID;FA;;;SY)(A;OICIIOID;GA;;;SY)(A;ID;FA;;;BA)(A;OICIIOID;GA;;;BA) (A;ID;0x1200a9;;;AU)(A;OICIIOID;GXGR;;;AU)
```
## <a name="additional-references"></a>其他参考
- [使用](command-line-syntax-key.md)
[ImageGroup 命令](using-the-add-imagegroup-command.md)
的命令行语法键使用[AllImageGroups 命令](using-the-get-allimagegroups-command.md)
，使用[ImageGroup 命令](using-the-get-imagegroup-command.md)
，使用[ImageGroup 命令](using-the-remove-imagegroup-command.md)
