---
title: reset session
description: 用于重置会话命令的参考文章，可用于重置远程桌面会话主机服务器上的会话。
ms.topic: reference
ms.assetid: 4f029ecc-874e-415a-95a8-8b731bae35f9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: a154ffb27ac8ead093c0e41f9a50d0952b736abc
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037025"
---
# <a name="reset-session"></a>reset session

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使你能够重置远程桌面会话主机服务器上的会话)  (删除。 只有会话运行不正常或似乎已停止响应时，才应重置会话。

> [!NOTE]
> 若要了解最新版本中的新增功能，请参阅 [Windows Server 中远程桌面服务的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
reset session {<sessionname> | <sessionID>} [/server:<servername>] [/v]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `<sessionname>` | 指定要重置的会话的名称。 若要确定会话的名称，请使用 " [查询会话" 命令](query-session.md)。 |
| `<sessionID>` | 指定要重置的会话的 ID。 |
| /server:`<servername>` | 指定包含要重置的会话的终端服务器。 否则，它将使用当前远程桌面会话主机服务器。 仅当从远程服务器使用此命令时，此参数才是必需的。 |
| /v | 显示要执行的操作的相关信息。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="remarks"></a>注解

- 你可以始终重置自己的会话，但必须具有 " **完全控制** " 访问权限才能重置其他用户的会话。 请注意，在不发出警告的情况下重置用户会话可能导致会话中的数据丢失。

## <a name="examples"></a>示例

若要重置指定的 *rdp-tcp # 6*会话，请键入：

```
reset session rdp-tcp#6
```

若要重置使用 *会话 ID 3*的会话，请键入：

```
reset session 3
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [远程桌面服务命令参考](remote-desktop-services-terminal-services-command-reference.md)
