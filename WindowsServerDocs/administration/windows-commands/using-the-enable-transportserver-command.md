---
title: TransportServer
description: TransportServer 的参考主题，可用于启用传输服务器的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d79dba1-4b57-4a00-8cba-877e6b8618e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 50cc381b1c178628be7d135868027b4f37787cdd
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720921"
---
# <a name="enable-transportserver"></a>TransportServer

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启用传输服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Enable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定传输服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定名称，则将使用本地服务器。|
## <a name="examples"></a>示例
若要在服务器上启用这些服务，请运行下列操作之一：
```
wdsutil /Enable-TransportServer
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [Command-Line Syntax Key](command-line-syntax-key.md)
使用[TransportServer 命令](using-the-disable-transportserver-command.md)
的命令行语法键[使用 TransportServer 命令](using-the-get-transportserver-command.md)
[子命令： TransportServer](subcommand-set-transportserver.md)
[子](subcommand-start-transportserver.md)
命令： TransportServer 子命令：[stop-TransportServer](subcommand-stop-transportserver.md)
