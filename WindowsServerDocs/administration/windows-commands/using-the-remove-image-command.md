---
title: 删除-映像
description: 删除映像的参考文章，用于从服务器中删除映像。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce5e2384-2264-4b22-92af-74eec8c10ae0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: badcb079b12cf4357cba85d5711cfc5b6a50a2a4
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931240"
---
# <a name="remove-image"></a>删除-映像

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从服务器中删除映像。

## <a name="syntax"></a>语法
对于启动映像：
```
wdsutil [Options] /remove-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<Filename>]
```
对于安装映像：
```
wdsutil [Options] /remove-Imagmedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>] [/Filename:<Filename>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
许可证<Image name>|指定映像的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
媒体： {Boot &#124; 安装}|指定图像的类型。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定图像的体系结构。 由于不同体系结构中的不同启动映像可能具有相同的映像名称，因此指定体系结构值可确保删除正确的映像。|
|\mediaGroup： <Image group name> ]|指定包含图像的映像组。 如果未指定映像组名称，并且服务器上只存在一个映像组，则将使用该映像组。 如果存在多个映像组，则必须使用此选项来指定映像组。|
|[/Filename： <File name> ]|如果无法按名称唯一地标识映像，则必须使用此选项指定文件名。|
## <a name="examples"></a>示例
若要删除启动映像，请键入：
```
wdsutil /remove-Imagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86
```
```
wdsutil /verbose /remove-Imagmedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filename:boot.wim
```
若要删除安装映像，请键入：
```
wdsutil /remove-Imagmedia:Windows Vista with Officemediatype:Install
```
```
wdsutil /verbose /remove-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 /Filename:install.wim
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 "添加图像" 命令](using-the-add-image-command.md) 
[使用复制映像命令](using-the-copy-image-command.md) 
[使用导出映像命令](using-the-export-image-command.md) 
[使用 Get Image 命令](using-the-get-image-command.md) 
[使用 Replace 图像命令](using-the-replace-image-command.md) 
[子命令：设置-图像](subcommand-set-image.md)
