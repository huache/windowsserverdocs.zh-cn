---
title: AllNamespaces
description: 用于 AllNamespaces 的 Windows 命令主题，该主题显示有关服务器上的所有命名空间的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e8fe896d-a69a-4180-923b-9f18185f5941
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bbdba81f68f609c6ed7ba740b68b1ac1123913ab
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831250"
---
# <a name="get-allnamespaces"></a>AllNamespaces

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示有关服务器上的所有命名空间的信息。

## <a name="syntax"></a>语法
Windows Server 2008：
```
wdsutil /Get-AllNamespaces [/Server:<Server name>] [/ContentProvider:<name>] [/Show:Clients] [/ExcludedeletePending]
```
Windows Server 2008 R2：
```
wdsutil /Get-AllNamespaces [/Server:<Server name>] [/ContentProvider:<name>] [/details:Clients] [/ExcludedeletePending]
```
### <a name="parameters"></a>参数

|         参数         |                                                                               Windows Server 2008                                                                               | Windows Server 2008 R2 |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------|
|  [/Server：<Server name>]  | 指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。 |                        |
| [/ContentProvider：<name>] |                                                        仅显示指定内容提供程序的命名空间。                                                         |                        |
|      [/Show：个客户端]      |                            仅支持 Windows Server 2008。 显示有关连接到命名空间的客户端计算机的信息。                             |                        |
|    [/details：客户端]     |                           仅支持 Windows Server 2008 R2。 显示有关连接到命名空间的客户端计算机的信息。                           |                        |
|  [/ExcludedeletePending]  |                                                              从列表中排除任何已停用的传输。                                                              |                        |

## <a name="examples"></a><a name=BKMK_examples></a>示例
若要查看所有命名空间，请键入：
```
wdsutil /Get-AllNamespaces
```
若要查看除已停用的命名空间之外的所有命名空间，请键入：
- Windows Server 2008
  ```
  wdsutil /Get-AllNamespaces /Server:MyWDSServer /ContentProvider:MyContentProv /Show:Clients /ExcludedeletePending
  ```
- Windows Server 2008 R2
  ```
  wdsutil /Get-AllNamespaces /Server:MyWDSServer /ContentProvider:MyContentProv /details:Clients /ExcludedeletePending
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法键](command-line-syntax-key.md)
  使用[
  的](using-the-remove-namespace-command.md)[新命名空间命令](using-the-new-namespace-command.md)
  [子命令：启动-命名](subcommand-start-namespace.md)空间
