---
title: 取消初始化-服务器
description: 用于取消初始化服务器的 Windows 命令主题，该主题将恢复在初始服务器配置期间对服务器所做的更改。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 015efb04-fe84-469f-bd81-49d0046296b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4ed912af1ec3bc505e1e7465650a119af979b407
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833110"
---
# <a name="uninitialize-server"></a>取消初始化-服务器

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

恢复在初始服务器配置期间对服务器所做的更改。 这包括 **/initialize-server**选项或 Windows 部署服务 mmc 管理单元所做的更改。 请注意，此命令会将服务器重置为未配置状态。 此命令不会修改 remoteInstall 共享文件夹的内容。 相反，它会重置服务器的状态，以便您可以重新初始化服务器。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要重新初始化服务器，请键入下列内容之一：
```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用](using-the-disable-server-command.md)
使用[enable](using-the-enable-server-command.md) -server 命令
使用 "服务器[" 命令的](using-the-get-server-command.md)命令行语法，
[使用 "初始化-](using-the-initialize-server-command.md)服务器" 命令
子命令： [Set-server](subcommand-set-server.md)
[子命令：启动-服务器](subcommand-start-server.md)
[子命令： stop-server](subcommand-stop-server.md)
