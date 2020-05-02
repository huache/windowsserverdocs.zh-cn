---
title: 取消初始化-服务器
description: 有关 "取消初始化-服务器" 的参考主题，这会恢复在初始服务器配置期间对服务器所做的更改。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 015efb04-fe84-469f-bd81-49d0046296b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4d7747a44172b7382bd22a7d48ccc717a89ccacb
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721386"
---
# <a name="uninitialize-server"></a>取消初始化-服务器

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

恢复在初始服务器配置期间对服务器所做的更改。 这包括 **/initialize-server**选项或 Windows 部署服务 mmc 管理单元所做的更改。 请注意，此命令会将服务器重置为未配置状态。 此命令不会修改 remoteInstall 共享文件夹的内容。 相反，它会重置服务器的状态，以便您可以重新初始化服务器。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要重新初始化服务器，请键入下列内容之一：
```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)

使用[enable](using-the-enable-server-command.md)

[-server 命令](using-the-disable-server-command.md)通过使用[Initialize-](using-the-initialize-server-command.md)
server[命令使用 "](using-the-get-server-command.md)服务器" 命令使用 "服务器" 命令[： set-server](subcommand-set-server.md)
[子命令：启动-服务器](subcommand-start-server.md)
[子命令：停止-服务器](subcommand-stop-server.md)
