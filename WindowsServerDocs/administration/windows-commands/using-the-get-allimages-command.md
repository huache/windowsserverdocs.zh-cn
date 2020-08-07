---
title: AllImages
description: AllImages 的参考文章，用于检索有关服务器上所有映像的信息。
ms.topic: article
ms.assetid: 19de3720-4315-415a-8dc6-486caa0b2100
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 542de8f24f8bbb85a44fdefa9d25ca9acda66ba5
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892034"
---
# <a name="get-allimages"></a>AllImages

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

检索有关服务器上所有映像的信息。

## <a name="syntax"></a>语法
```
wdsutil /Get-AllImages [/Server:<Server name>] /Show:{Boot | Install | LegacyRis | All} [/detailed]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
|/Show： {Boot &#124; 安装 &#124; LegacyRis &#124; 全部}|-   **Boot**仅返回启动映像。<br />-   **Install**返回安装映像以及包含它们的映像组的相关信息。<br />-   **LegacyRis**只 (RIS) 映像返回远程安装服务。<br />-   **All**返回启动映像信息、安装映像信息 (包括有关映像组) 的信息，以及 RIS 映像信息。|
|[/detailed]|指示应返回每个图像中的所有图像元数据。 如果未使用此选项，则默认行为是只返回映像名称、说明和文件名。|
## <a name="examples"></a>示例
若要查看有关图像的信息，请键入下列内容之一：
```
wdsutil /Get-AllImages /Show:Install
wdsutil /verbose /Get-AllImages /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 "添加图像" 命令](using-the-add-image-command.md) 
[使用复制映像命令](using-the-copy-image-command.md) 
[使用导出映像命令](using-the-export-image-command.md) 
[使用删除图像命令](using-the-remove-image-command.md) 
[使用 Replace 图像命令](using-the-replace-image-command.md) 
[子命令：设置-图像](subcommand-set-image.md)
