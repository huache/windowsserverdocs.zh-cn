---
title: 新-MulticastTransmission
description: MulticastTransmission 的参考文章，用于为映像创建新的多播传输。
ms.topic: reference
ms.assetid: c1f1dc46-dd50-4eb9-9f72-cf0e5d71bd3d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 30988ad23151f12533b75323f9376859a4c5d2a5
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038145"
---
# <a name="new-multicasttransmission"></a>新-MulticastTransmission

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

为映像创建新的多播传输。 此命令等效于使用 Windows 部署服务 mmc 管理单元创建传输 (右键单击 " **多播传输** " 节点，然后单击 " **创建多播传输**) "。 当同时安装了 "部署服务器" 角色服务和 "传输服务器" 角色服务时，应使用此命令 (默认安装) 。 如果只安装了传输服务器角色服务，请使用 [新的命名空间命令](using-the-new-namespace-command.md)。
## <a name="syntax"></a>语法
对于安装映像，请执行以下操作：
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      mediatype:Install
       mediaGroup:<Image Group>]
        [/Filename:<File name>]
```
对于启动映像传输 (仅支持 Windows Server 2008 R2) ：
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      mediatype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
许可证<Image name>|指定要使用多播传输的映像的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
|友好<Friendly name>|指定传输的友好名称。|
|/Description<Description>]|指定传输的描述。|
媒体： {Boot&#124;安装}|指定要使用多播传输的映像类型。 注意仅 Windows Server 2008 R2 支持 **Boot** 。|
|\mediaGroup： <Image group name> ]|指定包含图像的映像组。 如果未指定映像组名称，并且服务器上只存在一个映像组，则使用该映像组。 如果服务器上存在多个映像组，则必须使用此选项来指定映像组名称。|
|[/Filename： <File name> ]|指定文件名。 如果无法按名称唯一地标识源映像，则必须使用此选项指定文件名。|
|/Transmissiontype： {自动广播 &#124; ScheduledCast}|指定是 (自动广播) 还是基于指定的启动条件 (ScheduledCast) 来自动启动传输。<p><ul><li>**自动强制转换**。 这种传输类型表示，一旦适用的客户端请求安装映像，就会开始所选映像的多播传输。 其他客户端请求同一映像时，它们会加入已启动的传输。</li><li>**计划强制转换**。 此传输类型根据请求映像的客户端数和/或特定的日期和时间来设置传输的启动条件。 你可以指定以下选项：<p><ul><li>[/time： <time> ]-设置使用以下格式开始传输的时间： YYYY/MM/DD： hh： MM。</li><li>[/Clients： <Number of clients> ]-设置在传输开始之前要等待的最少客户端数。</li></ul></li></ul>|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定要使用多播传输的启动映像的体系结构。 由于不同体系结构的启动映像可能具有相同的名称，因此应指定体系结构以确保使用正确的映像。|
|[/Filename： <File name> ]|指定文件名。 如果无法按名称唯一地标识源映像，则必须指定文件名。|
## <a name="examples"></a>示例
若要在 Windows Server 2008 R2 中创建启动映像的自动强制转换，请键入：
```
wdsutil /New-MulticastTransmission /FriendlyName:WDS Boot Transmission
/Image:X64 Boot Imagemediatype:Boot /Architecture:x64 /Transmissiontype:AutoCast
```
若要创建安装映像的自动强制转换，请键入：
```
wdsutil /New-MulticastTransmission /FriendlyName:WDS AutoCast Transmission
/Image:Vista with Officemediatype:Install /Transmissiontype:AutoCast
```
若要创建安装映像的计划强制转换，请键入：
```
wdsutil /New-MulticastTransmission /FriendlyName:WDS SchedCast Transmission /Server:MyWDSServemedia:Vista with Officemediatype:Install
/Transmissiontype:ScheduledCast /time:2006/11/20:17:00 /Clients:100
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllMulticastTransmissions 命令](using-the-get-allmulticasttransmissions-command.md) 
[使用 MulticastTransmission 命令](using-the-get-multicasttransmission-command.md) 
[使用 MulticastTransmission 命令](using-the-remove-multicasttransmission-command.md) 
[子命令： MulticastTransmission](subcommand-start-multicasttransmission.md)
