---
title: tasklist
description: 了解如何显示在本地或远程计算机上运行的进程的列表。
ms.topic: reference
ms.assetid: 8dbe30ee-1484-46be-917b-5ca3ff4fdc9c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a57fc47473be3d8d5eb3fabab6f613da283fa231
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640121"
---
# <a name="tasklist"></a>tasklist

显示本地计算机或远程计算机上当前正在运行的进程列表。 **Tasklist** 替换 **tlist.exe** 工具。



## <a name="syntax"></a>语法

```
tasklist [/s <Computer> [/u [<Domain>\]<UserName> [/p <Password>]]] [{/m <Module> | /svc | /v}] [/fo {table | list | csv}] [/nh] [/fi <Filter> [/fi <Filter> [ ... ]]]
```

### <a name="parameters"></a>参数

|          参数           |                                                                                                                                            说明                                                                                                                                             |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        /s \<Computer>        |                                                                                         指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。                                                                                         |
| 形\<Domain>\\\]\<UserName> | 使用*用户名*或*域*用户名指定的用户的帐户权限运行命令 \* <em>。 \* \*</em> \* 只有指定 **/s**时才能指定/u。 默认值是当前登录到发出命令的计算机的用户的权限。 |
|        /p \<Password>        |                                                                                                       指定在 **/u** 参数中指定的用户帐户的密码。                                                                                                        |
|         一样 \<Module>         |                                                               列出与给定模式名称匹配的、加载了 DLL 模块的所有任务。 如果未指定模块名称，此选项将显示每个任务加载的所有模块。                                                                |
|             /svc             |                                                                                    列出每个进程的所有不截断的服务信息。 当 **/fo** 参数设置为 **表**时有效。                                                                                    |
|              /v              |                                                                                 在输出中显示详细的任务信息。 若要在不截断的情况下完成详细的输出，请将 **/v** 和 **/svc** 一起使用。                                                                                 |
|  /fo {表 \| 列表 \| csv}  |                                                                             指定要用于输出的格式。 有效值为 **table**、 **list**和 **csv**。 输出的默认格式为 **table**。                                                                             |
|             /nh              |                                                                                             取消输出中的列标题。 当 **/fo** 参数设置为 **表** 或 **csv**时有效。                                                                                              |
|        /fi \<Filter>         |                                                                          指定要包含在查询中或从查询中排除的进程的类型。 有关有效的筛选器名称、运算符和值，请参阅下表。                                                                          |
|              /?              |                                                                                                                                在命令提示符下显示帮助。                                                                                                                                |

### <a name="filter-names-operators-and-values"></a>筛选器名称、运算符和值

| 筛选器名称 |    有效的运算符     |                                                                 有效值                                                                 |
|-------------|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|   状态    |         eq、ne         |                                                                   RUNNING                                                                    |
|  IMAGENAME  |         eq、ne         |                                                                  映像名称                                                                  |
|     PID     | eq、ne、gt、lt、ge、le |                                                                  PID 值                                                                   |
|   SESSION   | eq、ne、gt、lt、ge、le |                                                                会话号                                                                |
| SESSIONNAME |         eq、ne         |                                                                 “会话名称”                                                                 |
|   CPUTIME   | eq、ne、gt、lt、ge、le | 采用 <em>HH</em>**：**<em>MM</em>**：**<em>SS</em>格式的 CPU 时间，其中 *MM* 和 *SS* 介于0到59之间， *HH* 是任意无符号数字 |
|  MEMUSAGE   | eq、ne、gt、lt、ge、le |                                                              内存使用量（KB）                                                              |
|  USERNAME   |         eq、ne         |                                                             任何有效的用户名                                                              |
|  服务   |         eq、ne         |                                                                 服务名称                                                                 |
| SYSTEM.WINDOWS.CONTROLS.PAGE.WINDOWTITLE |         eq、ne         |                                                                 窗口标题                                                                 |
|   模块   |         eq、ne         |                                                                   DLL 名称                                                                   |

## <a name="remarks"></a>备注

指定远程系统时，不支持 SYSTEM.WINDOWS.CONTROLS.PAGE.WINDOWTITLE 和 STATUS 筛选器。

## <a name="examples"></a><a name="BKMK_examples"></a>示例

若要列出进程 ID 大于1000的所有任务并将其显示为 CSV 格式，请键入：
```
tasklist /v /fi "PID gt 1000" /fo csv
```
若要列出当前正在运行的系统进程，请键入：
```
tasklist /fi "USERNAME ne NT AUTHORITY\SYSTEM" /fi "STATUS eq running"
```
若要列出当前正在运行的所有进程的详细信息，请键入：
```
tasklist /v /fi "STATUS eq running"
```
若要列出远程计算机 "Srvmain" 上其 DLL 名称以 "ntdll.dll" 开头的进程的所有服务信息，请键入：
```
tasklist /s srvmain /svc /fi "MODULES eq ntdll*"
```
要使用当前登录的用户帐户的凭据列出远程计算机 "Srvmain" 上的进程，请键入：
```
tasklist /s srvmain
```
若要使用用户帐户 Hiropln 的凭据列出远程计算机 "Srvmain" 上的进程，请键入：
```
tasklist /s srvmain /u maindom\hiropln /p p@ssW23
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)