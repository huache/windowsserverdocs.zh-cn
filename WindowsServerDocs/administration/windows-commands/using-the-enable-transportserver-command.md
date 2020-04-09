---
title: TransportServer
description: 适用于 TransportServer 的 Windows 命令主题，可用于启用传输服务器的所有服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d79dba1-4b57-4a00-8cba-877e6b8618e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ee5f1206633fb47c4a4b066c099fbf9c7020fb6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831480"
---
# <a name="enable-transportserver"></a>TransportServer

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

启用传输服务器的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Enable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定传输服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定名称，则将使用本地服务器。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要在服务器上启用这些服务，请运行下列操作之一：
```
wdsutil /Enable-TransportServer
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- 使用[TransportServer 命令
的](using-the-disable-transportserver-command.md)[命令行语法键](command-line-syntax-key.md)
使用[TransportServer 命令](using-the-get-transportserver-command.md)
[子命令： TransportServer](subcommand-set-transportserver.md)
[子命令：](subcommand-start-transportserver.md)
子命令： [stop-TransportServer](subcommand-stop-transportserver.md)
