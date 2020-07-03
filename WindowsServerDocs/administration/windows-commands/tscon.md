---
title: tscon
description: Tscon 的参考文章，用于连接到远程桌面会话主机（rd 会话主机）服务器上的另一个会话。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 315a9793-cd10-4987-bb68-89a9d13f7fce
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5679af2a53e28b91712a373e8d3c5d63850efbe1
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934208"
---
# <a name="tscon"></a>tscon

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

连接到远程桌面会话主机服务器上的另一个会话。



> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法
```
tscon {<SessionID> | <SessionName>} [/dest:<SessionName>] [/password:<pw> | /password:*] [/v]
```
### <a name="parameters"></a>参数

|参数|说明|
|-------|--------|
|\<SessionID>|指定要连接到的会话的 ID。 如果使用可选的 **/dest：** < *SessionName*> 参数，则这是要连接到的会话的 ID。|
|\<SessionName>|指定要连接到的会话的名称。|
|/dest\<SessionName>|指定当前会话的名称。 当你连接到新的会话时，此会话将断开连接。|
|/password\<pw>|指定拥有要连接到的会话的用户的密码。 当连接用户不拥有会话时，此密码是必需的。|
|/password： *|提示输入拥有要连接到的会话的用户的密码。|
|/v|显示要执行的操作的相关信息。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
-   您必须具有 "完全控制" 访问权限或 "连接" 特殊访问权限才能连接到另一个会话。
-   使用 **/dest：** < *SessionName*> 参数，可以将另一个用户的会话连接到不同的会话。
-   如果未在 <*password*> 参数中指定密码，并且目标会话所属的用户不是当前用户，则**tscon**会失败。
-   你无法连接到控制台会话。

## <a name="examples"></a>示例
- 若要连接到当前 rd 会话主机服务器上的会话12并断开当前会话的连接，请键入：
  ```
  tscon 12
  ```
- 若要通过使用密码 mypass 连接到当前 rd 会话主机服务器上的会话23并断开当前会话的连接，请键入：
  ```
  tscon 23 /password:mypass
  ```
- 若要将名为 TERM03 的会话连接到名为 TERM05 的会话，然后断开连接会话 TERM05 （如果已连接），请键入：
  ```
  tscon TERM03 /v /dest:TERM05
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法关键字](command-line-syntax-key.md) 
  [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
