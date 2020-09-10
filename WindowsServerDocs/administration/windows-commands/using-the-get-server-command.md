---
title: 获取服务器
description: 用于从指定的 Windows 部署服务服务器中检索信息的获取服务器的参考文章。
ms.topic: reference
ms.assetid: bef60db4-d58d-4304-ab4b-be53dd3271c3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: fe55e707dda58e65d2b86fe553910d010f8b2586
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628499"
---
# <a name="get-server"></a>获取服务器

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

检索指定 Windows 部署服务服务器中的信息。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-Server [/Server:<Server name>] /Show:{Config | Images | All} [/detailed]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名 (FQDN) 。 如果未指定服务器名称，则使用本地服务器。|
|/Show： {Config &#124; &#124; All）|指定要返回的信息的类型。<p>-   **Config** 返回配置信息。<br />-   **映像** 返回有关映像组、启动映像和安装映像的信息。<br />-   **All** 返回配置信息和图像信息。|
|[/detailed]|可以将此选项与 **/show： Images** 或 **/show： all** 一起使用，以指示应返回每个图像中的所有图像元数据。 如果未使用 **/detailed** 选项，则默认行为是返回映像名称、说明和文件名。|
## <a name="examples"></a>示例
若要查看有关服务器的信息，请键入：
```
wdsutil /Get-Server /Show:Config
```
若要查看有关服务器的详细信息，请键入：
```
wdsutil /verbose /Get-Server /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 disable-Server 命令](using-the-disable-server-command.md) 
[使用 enable-Server 命令](using-the-enable-server-command.md) 
[使用 Initialize-Server 命令](using-the-initialize-server-command.md) 
[子命令：设置-服务器](subcommand-set-server.md) 
[子命令：启动-服务器](subcommand-start-server.md) 
[子命令：停止-服务器](subcommand-stop-server.md) 
["取消初始化服务器" 选项](the-uninitialize-server-option.md)
