---
title: tskill
description: Tskill 的参考文章，用于结束在远程桌面会话主机服务器上的会话中运行的进程。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 08986e6a-6900-4ece-85a1-8f73b14db1b3 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5e4e32bada68b8c7d931b8603fbf09eba45791d
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954879"
---
# <a name="tskill"></a>tskill

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

结束在远程桌面会话主机服务器上的会话中运行的进程。


> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](/previous-versions/orphan-topics/ws.11/hh831527(v=ws.11))。

## <a name="syntax"></a>语法
```
tskill {<ProcessID> | <ProcessName>} [/server:<ServerName>] [/id:<SessionID> | /a] [/v]
```

### <a name="parameters"></a>参数

|参数|说明|
|-------|--------|
|\<ProcessID>|指定要结束的进程的 ID。|
|\<ProcessName>|指定要结束的进程的名称。 此参数可以包含通配符。|
|/server:\<ServerName>|指定包含要结束的进程的终端服务器。 如果未指定 **/server** ，则使用当前 RD 会话主机服务器。|
|/id\<SessionID>|结束在指定的会话中运行的进程。|
|/a|结束所有会话中正在运行的进程。|
|/v|显示要执行的操作的相关信息。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
- 除非你是管理员，否则可以使用**tskill**仅结束属于你的进程。 管理员对所有**tskill**函数具有完全访问权限，并且可以结束其他用户会话中运行的进程。
- 如果会话中正在运行的所有进程均结束，该进程也将结束。
- 如果使用*ProcessName*和 **/server：**<em>ServerName</em>参数，则还必须指定 **/id：**<em>SessionID</em>或 **/a**参数。

## <a name="examples"></a>示例
- 若要结束进程6543，请键入：
  ```
  tskill 6543
  ```
- 若要结束在会话5上运行的进程资源管理器，请键入：
  ```
  tskill explorer /id:5
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法关键字](command-line-syntax-key.md) 
  [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
