---
title: 启用-服务器
description: 适用于 enable-Server 的 Windows 命令主题，启用所有服务以进行 Windows 部署服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6b10ff920667cfdbaae5baaf096bf56e11ce880e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831540"
---
# <a name="enable-server"></a>启用-服务器

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

启用 Windows 部署服务的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要在服务器上启用这些服务，请运行下列操作之一：
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
使用[
命令
使用服务器](using-the-get-server-command.md)[命令的命令](using-the-disable-server-command.md)行语法，[使用 Initialize-](using-the-initialize-server-command.md) Server 命令
[子命令： Set-server](subcommand-set-server.md)
子命令[：启动-服务器](subcommand-start-server.md)
子命令：[停止](subcommand-stop-server.md) [-服务器
](the-uninitialize-server-option.md)
