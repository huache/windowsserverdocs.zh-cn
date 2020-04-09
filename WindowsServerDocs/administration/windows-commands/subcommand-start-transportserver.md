---
title: 子命令开始-TransportServer
description: TransportServer 的 Windows 命令主题，用于启动传输服务器的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1356d415006324d75783d4e12ad6882d0fcc779
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833750"
---
# <a name="subcommand-start-transportserver"></a>子命令： TransportServer

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

启动传输服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定传输服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要启动服务器，请键入下列内容之一：
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用 TransportServer 命令](using-the-disable-transportserver-command.md) [
使用](using-the-enable-transportserver-command.md)TransportServer 命令
使用[命令](using-the-get-transportserver-command.md)
[子命令： TransportServer](subcommand-set-transportserver.md)
[子命令： stop-TransportServer](subcommand-stop-transportserver.md)
