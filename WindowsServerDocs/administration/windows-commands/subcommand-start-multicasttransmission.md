---
title: 子命令开始-MulticastTransmission
description: 用于启动映像的计划强制转换的子 MulticastTransmission 的参考文章。
ms.topic: reference
ms.assetid: a1b2d459-1ece-49d4-997c-9d206c463b61
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c6af2887e69b88d5c253ea2c9e8632f2493ea19f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633918"
---
# <a name="subcommand-start-multicasttransmission"></a>子命令： MulticastTransmission

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启动映像的计划强制转换。

## <a name="syntax"></a>语法
**Windows Server 2008**
```
wdsutil /start-MulticastTransmissiomedia:<Image name> [/Server:<Server namemediatype:InstallmediaGroup:<Image group name>] [/Filename:<File name>]
```
用于启动映像的**Windows Server 2008 R2** ：
```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
对于安装映像：
```
wdsutil [Options] /start-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
      mediatype:Install
       mediaGroup:<Image Group>]
        [/Filename:<File name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
许可证<Image name>|指定映像的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
媒体： {Install&#124;Boot}|指定映像类型。 请注意，必须将此选项设置为 "为 Windows Server 2008 **安装** "。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|与要启动的传输关联的启动映像的体系结构。 由于不同体系结构中的启动映像可能具有相同的映像名称，因此应指定体系结构以确保使用正确的传输。|
|\mediaGroup： <Image group name> ]|指定图像的图像组。 如果未指定映像组名称，并且服务器上只存在一个映像组，则将使用该映像组。 如果服务器上存在多个映像组，则必须使用此选项来指定映像组名称。|
|[/Filename： <File name> ]|指定包含图像的文件的名称。 如果无法按名称唯一地标识映像，则必须使用此选项指定文件名。|
## <a name="examples"></a>示例
若要开始多播传输，请键入下列内容之一：
```
wdsutil /start-MulticastTransmissiomedia:Vista with Office
/Imagetype:Install
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:Vista with Officemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
若要为 Windows Server 2008 R2 启动启动映像多播传输，请键入：
```
wdsutil /start-MulticastTransmission /Server:MyWDSServemedia:X64 Boot Imagemediatype:Boot /Architecture:x64
/Filename:boot.wim\n\
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllMulticastTransmissions 命令](using-the-get-allmulticasttransmissions-command.md) 
[使用 MulticastTransmission 命令](using-the-get-multicasttransmission-command.md) 
[使用 MulticastTransmission 命令](using-the-new-multicasttransmission-command.md) 
[使用 MulticastTransmission 命令](using-the-remove-multicasttransmission-command.md)
