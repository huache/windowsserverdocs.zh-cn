---
title: MulticastTransmission
description: MulticastTransmission 的参考文章，用于禁用映像的多播传输。
ms.topic: reference
ms.assetid: 9a7f5c31-bfbf-425d-9129-a6f9173fe83d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 680894f9a8f5d73d4bc71511ce006f82f04d0b5c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636399"
---
# <a name="using-the-remove-multicasttransmission-command"></a>使用 MulticastTransmission 命令

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

禁用映像的多播传输。 除非指定 **/force**，否则现有的客户端将完成映像传输，但不允许新客户端加入。

## <a name="syntax"></a>语法
**Windows Server 2008**
```
wdsutil /remove-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image Group>] [/Filename:<File name>] [/force]
```
用于启动映像的**Windows Server 2008 R2** ：
```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
\x20    [/Server:<Server name>]
\x20  mediatype:Boot
\x20    /Architecture:{x86 | ia64 | x64}
\x20    [/Filename:<File name>]
```
对于安装映像：
```
wdsutil [Options] /remove-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group
        [/Filename:<File name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
许可证<Image name>|指定映像的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名 (FQDN) 。 如果未指定服务器名称，则使用本地服务器。|
媒体： {Install&#124;Boot}|指定映像类型。 请注意，必须将此选项设置为 "为 Windows Server 2008 **安装** "。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定与要启动的传输关联的启动映像的体系结构。 由于不同体系结构中的启动映像可能具有相同的映像名称，因此应指定体系结构以确保使用正确的传输。|
|\mediaGroup： <Image group name> ]|指定包含图像的映像组。 如果未指定映像组名称，并且服务器上只存在一个映像组，则使用该映像组。 如果服务器上存在多个映像组，则必须使用此选项来指定映像组名称。|
|[/Filename： <File name> ]|指定文件名。 如果无法按名称唯一地标识源映像，则必须使用此选项指定文件名。|
|/force|删除传输并终止所有客户端。 除非指定了 **/force** 选项的值，否则现有的客户端可以完成映像传输，而新客户端将无法加入。|
## <a name="examples"></a>示例
若要停止命名空间 (当前客户端将完成传输，但新客户端将无法联接) ，请键入：
```
wdsutil /remove-MulticastTransmissiomedia:Vista with Office
/Imagetype:Install
```
```
wdsutil /remove-MulticastTransmissiomedia:x64 Boot Image
/Imagetype:Boot /Architecture:x64
```
若要强制终止所有客户端，请键入：
```
wdsutil /remove-MulticastTransmission /Server:MyWDSServer
/Image:Vista with Officemediatype:InstalmediaGroup:ImageGroup1
/Filename:install.wim /force
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllMulticastTransmissions 命令](using-the-get-allmulticasttransmissions-command.md) 
[使用 MulticastTransmission 命令](using-the-get-multicasttransmission-command.md) 
[使用 MulticastTransmission 命令](using-the-new-multicasttransmission-command.md) 
[子命令： MulticastTransmission](subcommand-start-multicasttransmission.md)
