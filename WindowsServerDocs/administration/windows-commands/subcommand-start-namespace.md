---
title: 子命令开始-命名空间
description: 子命令开始-命名空间的参考主题，用于启动计划强制转换命名空间。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2dd1c11e-6ab7-4129-9e3a-3f80e0ba59c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1562fcb6c61533fcc9994e9011bf7d61154c06f7
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721659"
---
# <a name="subcommand-start-namespace"></a>子命令：起始-命名空间

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启动计划强制转换命名空间。

## <a name="syntax"></a>语法
```
wdsutil /start-Namespace /Namespace:<Namespace name[/Server:<Server name>]
```
### <a name="parameters"></a>参数

|          参数          |                                                                                                                                                                                             描述                                                                                                                                                                                             |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Namespace： <命名空间名称| 指定命名空间的名称。 请注意，这不是友好名称，并且必须是唯一的。<p>-   **部署服务器**：命名空间名称的语法为/NAMSPACE： WDS：<Image group>/<Image name>/<Index>。 例如： **WDS： ImageGroup1/install/1**<br />-   **传输服务器**：此名称必须与在服务器上创建命名空间时为命名空间指定的名称相匹配。 |
|   [/Server：<Server name>]   |                                                                                                           指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。                                                                                                           |

## <a name="examples"></a>示例
若要启动命名空间，请键入下列内容之一：
```
wdsutil /start-Namespace /Namespace:Custom Auto 1
wdsutil /start-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1
```
## <a name="additional-references"></a>其他参考
- [Command-Line Syntax Key](command-line-syntax-key.md)
[使用 AllNamespaces 命令](using-the-get-allnamespaces-command.md)
的命令行语法键使用带有[remove 命名空间](using-the-remove-namespace-command.md)命令的[新命名空间](using-the-new-namespace-command.md)
命令
