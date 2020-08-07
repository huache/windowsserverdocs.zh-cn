---
title: 启用-服务器
description: 启用-Server 的参考文章，启用所有服务 Windows 部署服务。
ms.topic: article
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 04884c4f4648db4ff78446048f34ea1ec609d154
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87896549"
---
# <a name="enable-server"></a>启用-服务器

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启用 Windows 部署服务的所有服务。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
## <a name="examples"></a>示例
若要在服务器上启用这些服务，请运行下列操作之一：
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 disable-Server 命令](using-the-disable-server-command.md) 
[使用 get-Server 命令](using-the-get-server-command.md) 
[使用 Initialize-Server 命令](using-the-initialize-server-command.md) 
[子命令：设置-服务器](subcommand-set-server.md) 
[子命令：启动-服务器](subcommand-start-server.md) 
[子命令：停止-服务器](subcommand-stop-server.md) 
["取消初始化服务器" 选项](the-uninitialize-server-option.md)
