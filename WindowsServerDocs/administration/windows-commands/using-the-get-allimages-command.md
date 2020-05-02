---
title: AllImages
description: AllImages 的参考主题，它检索有关服务器上所有映像的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 19de3720-4315-415a-8dc6-486caa0b2100
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1f32a1789b22d04b7b61979d0ea49d91f0cf157
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720021"
---
# <a name="get-allimages"></a>AllImages

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

检索有关服务器上所有映像的信息。

## <a name="syntax"></a>语法
```
wdsutil /Get-AllImages [/Server:<Server name>] /Show:{Boot | Install | LegacyRis | All} [/detailed]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
|/Show： {Boot &#124; 安装 &#124; LegacyRis &#124; 全部}|-   **Boot**仅返回启动映像。<br />-   **Install**返回安装映像以及包含它们的映像组的相关信息。<br />-   **LegacyRis**仅返回远程安装服务（RIS）映像。<br />-   **All**返回启动映像信息、安装映像信息（包括映像组的相关信息）和 RIS 映像信息。|
|[/detailed]|指示应返回每个图像中的所有图像元数据。 如果未使用此选项，则默认行为是只返回映像名称、说明和文件名。|
## <a name="examples"></a>示例
若要查看有关图像的信息，请键入下列内容之一：
```
wdsutil /Get-AllImages /Show:Install
wdsutil /verbose /Get-AllImages /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[Using the add-Image Command](using-the-add-image-command.md)
使用 "复制映像" 命令通过 "[复制映像](using-the-copy-image-command.md)
" 命令使用 "复制映像
" 命令使用 "[替换](using-the-replace-image-command.md)
图像命令"[命令使用 "](using-the-export-image-command.md)[删除](using-the-remove-image-command.md)
图像" 命令[：设置-图像](subcommand-set-image.md)
