---
title: 子命令启动-服务器
description: 子命令启动-服务器的参考主题，用于启动 Windows 部署服务服务器的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e4343e2-0a16-4e65-8769-c09adaef5680
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e2a6de007e62bf3be5544f97b53a4fcc13118985
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721652"
---
# <a name="subcommand-start-server"></a>子命令：启动-服务器

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启动 Windows 部署服务服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /start-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定要启动的服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要启动服务器，请键入下列内容之一：
```
wdsutil /start-Server
wdsutil /verbose /start-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)

[使用 enable](using-the-enable-server-command.md)
[-server 命令](using-the-disable-server-command.md)通过使用[Initialize-](using-the-initialize-server-command.md)
server 命令通过使用[get-help](using-the-get-server-command.md)
命令，使用命令行命令[： set-server](subcommand-set-server.md)
[子命令：停止-服务器](subcommand-stop-server.md)
[初始化-服务器选项](the-uninitialize-server-option.md)
