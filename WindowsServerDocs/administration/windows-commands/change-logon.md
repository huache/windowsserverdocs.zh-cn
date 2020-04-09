---
title: change logon
description: "\"更改登录\" 的 Windows 命令主题，用于启用或禁用来自客户端会话的登录，或者显示当前登录状态。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 41466260-aee9-4333-bcb6-178112c22afd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6a101fc567981716536ecad8e754b81a43eb2c91
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848150"
---
# <a name="change-logon"></a>change logon

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

启用或禁用来自客户端会话的登录，或者显示当前登录状态。 此实用程序对于系统维护非常有用。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

> [!NOTE]
> 在 Windows Server 2008 R2 中，“终端服务”被重命名为“远程桌面服务”。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法
```
change logon {/query | /enable | /disable | /drain | /drainuntilrestart}
```
### <a name="parameters"></a>参数

|     参数      |                                                       说明                                                        |
|--------------------|--------------------------------------------------------------------------------------------------------------------------|
|       /query       |                             显示当前登录状态，不管是启用还是禁用。                              |
|      /enable       |                              允许来自客户端会话的登录，但不允许来自控制台的登录。                              |
|      /disable      |  禁止来自客户端会话的后续登录，而不是从控制台中登录。 不会影响当前登录的用户。   |
|       /drain       |                 禁止从新客户端会话登录，但允许重新断开现有会话的登录。                 |
| /drainuntilrestart | 禁止在重新启动计算机之前从新的客户端会话登录，但允许重新与现有会话进行重新启动。 |
|         /?         |                                           在命令提示符下显示帮助。                                           |

## <a name="remarks"></a>备注
- 只有管理员才能使用**change logon**命令。
- 重新启动系统时，将重新启用登录。 如果从客户端会话连接到远程桌面会话主机（rd 会话主机）服务器并禁用登录，然后在重新启用登录之前注销，则无法重新连接到会话。 若要重新启用来自客户端会话的登录，请在控制台上登录。

## <a name="examples"></a><a name=BKMK_examples></a>示例

- 若要显示当前登录状态，请键入：
  ```
  change logon /query
  ```
- 若要允许从客户端会话登录，请键入：
  ```
  change logon /enable
  ```
- 若要禁用客户端登录，请键入：
  ```
  change logon /disable
  ```
  
## <a name="additional-references"></a>其他参考
- - [命令行语法项](command-line-syntax-key.md)
- [change](change.md)
- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
