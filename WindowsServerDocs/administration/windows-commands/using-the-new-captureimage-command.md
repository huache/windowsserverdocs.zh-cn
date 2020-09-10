---
title: 新-捕获映像
description: 捕获映像的参考文章，用于根据现有启动映像创建新的捕获映像。
ms.topic: reference
ms.assetid: 2dfd08f0-be59-4715-96e6-c498305873f4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ab582e65ad3f1c9920071260541fefd0125bf428
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627995"
---
# <a name="new-captureimage"></a>新-捕获映像

从现有的启动映像创建新的捕获映像。 捕获映像是启动 Windows 部署服务捕获实用程序（而不是启动安装程序）的启动映像。 启动已使用 Sysprep) 准备的引用计算机 (时，向导将创建引用计算机的安装映像，并将其另存为 Windows 映像 ( .wim) 文件。 你还可以将图像添加到 media (例如 CD、DVD 或 USB 驱动器) ，然后从该媒体启动计算机。 创建安装映像之后，可以将该映像添加到服务器中，以进行 PXE 启动部署。 有关详细信息，请参阅 () 创建映像 [https://go.microsoft.com/fwlink/?LinkId=115311](https://go.microsoft.com/fwlink/?LinkId=115311) 。

## <a name="syntax"></a>语法

```
WDSUTIL [Options] /New-CaptureImage [/Server:<Server name>]
     /Image:<Image name>
     /Architecture:{x86 | ia64 | x64}
     [/Filename:<File name>]
     /DestinationImage
        /FilePath:<File path and name>
        [/Name:<Name>]
        [/Description:<Description>]
        [/Overwrite:{Yes | No | Append}]
        [/UnattendFilePath:<File path>]
```

### <a name="parameters"></a>参数

|        参数         |                                                                                                                                                                                                                         说明                                                                                                                                                                                                                          |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server： \<Server name> ] |                                                                                                                                       指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。                                                                                                                                        |
|   影像\<Image name>   |                                                                                                                                                                                                         指定源启动映像的名称。                                                                                                                                                                                                         |
|   /Architecture： {x86    |                                                                                                                                                                                                                             ia64                                                                                                                                                                                                                             |
| [/Filename： \<Filename> ] |                                                                                                                                                                            如果无法按名称唯一地标识映像，则必须使用此选项指定文件名。                                                                                                                                                                            |
|    /DestinationImage     | 指定目标映像的设置。 使用以下选项指定设置：</br>-/FilePath： \<File path and name> 为新的捕获映像设置完整文件路径。</br>-[/Name： \<Name> ]-设置图像的显示名称。 如果未指定显示名称，将使用源映像的显示名称。</br>-[/Description： \<Description> ]-设置图像的说明。</br>-[/Overwrite： {Yes |

## <a name="examples"></a>示例

若要创建捕获映像并将其命名为 WinPECapture，请键入：
```
WDSUTIL /New-CaptureImage /Image:WinPE boot image /Architecture:x86 /DestinationImage /FilePath:C:\Temp\WinPECapture.wim
```
若要创建捕获映像并应用指定的设置，请键入：
```
WDSUTIL /Verbose /Progress /New-CaptureImage /Server:MyWDSServer /Image:WinPE boot image /Architecture:x64 /Filename:boot.wim
/DestinationImage /FilePath:\\Server\Share\WinPECapture.wim /Name:New WinPE image /Description:WinPE image with capture utility /Overwrite:No /UnattendFilePath:\\Server\Share\WDSCapture.inf
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)