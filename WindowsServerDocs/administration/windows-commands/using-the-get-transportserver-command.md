---
title: TransportServer
description: TransportServer 的参考主题，用于显示有关指定传输服务器的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: de634123-0179-41b2-9c6f-726508130ff5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 82ab5f901240f964bd22e7fb8053ed95b1c6fe51
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719727"
---
# <a name="get-transportserver"></a>TransportServer

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关指定传输服务器的信息。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-TransportServer [/Server:<Server name>] /Show:{Config}
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
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
- [Command-Line Syntax Key](command-line-syntax-key.md)使用
[TransportServer 命令](using-the-disable-transportserver-command.md)
的命令行语法键[使用 enable-TransportServer 命令](using-the-enable-transportserver-command.md)
[子命令： TransportServer](subcommand-set-transportserver.md)
[子](subcommand-start-transportserver.md)
命令： TransportServer 子命令：[stop-TransportServer](subcommand-stop-transportserver.md)
