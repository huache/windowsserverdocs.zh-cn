---
title: 子命令停止-TransportServer
description: TransportServer 的参考主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: dc1b1eec-6893-445e-81dc-16b3fae287fa
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4321ec991b2c20911f992e4c3c38e5c9cfa5f165
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721624"
---
# <a name="subcommand-stop-transportserver"></a>子命令： TransportServer

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

停止传输服务器上的所有服务。
## <a name="syntax"></a>语法
```
wdsutil [Options] /Stop-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定传输服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定传输服务器，将使用本地服务器。|
## <a name="examples"></a><a name="BKMK_examples"></a>示例
若要停止服务，请键入下列内容之一：
```
wdsutil /Stop-TransportServer
wdsutil /verbose /Stop-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [使用](command-line-syntax-key.md)
[TransportServer 命令](using-the-disable-transportserver-command.md)
的命令行语法键使用[TransportServer 命令](using-the-get-transportserver-command.md)
子命令[TransportServer 命令](using-the-enable-transportserver-command.md)
[： TransportServer](subcommand-set-transportserver.md)
[子命令：启动-TransportServer](subcommand-start-transportserver.md)
