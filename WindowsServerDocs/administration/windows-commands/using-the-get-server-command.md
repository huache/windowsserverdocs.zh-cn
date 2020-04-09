---
title: 获取服务器
description: 用于获取服务器的 Windows 命令主题，该主题从指定的 Windows 部署服务服务器中检索信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bef60db4-d58d-4304-ab4b-be53dd3271c3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65903dc89730eb9d1da23be31ecc1909daece9c4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830840"
---
# <a name="get-server"></a>获取服务器

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

检索指定 Windows 部署服务服务器中的信息。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-Server [/Server:<Server name>] /Show:{Config | Images | All} [/detailed]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，则使用本地服务器。|
|/Show： {Config &#124; Images &#124; All}|指定要返回的信息的类型。<p>-   **Config**返回配置信息。<br />-   **映像**返回有关映像组、启动映像和安装映像的信息。<br />-   **全部**返回配置信息和图像信息。|
|[/detailed]|可以将此选项与 **/show： Images**或 **/show： all**一起使用，以指示应返回每个图像中的所有图像元数据。 如果未使用 **/detailed**选项，则默认行为是返回映像名称、说明和文件名。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要查看有关服务器的信息，请键入：
```
wdsutil /Get-Server /Show:Config
```
若要查看有关服务器的详细信息，请键入：
```
wdsutil /verbose /Get-Server /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用](using-the-disable-server-command.md)
使用 enable-server[命令
使用](using-the-initialize-server-command.md) [Enable](using-the-enable-server-command.md) -Server 命令的命令行语法，
[子命令： Set-server](subcommand-set-server.md)
子命令[： start-server](subcommand-start-server.md) [
](subcommand-stop-server.md) [The uninitialize-Server Option](the-uninitialize-server-option.md)

