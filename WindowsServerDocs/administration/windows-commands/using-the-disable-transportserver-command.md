---
title: TransportServer
description: TransportServer 的参考主题，禁用传输服务器的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a009706b-8e89-486b-8e3d-512cd9f4de74
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 81ae150b4f8e4de577e377a2d10a7a69675adac7
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720959"
---
# <a name="disable-transportserver"></a>TransportServer

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

禁用传输服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Disable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定要禁用的传输服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定传输服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要禁用服务器，请键入：
```
wdsutil /Disable-TransportServer
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [Command-Line Syntax Key](command-line-syntax-key.md)
使用[TransportServer 命令](using-the-enable-transportserver-command.md)
的命令行语法键[使用 TransportServer 命令](using-the-get-transportserver-command.md)
[子命令： TransportServer](subcommand-set-transportserver.md)
[子](subcommand-start-transportserver.md)
命令： TransportServer 子命令：[stop-TransportServer](subcommand-stop-transportserver.md)
