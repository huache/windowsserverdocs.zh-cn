---
title: 子命令集-ImageGroup
description: 用于更改映像组属性的子命令集-ImageGroup 的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4d86946a-e261-4d41-8b0c-1ab0ba2e3430
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 966e3c10d9bcc13568f5fec4e1efd1ad46a121b0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833910"
---
# <a name="subcommand-set-imagegroup"></a>子命令： set-ImageGroup

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更改映像组的属性。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Set-ImageGroumediaGroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
mediaGroup：<Image group name>|指定映像组的名称。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定，将使用本地服务器。|
|[/Name：<New image group name>]|指定映像组的新名称。|
|[/Security：<SDDL>]|以安全描述符定义语言（SDDL）格式指定映像组的新安全描述符。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
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
- [命令行语法键](command-line-syntax-key.md)
[使用](using-the-add-imagegroup-command.md) [AllImageGroups 命令
使用命令](using-the-get-allimagegroups-command.md)
使用[ImageGroup 命令](using-the-get-imagegroup-command.md)，
[使用 ImageGroup 命令](using-the-remove-imagegroup-command.md)。
