---
title: TransportServer
description: TransportServer 的参考文章，可禁用传输服务器的所有服务。
ms.topic: reference
ms.assetid: a009706b-8e89-486b-8e3d-512cd9f4de74
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 361a963f1e2e7fd98d05dc288dbca06353ae22f0
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032142"
---
# <a name="disable-transportserver"></a>TransportServer

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

禁用传输服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Disable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server： <Server name> ]|指定要禁用的传输服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定传输服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要禁用服务器，请键入：
```
wdsutil /Disable-TransportServer
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 TransportServer 命令](using-the-enable-transportserver-command.md) 
[使用 TransportServer 命令](using-the-get-transportserver-command.md) 
[子命令： set-TransportServer](subcommand-set-transportserver.md) 
[子命令： TransportServer](subcommand-start-transportserver.md) 
[子命令： TransportServer](subcommand-stop-transportserver.md)
