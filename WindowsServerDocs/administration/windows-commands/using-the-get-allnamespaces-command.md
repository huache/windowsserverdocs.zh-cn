---
title: AllNamespaces
description: AllNamespaces 的参考文章，用于显示有关服务器上所有命名空间的信息。
ms.topic: reference
ms.assetid: e8fe896d-a69a-4180-923b-9f18185f5941
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b87b1fb3b2a7a1a7bb21f9c5a6a389494532dde5
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626378"
---
# <a name="get-allnamespaces"></a>AllNamespaces

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

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
|  [/Server： <Server name> ]  | 指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。 |                        |
| [/ContentProvider： <name> ] |                                                        仅显示指定内容提供程序的命名空间。                                                         |                        |
|      [/Show：个客户端]      |                            仅支持 Windows Server 2008。 显示有关连接到命名空间的客户端计算机的信息。                             |                        |
|    [/details：客户端]     |                           仅支持 Windows Server 2008 R2。 显示有关连接到命名空间的客户端计算机的信息。                           |                        |
|  [/ExcludedeletePending]  |                                                              从列表中排除任何已停用的传输。                                                              |                        |

## <a name="examples"></a>示例
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
  - [命令行语法关键字](command-line-syntax-key.md) 
  [使用新的命名空间命令](using-the-new-namespace-command.md) 
  [使用移除命名空间命令](using-the-remove-namespace-command.md) 
  [子命令：起始-命名空间](subcommand-start-namespace.md)
