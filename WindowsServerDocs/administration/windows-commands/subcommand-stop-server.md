---
title: 子命令停止-服务器
description: 子命令停止-服务器的参考主题，用于停止 Windows 部署服务服务器上的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 09f411c0-099f-4591-95fd-b77b3fd9118a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68cc73ac016e2ffded774567034801e1c11944d1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721635"
---
# <a name="subcommand-stop-server"></a>子命令：停止-服务器

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

停止 Windows 部署服务服务器上的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Stop-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要停止服务，请键入下列内容之一：
```
wdsutil /Stop-Server
wdsutil /verbose /Stop-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)

使用 enable[-server 命令](using-the-disable-server-command.md)通过使用命令行中的[命令使用](using-the-get-server-command.md)
[enable](using-the-enable-server-command.md)
-server 命令使用[Initialize-](using-the-initialize-server-command.md)
server 命令命令[： set-server](subcommand-set-server.md)
[子命令：启动-服务器](subcommand-start-server.md)
-取消[初始化-服务器选项](the-uninitialize-server-option.md)
