---
title: taskkill
description: Taskkill 的参考文章，用于结束一个或多个任务或进程。
ms.topic: reference
ms.assetid: 2b71e792-08b6-46d4-95a5-cb6336a79524
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f750f7487e8220c93ea30a78ee185f28a74fd512
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622367"
---
# <a name="taskkill"></a>taskkill

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

结束一个或多个任务或进程。 可以通过进程 ID 或图像名称结束进程。 **taskkill** 替换 **kill** 工具。

有关如何使用此命令的示例，请参阅[示例](#examples)。

## <a name="syntax"></a>语法

```
taskkill [/s <computer> [/u [<Domain>\]<UserName> [/p [<Password>]]]] {[/fi <Filter>] [...] [/pid <ProcessID> | /im <ImageName>]} [/f] [/t]
```

### <a name="parameters"></a>参数

|         参数         |                                                                                                                                        说明                                                                                                                                        |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      /s \<computer>       |                                                                                    指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。                                                                                     |
| /u \<Domain>\\\<UserName> | 使用*用户名*或*域*用户名指定的用户的帐户权限运行命令 \\ *UserName*。 只有指定 **/s**时才能指定 **/u** 。 默认值是当前登录到发出命令的计算机的用户的权限。 |
|      /p \<Password>       |                                                                                                   指定在 **/u** 参数中指定的用户帐户的密码。                                                                                                   |
|       /fi \<Filter>       |          应用筛选器以选择一组任务。 可以使用多个筛选器，也可以使用通配符 (**\\** \*) 来指定所有任务或映像名称。 [有关有效的筛选器名称](#filter-names-operators-and-values)、运算符和值，请参阅下表。           |
|     /pid \<ProcessID>     |                                                                                                                 指定要终止的进程的进程 ID。                                                                                                                 |
|     /im \<ImageName>      |                                                                                指定要终止的进程的映像名称。 使用通配符 (**\\** \*) 指定所有映像名称。                                                                                |
|            /f             |                                                                    指定强制终止进程。 对于远程进程，此参数将被忽略。所有远程进程都被强制终止。                                                                     |
|            /t              |                                                                                                          终止指定的进程以及由该进程启动的任何子进程。                                                                                                          |

#### <a name="filter-names-operators-and-values"></a>筛选器名称、运算符和值

| 筛选器名称 |    有效的运算符     |                                                                有效值 (s)                                                                 |
|-------------|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|   状态    |         eq、ne         |                                                 运行 &#124; 没有响应 &#124; 未知                                                 |
|  IMAGENAME  |         eq、ne         |                                                                  映像名称                                                                  |
|     PID     | eq、ne、gt、lt、ge、le |                                                                  PID 值                                                                   |
|   SESSION   | eq、ne、gt、lt、ge、le |                                                                会话号                                                                |
|   CPUtime   | eq、ne、gt、lt、ge、le | 采用 <em>HH</em>**：**<em>MM</em>**：**<em>SS</em>格式的 CPU 时间，其中 *MM* 和 *SS* 介于0到59之间， *HH* 是任意无符号数字 |
|  MEMUSAGE   | eq、ne、gt、lt、ge、le |                                                              内存使用量（KB）                                                              |
|  USERNAME   |         eq、ne         |                                               *用户*或*域*用户 (的任何有效用户名 \\ *User*)                                                |
|  服务   |         eq、ne         |                                                                 服务名称                                                                 |
| SYSTEM.WINDOWS.CONTROLS.PAGE.WINDOWTITLE |         eq、ne         |                                                                 窗口标题                                                                 |
|   模块   |         eq、ne         |                                                                   DLL 名称                                                                   |

## <a name="remarks"></a>备注
* 指定远程系统时，不支持 SYSTEM.WINDOWS.CONTROLS.PAGE.WINDOWTITLE 和 STATUS 筛选器。
* **\\**仅当应用了筛选器时，才<em>接受 **/im</em> *选项 () 通配符。
* 不管是否指定了 **/f** 选项，远程进程的终止始终都是强制执行的。
* 向主机名筛选器提供计算机名称将导致关闭并停止所有进程。
* 您可以使用 **tasklist** 来确定进程 ID (PID) 以终止进程。

## <a name="examples"></a>示例

若要结束进程 Id 为1230、1241和1253的进程，请键入：

```
taskkill /pid 1230 /pid 1241 /pid 1253
```

若要在系统启动进程 Notepad.exe 强制结束进程，请键入：

```
taskkill /f /fi USERNAME eq NT AUTHORITY\SYSTEM /im notepad.exe
```

若要结束远程计算机上的所有进程 Srvmain 使用映像名称开头，请注意，使用用户帐户 Hiropln 的凭据时，请键入：

```
taskkill /s srvmain /u maindom\hiropln /p p@ssW23 /fi IMAGENAME eq note* /im *
```

若要结束进程 ID 为2134的进程及其启动的任何子进程，但仅当这些进程已由管理员帐户启动时，请键入：

```
taskkill /pid 2134 /t /fi username eq administrator
```

若要结束所有进程 ID 大于或等于1000的进程，无论其映像名称如何，请键入：

```
taskkill /f /fi PID ge 1000 /im *
```

## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
