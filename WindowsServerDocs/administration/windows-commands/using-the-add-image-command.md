---
title: 添加图像
description: 有关添加映像的参考文章，可将图像添加到 Windows 部署服务服务器。
ms.topic: reference
ms.assetid: d5b6f4da-90ba-4b0e-9423-66c8ef5172e2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 03f7a024b2d396f54db66a48353557f776552db1
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029825"
---
# <a name="add-image"></a>添加图像

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将图像添加到 Windows 部署服务服务器。

## <a name="syntax"></a>语法
对于启动映像，请使用以下语法：
```
wdsutil /add-ImagmediaFile:<wim file path> [/Server:<Server name>mediatype:Boot [/Skipverify] [/Name:<Image name>] [/Description:<Image description>]
[/Filename:<New wim file name>]
```
对于安装映像，请使用以下语法：
```
wdsutil /add-ImagmediaFile:<wim file path>
     [/Server:<Server name>]
   mediatype:Install
     [/Skipverify]
    mediaGroup:<Image group name>]
     [/SingleImage:<Single image name>]
         [/Name:<Name>]
         [/Description:<Description>]
     [/Filename:<File name>]
     [/UnattendFile:<Unattend file path>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
mediaFile： < .wim 文件路径>|指定包含要添加的映像 () 文件的 Windows 映像的完整路径和文件名。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
媒体： {Boot&#124;安装}|指定要添加的图像的类型。|
|[/Skipverify]|指定在添加映像之前，不会在源映像文件上执行完整性验证。|
|[/Name： <Name> ]|设置图像的显示名称。|
|/Description<Description>]|设置映像的说明。|
|[/Filename： <Filename> ]|指定 .wim 文件的新文件名。 这样，便可以在添加映像时更改 .wim 文件的文件名。 如果未指定文件名，则将使用源映像文件名。 在所有情况下，Windows 部署服务会进行检查以确定文件名在目标计算机的启动映像存储中是否唯一。|
|\mediaGroup： <Image group name> ]|指定要在其中添加图像的映像组的名称。 如果服务器上存在多个映像组，则必须指定映像组。 如果未指定此，并且映像组尚不存在，则将创建新的映像组。 否则，将使用现有的映像组。|
|[/SingleImage： <Single image name> ][/Name： <Name> ]/Description<Description>]|从 .wim 文件复制指定的单一映像，并设置图像的显示名称和说明。|
|[/UnattendFile： <Unattend file path> ]|指定与要添加的映像关联的无人参与安装文件的完整路径。 如果未指定 **/SingleImage** ，则同一无人参与文件将与 .wim 文件中的所有映像相关联。|
## <a name="examples"></a>示例
若要添加启动映像，请键入：
```
wdsutil /add-ImagmediaFile:C:\MyFolder\Boot.wimmediatype:Boot
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share\Boot.wim /Server:MyWDSServemediatype:Boot /Name:My WinPE Image
/Description:WinPE Image containing the WDS Client /Filename:WDSBoot.wim
```
若要添加安装映像，请键入下列内容之一：
```
wdsutil /add-ImagmediaFile:C:\MyFolder\Install.wimmediatype:Install
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share \Install.wim /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1
/SingleImage:Windows Pro /Name:My WDS Image
/Description:Windows Pro image with Microsoft Office /Filename:Win Pro.wim /UnattendFile:\\server\share\unattend.xml
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用复制映像命令](using-the-copy-image-command.md) 
[使用导出映像命令](using-the-export-image-command.md) 
[使用 Get Image 命令](using-the-get-image-command.md) 
[使用删除图像命令](using-the-remove-image-command.md) 
[使用 Replace 图像命令](using-the-replace-image-command.md) 
[子命令：设置-图像](subcommand-set-image.md)
