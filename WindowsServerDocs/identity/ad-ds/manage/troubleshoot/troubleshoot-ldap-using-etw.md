---
title: 使用 ETW 排查 LDAP 连接问题
description: 如何打开并使用 ETW 跟踪 AD DS 域控制器之间的 LDAP 连接。
author: Teresa-Motiv
manager: dcscontentpm
ms.prod: windows-server-dev
ms.technology: active-directory-lightweight-directory-services
audience: Admin
ms.author: v-tea
ms.topic: article
ms.date: 11/22/2019
ms.openlocfilehash: 516304498206523a1ce618da6aa21640e38c9654
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965649"
---
# <a name="using-etw-to-troubleshoot-ldap-connections"></a>使用 ETW 排查 LDAP 连接问题

[Windows 事件跟踪（ETW）](/windows/win32/etw/event-tracing-portal)是一个非常有用的故障排除工具，可用于 Active Directory 域服务（AD DS）。 可以使用 ETW 跟踪 Windows 客户端和 LDAP 服务器之间的轻型目录访问协议（[LDAP](/previous-versions/windows/desktop/ldap/lightweight-directory-access-protocol-ldap-api)）通信，包括 AD DS 域控制器。

## <a name="how-to-turn-on-etw-and-start-a-trace"></a>如何打开 ETW 并启动跟踪

**启用 ETW**

1. 打开注册表编辑器，并创建以下注册表子项：

   **HKEY \_ 本地 \_ 计算机 \\ 系统 \\ CurrentControlSet \\ Services \\ ldap \\ 跟踪 \\ * ProcessName***

   在此子项中， *ProcessName*是要跟踪的进程的完整名称，包括其扩展（例如 "Svchost.exe"）。

1. （**可选**）在此子项下，创建一个名为**PID**的新项。 若要使用此项，请将进程 ID 指定为 DWORD 值。  

   如果指定进程 ID，则 ETW 只跟踪具有此进程 ID 的应用程序的实例。

**启动跟踪会话**

