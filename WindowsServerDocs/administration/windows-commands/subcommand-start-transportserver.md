---
title: 子命令开始-TransportServer
description: 子命令 TransportServer 的参考主题，用于启动传输服务器的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 92bd68421883c49ec29dfb78f06121bff880b01e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721639"
---
# <a name="subcommand-start-transportserver"></a>子命令： TransportServer

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启动传输服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定传输服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要启动服务器，请键入下列内容之一：
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [使用](command-line-syntax-key.md)
[TransportServer 命令](using-the-disable-transportserver-command.md)
的命令行语法键使用[TransportServer 命令](using-the-get-transportserver-command.md)
子命令[TransportServer 命令](using-the-enable-transportserver-command.md)
[： TransportServer](subcommand-set-transportserver.md)
[子命令： stop-TransportServer](subcommand-stop-transportserver.md)
