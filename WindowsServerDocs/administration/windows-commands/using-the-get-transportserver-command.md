---
title: TransportServer
description: TransportServer 的参考文章，其中显示有关指定传输服务器的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: de634123-0179-41b2-9c6f-726508130ff5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 115942290679decd8b8c660e4113576efb30123d
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932168"
---
# <a name="get-transportserver"></a>TransportServer

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关指定传输服务器的信息。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-TransportServer [/Server:<Server name>] /Show:{Config}
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
|/Show： {Config}|返回有关指定传输服务器的配置信息。|
## <a name="examples"></a>示例
若要查看有关服务器的信息，请键入：
```
wdsutil /Get-TransportServer /Show:Config
```
若要查看配置信息，请键入：
```
wdsutil /Get-TransportServer /Server:MyWDSServer /Show:Config
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 TransportServer 命令](using-the-disable-transportserver-command.md) 
[使用 TransportServer 命令](using-the-enable-transportserver-command.md) 
[子命令： set-TransportServer](subcommand-set-transportserver.md) 
[子命令： TransportServer](subcommand-start-transportserver.md) 
[子命令： TransportServer](subcommand-stop-transportserver.md)
