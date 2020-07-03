---
title: reset session
description: '* * * * 的参考文章'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4f029ecc-874e-415a-95a8-8b731bae35f9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 07ebe7220ec2624dd0dee5e5302be9c98fbd7fa0
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933101"
---
# <a name="reset-session"></a>reset session

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使你能够在远程桌面会话主机（rd 会话主机）服务器上重置（删除）会话。


> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法
```
reset session {<SessionName> | <SessionID>} [/server:<ServerName>] [/v]
```

### <a name="parameters"></a>参数

|参数|说明|
|-------|--------|
|\<SessionName>|指定要重置的会话的名称。 若要确定会话的名称，请使用 "**查询会话**" 命令。|
|\<SessionID>|指定要重置的会话的 ID。|
|/server:\<ServerName>|指定包含要重置的会话的终端服务器。 否则，使用当前的 rd 会话主机服务器。|
|/v|显示要执行的操作的相关信息。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
-   你可以始终重置自己的会话，但必须具有 "完全控制" 访问权限才能重置其他用户的会话。
-   请注意，在不发出警告的情况下重置用户会话可能导致会话中的数据丢失。
-   只有会话运行不正常或似乎已停止响应时，才应重置会话。
-   仅当使用远程服务器上的 "**重置会话**" 时， **/server**参数才是必需的。

## <a name="examples"></a>示例
- 若要重置指定的 rdp-tcp # 6 会话，请键入：
  ```
  reset session rdp-tcp#6
  ```
- 若要重置使用会话 ID 3 的会话，请键入：
  ```
  reset session 3
  ```

## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
