---
title: MulticastTransmission
description: MulticastTransmission 的参考主题，该主题显示有关指定映像的多播传输的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b733737b-1e81-43d4-a058-d6985a613bef
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a848a4aceb41b4da679d9182459df29c89008fea
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719760"
---
# <a name="get-multicasttransmission"></a>MulticastTransmission

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示有关指定映像的多播传输的信息。

## <a name="syntax"></a>语法
**Windows Server 2008**
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] 
[/Filename:<File name>] [/Show:Clients]
```
用于启动映像传输的**Windows Server 2008 R2** ：
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
    [/Server:<Server name>]
    [/details:Clients]
  mediatype:Boot
    /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
对于安装映像传输：
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
         [/Server:<Server name>]
         [/details:Clients]
       mediatype:Install
    mediaGroup:<Image Group>]
     [/Filename:<File name>]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
许可证<Image name>|显示与此映像关联的多播传输。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，则使用本地服务器。|
媒体媒体：安装|指定映像类型。 请注意，必须将此选项设置为 "**安装**"。|
|\mediaGroup：<Image group name>]|指定包含图像的映像组。 如果未指定映像组名称，并且服务器上只存在一个映像组，则使用该映像组。 如果服务器上存在多个映像组，则必须使用此选项来指定映像组。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定与传输关联的启动映像的体系结构。 由于不同体系结构中的启动映像可能具有相同的映像名称，因此应指定体系结构以确保使用正确的映像。|
|[/Filename：<File name>]|指定包含图像的文件。 如果无法按名称唯一地标识映像，则必须使用此选项指定文件名。|
|[/Show：个客户端]<p>或<p>[/details：客户端]|显示有关连接到多播传输的客户端计算机的信息。|
## <a name="examples"></a>示例
**Windows Server 2008**若要查看有关通过 Office 进行名为 Vista 的映像的传输的信息，请键入下列内容之一：
```
wdsutil /Get-MulticastTransmissiomedia:Vista with Officemediatype:Install
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim /Show:Clients
```
**Windows Server 2008 R2**若要查看有关通过 Office 进行名为 Vista 的映像的传输的信息，请键入下列内容之一：
```
wdsutil /Get-MulticastTransmissiomedia:Vista with Office
 /Imagetype:Install
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim /details:Clients
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServemedia:X64 Boot Imagemediatype:Boot /Architecture:x64 /Filename:boot.wim /details:Clients
```
## <a name="additional-references"></a>其他参考
- [使用](command-line-syntax-key.md)
[AllMulticastTransmissions 命令](using-the-get-allmulticasttransmissions-command.md)
的命令行语法键使用 MulticastTransmission 命令，使用[MulticastTransmission 命令](using-the-remove-multicasttransmission-command.md)
子[命令](using-the-new-multicasttransmission-command.md)
[： start-MulticastTransmission](subcommand-start-multicasttransmission.md)
