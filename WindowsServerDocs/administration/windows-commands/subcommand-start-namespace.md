---
title: 子命令开始-命名空间
description: 子命令开始-命名空间的参考文章，用于启动计划强制转换命名空间。
ms.topic: reference
ms.assetid: 2dd1c11e-6ab7-4129-9e3a-3f80e0ba59c0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9d37921024c1f92f97687c7b0a4a0714192fe564
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633919"
---
# <a name="subcommand-start-namespace"></a>子命令：起始-命名空间

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启动计划强制转换命名空间。

## <a name="syntax"></a>语法
```
wdsutil /start-Namespace /Namespace:<Namespace name[/Server:<Server name>]
```
### <a name="parameters"></a>参数

|          参数          |                                                                                                                                                                                             说明                                                                                                                                                                                             |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Namespace： <命名空间名称| 指定命名空间的名称。 请注意，这不是友好名称，并且必须是唯一的。<p>-   **部署服务器**：命名空间名称的语法为/NAMSPACE： WDS： <Image group> / <Image name> / <Index> 。 例如： **WDS： ImageGroup1/install/1**<br />-   **传输服务器**：此名称必须与在服务器上创建命名空间时为命名空间指定的名称相匹配。 |
|   [/Server： <Server name> ]   |                                                                                                           指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。                                                                                                           |

## <a name="examples"></a>示例
若要启动命名空间，请键入下列内容之一：
```
wdsutil /start-Namespace /Namespace:Custom Auto 1
wdsutil /start-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllNamespaces 命令](using-the-get-allnamespaces-command.md) 
[使用新的命名空间命令](using-the-new-namespace-command.md) 
[使用移除命名空间命令](using-the-remove-namespace-command.md)
