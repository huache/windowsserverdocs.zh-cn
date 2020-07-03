---
title: 取消初始化-服务器
description: 有关 "取消初始化-服务器" 的参考文章，这会恢复在初始服务器配置期间对服务器所做的更改。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 015efb04-fe84-469f-bd81-49d0046296b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fdbe391a7335c347f05f9f9c06bbade3474fa30e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935875"
---
# <a name="uninitialize-server"></a>取消初始化-服务器

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

恢复在初始服务器配置期间对服务器所做的更改。 这包括 **/initialize-server**选项或 Windows 部署服务 mmc 管理单元所做的更改。 请注意，此命令会将服务器重置为未配置状态。 此命令不会修改 remoteInstall 共享文件夹的内容。 相反，它会重置服务器的状态，以便您可以重新初始化服务器。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要重新初始化服务器，请键入下列内容之一：
```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 disable-Server 命令](using-the-disable-server-command.md) 
[使用 enable-Server 命令](using-the-enable-server-command.md) 
[使用 get-Server 命令](using-the-get-server-command.md) 
[使用 Initialize-Server 命令](using-the-initialize-server-command.md) 
[子命令：设置-服务器](subcommand-set-server.md) 
[子命令：启动-服务器](subcommand-start-server.md) 
[子命令：停止-服务器](subcommand-stop-server.md)
