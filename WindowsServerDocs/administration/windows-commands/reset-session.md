---
title: reset session
description: '* * * * 的参考文章'
ms.topic: article
ms.assetid: 4f029ecc-874e-415a-95a8-8b731bae35f9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 2f910dfc1c13b0e8555078acfb4e7ad830049592
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87883662"
---
# <a name="reset-session"></a>reset session

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使你能够重置远程桌面会话主机 (rd 会话主机) server 上的会话)  (删除。


> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](/previous-versions/orphan-topics/ws.11/hh831527(v=ws.11))。

## <a name="syntax"></a>语法
```
reset session {<SessionName> | <SessionID>} [/server:<ServerName>] [/v]
```

### <a name="parameters"></a>参数

|参数|描述|
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
[远程桌面服务 (终端服务) 命令参考](remote-desktop-services-terminal-services-command-reference.md)