- 打开 "命令提示符" 窗口，并运行以下命令：

   ```cmd
   tracelog.exe -start <SessionName> -guid \#099614a5-5dd7-4788-8bc9-e29f43db28fc -f <FileName> -flag <TraceFlags>
   ```

   此命令中的占位符表示以下值。

  - \<*SessionName*>是用于标记跟踪会话的任意标识符。  
  > [!NOTE]  
  > 稍后停止跟踪会话时，必须引用此会话名称。
  - \<*FileName*>指定将向其写入事件的日志文件。
  - \<*TraceFlags*>应为[跟踪标志表](#values-for-trace-flags)中列出的一个或多个值。

## <a name="how-to-end-a-tracing-session-and-turn-off-event-tracing"></a>如何结束跟踪会话并关闭事件跟踪

**停止跟踪**

- 在命令提示符处运行以下命令：

   ```cmd
   tracelog.exe -stop <SessionName>
   ```

   在此命令中，与在 \<*SessionName*> **tracelog.exe 开始**命令中使用的名称相同。

**禁用 ETW**

- 在注册表编辑器中，删除**HKEY \_ LOCAL \_ MACHINE \\ System \\ CurrentControlSet \\ Services \\ ldap \\ 跟踪 \\ * ProcessName*** 子项。

## <a name="values-for-trace-flags"></a>跟踪标志的值

若要使用标志，请用**tracelog.exe-start**命令的参数中的 <*跟踪标志*> 占位符替换标志值。

> [!NOTE]  
> 您可以使用相应的标志值的总和指定多个标志。 例如，若要指定**调试 \_ 搜索**（0X00000001）和**调试 \_ 缓存**（0x00000010）标志，则适当的 \<*TraceFlags*> 值为**0x00000011**。

|标记名称 |标志值 |标志说明 |
| --- | --- | --- |
|**DEBUG_SEARCH** |0x00000001 |记录搜索请求和传递到这些请求的参数。 不会在此处记录响应。 仅记录搜索请求。 （使用**DEBUG_SPEWSEARCH**将响应记录到搜索请求。） |
|**DEBUG_WRITE** |0x00000002 |记录写入请求和传递到这些请求的参数。 写入请求包括 "添加"、"删除"、"修改" 和 "扩展" 操作。 |
|**DEBUG_REFCNT** |0x00000004 |日志引用用于连接和请求的计数数据和操作。 |
|**DEBUG_HEAP** |0x00000008 |记录所有内存分配和内存释放。 |
|**DEBUG_CACHE** |0x00000010 |记录缓存活动。 此活动包括添加、删除、命中、未命中等。 |
|**DEBUG_SSL** |0x00000020 |记录 SSL 信息和错误。 |
|**DEBUG_SPEWSEARCH** |0x00000040 |将所有服务器响应记录到搜索请求。 这些响应包括请求的属性，以及接收的所有数据。 |
|**DEBUG_SERVERDOWN** |0x00000080 |记录服务器停机和连接错误。 |
|**DEBUG_CONNECT** |0x00000100 |记录与建立连接相关的数据。<br />使用**DEBUG_CONNECTION**可记录与连接相关的其他数据。 |
|**DEBUG_RECONNECT** |0x00000200 |记录自动重新连接活动。 此活动包括重新连接尝试、失败和相关错误。 |
|**DEBUG_RECEIVEDATA** |0x00000400 |与从服务器接收消息相关的日志活动。 此活动包括诸如 "等待服务器响应" 之类的事件和从服务器接收的响应。 |
|**DEBUG_BYTES_SENT** |0x00000800 |将 LDAP 客户端发送的所有数据记录到服务器。 此函数实质上是数据包日志记录，但它总是记录未加密的数据。 （如果数据包通过 SSL 发送，此函数将记录未加密的数据包。）此日志记录可能更详细。 此标志最适用于其自己的或与**DEBUG_BYTES_RECEIVED**结合使用。 |
|**DEBUG_EOM** |0x00001000 |记录与到达邮件列表末尾相关的事件。 这些事件包括 "清除消息列表" 等信息。 |
|**DEBUG_BER** |0x00002000 |记录与基本编码规则（BER）相关的操作和错误。 这些操作和错误包括编码问题、缓冲区大小问题，等等。 |
|**DEBUG_OUTMEMORY** |0x00004000 |记录分配内存失败。 同时记录任何无法计算所需内存的问题（例如，在计算所需的缓冲区大小时发生的溢出）。 |
|**DEBUG_CONTROLS** |0x00008000 |记录与控件相关的数据。 此数据包括插入的控件、影响控件的问题、连接上的强制控件等。 |
|**DEBUG_BYTES_RECEIVED** |0x00010000 |记录 LDAP 客户端收到的所有数据。 此行为实质上是数据包日志记录，但它总是记录未加密的数据。 （如果数据包通过 SSL 发送，此选项将记录未加密的数据包。）这种类型的日志记录可能是详细的。 此标志最适用于其自己的或与**DEBUG_BYTES_SENT**结合使用。 |
|**DEBUG_CLDAP** |0x00020000 |记录特定于 UDP 和无连接 LDAP 的事件。 |
|**DEBUG_FILTER** |0x00040000 |记录构造搜索筛选器时遇到的事件和错误。<br/>**注意**此选项仅在筛选器构造期间记录客户端事件。 它不记录来自服务器的有关筛选器的任何响应。 |
|**DEBUG_BIND** |0x00080000 |记录绑定事件和错误。 此数据包括协商信息、绑定成功、绑定失败等。 |
|**DEBUG_NETWORK_ERRORS** |0x00100000 |记录一般网络错误。 此数据包括发送和接收错误。<br/>**注意**如果连接丢失或无法访问服务器， **DEBUG_SERVERDOWN**是首选标记。 |
|**DEBUG_VERBOSE** |0x00200000 |记录常规消息。 对于往往会生成大量输出的消息，请使用此选项。 例如，它记录消息，如 "已到达消息结束"、"服务器尚未响应" 等。 对于一般消息，此选项也很有用。 |
|**DEBUG_PARSE** |0x00400000 |记录常规消息事件和错误以及数据包分析和编码事件和错误。 |
|**DEBUG_REFERRALS** |0x00800000 |记录有关引用和追踪引用的数据。 |
|**DEBUG_REQUEST** |0x01000000 |记录请求的跟踪。 |
|**DEBUG_CONNECTION** |0x02000000 |记录常规连接数据和错误。 |
|**DEBUG_INIT_TERM** |0x04000000 |日志模块初始化和清理（DLL Main，等等）。 |
|**DEBUG_API_ERRORS** |0x08000000 |支持记录不正确地使用 API。 例如，如果在同一连接上调用绑定操作两次，则此选项会记录数据。 |
|**DEBUG_ERRORS** |0x10000000 |记录常规错误。 其中的大多数错误可以归类为模块初始化错误、SSL 错误或溢出或下溢错误。 |
|**DEBUG_PERFORMANCE** |0x20000000 |接收 LDAP 请求的服务器响应后，记录有关进程的全局 LDAP 活动统计信息的数据。 |

## <a name="example"></a>示例

假设有一个应用程序 App1.exe，该应用程序设置用户帐户的密码。 假设 App1.exe 产生意外错误。 若要使用 ETW 来帮助诊断此问题，请执行以下步骤：

1. 在注册表编辑器中，创建以下注册表项：

   **HKEY \_ 本地 \_ 计算机 \\ 系统 \\ CurrentControlSet \\ Services \\ ldap \\ 跟踪 \\App1.exe**

1. 若要启动跟踪会话，请打开命令提示符窗口，并运行以下命令：

   ```cmd
   tracelog.exe -start ldaptrace -guid \#099614a5-5dd7-4788-8bc9-e29f43db28fc -f .\ldap.etl -flag 0x80000
   ```

   此命令启动后，**调试 \_ 绑定**可确保 ETW 将跟踪消息写入。 \\ldap .etl。

1. 开始 App1.exe，并重现意外错误。

1. 若要停止跟踪会话，请在命令提示符下运行以下命令：

   ```cmd
    tracelog.exe -stop ldaptrace
   ```

1. 若要防止其他用户跟踪应用程序，请删除**HKEY \_ LOCAL \_ MACHINE** \\ **System** \\ **CurrentControlSet** \\ **Services** \\ **ldap** \\ **跟踪** \\ **App1.exe**注册表项。

1. 若要查看跟踪日志中的信息，请在命令提示符下运行以下命令：

   ```cmd
    tracerpt.exe .\ldap.etl -o -report
    ```

   > [!NOTE]  
   > 在此命令中， **tracerpt.exe**是[跟踪使用者](https://go.microsoft.com/fwlink/p/?linkid=83876)工具。
