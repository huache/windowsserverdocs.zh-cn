---
title: 子命令集-映像
description: 子命令集-Image 的参考文章，用于更改映像的属性。
ms.topic: article
ms.assetid: 2ae03c86-7a13-4e38-9182-32e55fffd504
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 35fff7823b730c4b9cc98ed2daafd437f6eecc2e
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87882195"
---
# <a name="subcommand-set-image"></a>子命令：设置-图像

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改映像的属性。

## <a name="syntax"></a>语法
对于启动映像：
```
wdsutil /Set-Imagmedia:<Image name> [/Server:<Server name>mediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>] [/Name:<Name>]
[/Description:<Description>] [/Enabled:{Yes | No}]
```
对于安装映像：
```
wdsutil /Set-Imagmedia:<Image name> [/Server:<Server name>]
   mediatype:InstallmediaGroup:<Image group name>]
     [/Filename:<File name>]
     [/Name:<Name>]
     [/Description:<Description>]
     [/UserFilter:<SDDL>]
     [/Enabled:{Yes | No}]
     [/UnattendFile:<Unattend file path>]
         [/OverwriteUnattend:{Yes | No}]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
许可证<Image name>|指定映像的名称。|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
媒体： {Boot &#124; 安装}|指定图像的类型。|
|/Architecture： {x86 &#124; ia64 &#124; x64}|指定图像的体系结构。 由于不同体系结构中不同的启动映像可以具有相同的映像名称，因此指定体系结构可确保修改正确的映像。|
|[/Filename： <File name> ]|如果无法按名称唯一地标识映像，则必须使用此选项指定文件名。|
|/Name|指定映像的名称。|
|/Description<Description>]|设置映像的说明。|
|[/Enabled： {Yes &#124; No}]|启用或禁用图像。|
|\mediaGroup： <Image group name> ]|指定包含图像的映像组。 如果未指定映像组名称，并且服务器上只存在一个映像组，则将使用该映像组。 如果服务器上存在多个映像组，则必须使用此选项来指定映像组。|
|[/UserFilter： <SDDL> ]|设置图像上的用户筛选器。 筛选器字符串必须采用安全描述符定义语言 (SDDL) 格式。 请注意，与图像组的 **/Security**选项不同，此选项仅限制可查看图像定义的用户，而不限制实际图像文件资源。 若要限制对文件资源的访问权限，从而限制对映像组中的所有映像的访问，你将需要为映像组本身设置安全性。|
|[/UnattendFile： <Unattend file path> ]|设置要与映像关联的无人参与文件的完整路径。 例如： **D:\Files\Unattend\Img1Unattend.xml**|
|[/OverwriteUnattend： {Yes &#124; No}]|如果已有与映像关联的无人参与文件，则可以指定 **/Overwrite**来覆盖无人参与文件。 请注意，默认设置为 "**否**"。|
## <a name="examples"></a>示例
若要设置启动映像的值，请键入下列内容之一：
```
wdsutil /Set-Imagmedia:WinPE boot imagemediatype:Boot /Architecture:x86 /Description:New description
wdsutil /verbose /Set-Imagmedia:WinPE boot image /Server:MyWDSServemediatype:Boot /Architecture:x86 /Filename:boot.wim
/Name:New Name /Description:New Description /Enabled:Yes
```
若要设置安装映像的值，请键入下列内容之一：
```
wdsutil /Set-Imagmedia:Windows Vista with Officemediatype:Install /Description:New description
wdsutil /verbose /Set-Imagmedia:Windows Vista with Office /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1
/Filename:install.wim /Name:New name /Description:New description /UserFilter:O:BAG:DUD:AI(A;ID;FA;;;SY)(A;ID;FA;;;BA)(A;ID;0x1200a9;;;AU) /Enabled:Yes /UnattendFile:\\server\share\unattend.xml /OverwriteUnattend:Yes
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 "添加图像" 命令](using-the-add-image-command.md) 
[使用复制映像命令](using-the-copy-image-command.md) 
[使用导出映像命令](using-the-export-image-command.md) 
[使用 Get Image 命令](using-the-get-image-command.md) 
[使用删除图像命令](using-the-remove-image-command.md) 
[使用 Replace 图像命令](using-the-replace-image-command.md)
