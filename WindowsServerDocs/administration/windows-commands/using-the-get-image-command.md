---
title: 获取-映像
description: 用于获取映像的 Windows 命令主题，它检索有关映像的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ecaa999-72ad-4191-adb5-a418de42a001
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cfebb8948d21d4f09855683bbf6c42d725d877e8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831000"
---
# <a name="get-image"></a>获取-映像

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

检索有关映像的信息。

## <a name="syntax"></a>语法
对于启动映像：
```
wdsutil [Options] /Get-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>]
```
对于安装映像：
```
wdsutil [Options] /Get-Imagmedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] [/Filename:<File name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
媒体：<Image name>|指定映像的名称。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
媒体： {Boot &#124; Install}|指定图像的类型。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定图像的体系结构。 由于不同体系结构中的启动映像可能具有相同的映像名称，因此指定体系结构值可确保返回正确的映像。|
|[/Filename：<File name>]|如果无法按名称唯一地标识映像，则必须使用此选项指定文件名。|
|\mediaGroup：<Image group name>]|指定包含图像的映像组。 如果未指定映像组并且服务器上只存在一个映像组，则将使用该组。 如果服务器上存在多个映像组，则必须使用此参数来指定映像组。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要检索有关启动映像的信息，请键入下列内容之一：
```
wdsutil /Get-Imagmedia:WinPE boot imagemediatype:Boot /Architecture:x86
wdsutil /verbose /Get-Imagmedia:WinPE boot image /Server:MyWDSServemediatype:Boot /Architecture:x86 /Filename:boot.wim
```
若要检索有关安装映像的信息，请键入下列内容之一：
```
wdsutil /Get-Imagmedia:Windows Vista with Officemediatype:Install
wdsutil /verbose /Get-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用 "添加图像"](using-the-add-image-command.md)命令
使用 "[复制映像](using-the-copy-image-command.md)" 命令
使用 "[输出](using-the-export-image-command.md)映像" 命令
使用 "替换图像"[命令
](using-the-remove-image-command.md) [使用 "替换图像](using-the-replace-image-command.md)" 命令
[子](subcommand-set-image.md)命令
