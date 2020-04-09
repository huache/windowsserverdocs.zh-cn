---
title: 子命令启动-服务器
description: 子命令启动服务器的 Windows 命令主题，用于启动 Windows 部署服务服务器的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e4343e2-0a16-4e65-8769-c09adaef5680
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc3e0d11348dd6b531671e62139f2ce2c884c5ee
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833740"
---
# <a name="subcommand-start-server"></a>子命令：启动-服务器

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

启动 Windows 部署服务服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /start-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定要启动的服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要启动服务器，请键入下列内容之一：
```
wdsutil /start-Server
wdsutil /verbose /start-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用](using-the-disable-server-command.md)
使用[enable](using-the-enable-server-command.md) -server 命令
使用 "服务器[" 命令的](using-the-get-server-command.md)命令行语法，
使用 "[初始化-](using-the-initialize-server-command.md)服务器" 命令
子命令[： Set-server](subcommand-set-server.md)
[子命令： stop-server](subcommand-stop-server.md)
["取消初始化-服务器" 选项](the-uninitialize-server-option.md)
