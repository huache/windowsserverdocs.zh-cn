---
title: 替换图像
description: 替换映像的 Windows 命令主题，它使用该映像的新版本替换现有映像。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68ded3df-e309-420f-9f5d-caeb609385a5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8d16ec07171e4560af8074cb9b0be7b6dc252119
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830220"
---
# <a name="using-the-replace-image-command"></a>使用 replace 图像命令

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

使用该映像的新版本替换现有映像。
## <a name="syntax"></a>语法
对于启动映像：
```
wdsutil [Options] /replace-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:Boot
     /Architecture:{x86 | ia64 | x64}
     [/Filename:<File name>]
     /replacementImage
       mediaFile:<wim file path>
         [/Name:<Image name>]
         [/Description:<Image description>]
```
对于安装映像：
```
wdsutil [Options] /replace-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:Install
    mediaGroup:<Image group name>]
     [/Filename:<File name>]
     /replacementImage
       mediaFile:<wim file path>
         [/SourceImage:<Source image name>]
         [/Name:<Image name>]
         [/Description:<Image description>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
媒体：<Image name>|指定要替换的映像的名称。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
媒体： {Boot &#124; Install}|指定要替换的图像的类型。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定要替换的图像的体系结构。 由于不同体系结构中的不同启动映像可能具有相同的映像名称，因此指定体系结构可确保替换正确的映像。|
|[/Filename：<File name>]|如果无法按名称唯一地标识映像，则必须使用此选项指定文件名。|
|/replacementImage|指定替换映像的设置。 使用以下选项设置这些设置：<p>-mediaFile： <file path>-指定新的 .wim 文件的名称和位置（完整路径）。<br />-[/SourceImage： <image name>]-如果 .wim 文件包含多个映像，则指定要使用的映像。 此选项仅适用于安装映像。<br />-[/Name：<Image name>] 设置图像的显示名称。<br />-[/Description：<Image description>]-设置映像的描述。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要替换启动映像，请键入下列内容之一：
```
wdsutil /replace-Imagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86 /replacementImagmediaFile:C:\MyFolder\Boot.wim
wdsutil /verbose /Progress /replace-Imagmedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim 
/replacementImagmediaFile:\\MyServer\Share\Boot.wim /Name:My WinPE Image /Description:WinPE Image with drivers
```
若要替换安装映像，请键入下列内容之一：
```
wdsutil /replace-Imagmedia:Windows Vista Homemediatype:Install /replacementImagmediaFile:C:\MyFolder\Install.wim
wdsutil /verbose /Progress /replace-Imagmedia:Windows Vista Pro /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/Filename:Install.wim /replacementImagmediaFile:\\MyServer\Share \Install.wim /SourceImage:Windows Vista Ultimate /Name:Windows Vista Desktop /Description:Windows Vista Ultimate with standard business applications.
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用 "添加图像"](using-the-add-image-command.md)命令
使用["复制映像](using-the-copy-image-command.md)" 命令
使用 "[输出映像"](using-the-export-image-command.md)命令
使用 "[获取映像](using-the-get-image-command.md)" 命令
使用 "[替换图像"](using-the-replace-image-command.md)命令
[子命令： set-image](subcommand-set-image.md)
