---
title: 高级疑难解答服务器消息块（SMB）
description: 介绍高级服务器消息块（SMB）故障排除方法。
author: Deland-Han
manager: dcscontentpm
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 21b090e8e70f287e9609d28588403e3aa0988ce4
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966299"
---
# <a name="advanced-troubleshooting-server-message-block-smb"></a>高级疑难解答服务器消息块（SMB）

服务器消息块（SMB）是一种用于文件系统操作的网络传输协议，可让客户端访问服务器上的资源。 SMB 协议的主要用途是通过 TCP/IP 启用两个系统之间的远程文件系统访问。

SMB 故障排除可能非常复杂。 本文并不是一个详尽的故障排除指南，它是一个简短的入门知识，可了解有关如何有效排查 SMB 问题的基础知识。

## <a name="tools-and-data-collection"></a>工具和数据收集

质量 SMB 故障排除的一个重要方面是传达正确的术语。 因此，本文介绍了基本的 SMB 术语，以确保数据收集和分析的准确性。

> [!Note]
> *SMB 服务器（SRV）* 是指承载文件系统（也称为文件服务器）的系统。 *SMB 客户端（CLI）* 是指尝试访问文件系统的系统，而不考虑操作系统版本。

例如，如果使用 Windows Server 2016 访问 Windows 10 上托管的 SMB 共享，则 Windows Server 2016 是 smb 客户端和 Windows 10 SMB 服务器。

### <a name="collect-data"></a>收集数据

在解决 SMB 问题之前，建议先在客户端和服务器端收集网络跟踪。 以下准则将适用：

- 在 Windows 系统上，可以使用 netshell （netsh）、网络监视器、Message 分析器或 Wireshark 来收集网络跟踪。

- 第三方设备通常具有内置的数据包捕获工具，例如 tcpdump （Linux/FreeBSD/Unix）或 pktt （NetApp）。 例如，如果 SMB 客户端或 SMB 服务器是 Unix 主机，则可以通过运行以下命令来收集数据：
  
  ```cmd
  # tcpdump -s0 -n -i any -w /tmp/$(hostname)-smbtrace.pcap
  ```
  
  使用键盘上的**Ctrl + C**停止收集数据。

若要发现问题的根源，可以检查两侧跟踪： CLI、SRV 或两者之间的某个位置。

#### <a name="using-netshell-to-collect-data"></a>使用 netshell 收集数据

本部分提供使用 netshell 收集网络跟踪的步骤。

> [!NOTE]  
> Netsh 跟踪创建 ETL 文件。 ETL 文件只能在 Message Analyzer （MA）中打开，并网络监视器3.4 （将分析器设置为网络监视器的分析程序 \> 窗口）。

1. 在 SMB 服务器和 SMB 客户端上，在驱动器**C**上创建一个**临时**文件夹。然后，运行以下命令：

   ```cmd
   netsh trace start capture=yes report=yes scenario=NetConnection level=5 maxsize=1024 tracefile=c:\\Temp\\%computername%\_nettrace.etl**
   ```
   
   如果使用的是 PowerShell，请运行以下 cmdlet：
   
   ```PowerShell
   New-NetEventSession -Name trace -LocalFilePath "C:\Temp\$env:computername`_netCap.etl" -MaxFileSize 1024

   Add-NetEventPacketCaptureProvider -SessionName trace -TruncationLength 1500

   Start-NetEventSession trace
   ```
   
2. 重现问题。

3. 通过运行以下命令停止跟踪：

   ```cmd
   netsh trace stop
   ```
   
   如果使用的是 PowerShell，请运行以下 cmdlet：

   ```PowerShell
   Stop-NetEventSession trace  
   Remove-NetEventSession trace
   ```

> [!NOTE] 
> 只应跟踪传输的数据量的最小值。 对于性能问题，如果出现这种情况，应始终采用良好的和错误的跟踪。

### <a name="analyze-the-traffic"></a>分析流量

SMB 是使用 TCP/IP 作为网络传输协议的应用程序级协议。 因此，SMB 问题也可能是由 TCP/IP 问题导致的。

检查 TCP/IP 是否遇到以下任何问题：

1. TCP 三向握手未完成。 这通常表示存在防火墙块，或服务器服务未运行。

2. 发生重新传输。 这可能会导致文件传输缓慢，因为出现复合 TCP 拥塞限制。

3. 五次重新传输后，TCP 重置可能表示系统之间的连接丢失，或者其中一个 SMB 服务崩溃或停止响应。

4. 将减少 TCP 接收窗口。 这可能是因为存储速度缓慢或某些其他问题导致无法从辅助函数驱动程序（AFD） Winsock 缓冲区检索数据。

如果没有明显的 TCP/IP 问题，请查看 SMB 错误。 为此，请执行以下步骤：

1. 请始终根据 SMB2 协议规范检查 SMB 错误。 许多 SMB 错误都是良性的（不有害）。 请参阅以下信息，确定在结论错误与以下任何问题相关后，SMB 返回错误的原因：

   - [SMB2 消息语法](/openspecs/windows_protocols/ms-smb2/6eaf6e75-9c23-4eda-be99-c9223c60b181)主题详细说明了每个 SMB 命令及其选项。
    
   - [SMB2 客户端处理](/openspecs/windows_protocols/ms-smb2/df0625a5-6516-4fbe-bf97-01bef451cab2)主题详细说明了 SMB 客户端如何创建请求并响应服务器消息。

   - [SMB2 服务器处理](/openspecs/windows_protocols/ms-smb2/e1d08834-42e0-41ca-a833-fc26f5132a6f)主题详细说明了 SMB 服务器如何创建请求并响应客户端请求。

2. 检查在 FSCTL \_ 验证 \_ 协商 \_ 信息（验证协商）命令后是否立即发送 TCP reset 命令。 如果是这样，请参阅以下信息：

   - 当客户端或服务器上的验证协商过程失败时，必须终止 SMB 会话（TCP 重置）。

   - 此过程可能会失败，因为 WAN 优化器正在修改 SMB 协商数据包。

   - 如果连接过早结束，则确定客户端和服务器之间的最后一个 exchange 通信。

#### <a name="analyze-the-protocol"></a>分析协议

查看网络跟踪中的实际 SMB 协议详细信息，以了解所使用的确切命令和选项。

> [!NOTE]
> 只有 Message Analyzer 可以分析 SMBv3 和更高版本的命令。

- 请记住，SMB 只执行所建议的操作。

- 可以通过检查 SMB 命令了解应用程序尝试执行的操作。

将命令和操作与协议规范进行比较以确保一切正常运行。 如果不是，则收集更接近或较低级别的数据，以查找有关根本原因的详细信息。 为此，请执行以下步骤：

1. 收集标准数据包捕获。

2. 运行**netsh**命令以跟踪和收集有关网络堆栈中是否存在问题的详细信息，或者删除 Windows 筛选平台（WFP）应用程序（如防火墙或防病毒程序）。

3. 如果所有其他选项均失败，请收集 t-sql （如果怀疑问题发生在 SMB 本身内）或其他数据是否足以识别根本原因。

例如：

- 文件传输速度慢于单个文件服务器。

- 双侧跟踪显示，SRV 响应读取请求的速度缓慢。

- 删除防病毒程序可以解决文件传输缓慢的情况。

- 请与防病毒程序 manufactory 联系以解决此问题。

> [!NOTE]
> 或者，你**还**可以在故障排除过程中临时卸载防病毒程序。

#### <a name="event-logs"></a>事件日志

SMB 客户端和 SMB 服务器都有详细的事件日志结构，如以下屏幕截图所示。 收集事件日志，以帮助找出问题的根本原因。

![事件日志](media/troubleshooting-smb-1.png)

## <a name="smb-related-system-files"></a>与 SMB 相关的系统文件

此部分列出了与 SMB 相关的系统文件。 若要保持系统文件的更新，请确保已安装最新的[更新汇总](https://support.microsoft.com/help/4498140/windows-10-update-history)。

**% Windir% \\ system32 \\ 驱动程序**以下列出的 SMB 客户端二进制文件：

- RDBSS.sys

- MRXSMB.sys

- MRXSMB10.sys

- MRXSMB20.sys

- MUP.sys

- SMBdirect.sys

**% Windir% \\ system32 \\ 驱动程序**以下列出的 SMB 服务器二进制文件：

- SRVNET.sys

- SRV.sys

- SRV2.sys

- SMBdirect.sys

- 低于 **% windir% \\ system32**

- srvsvc.dll

![SMB 组件](media/troubleshooting-smb-2.png)

### <a name="update-suggestions"></a>更新建议

建议你在解决 SMB 问题之前更新以下组件：

- 文件服务器需要文件存储。 如果存储包含 iSCSI 组件，请更新这些组件。

- 更新网络组件。

- 为了获得更好的性能和稳定性，请更新 Windows Core。

## <a name="reference"></a>参考

[Microsoft SMB 协议数据包交换方案](/windows/win32/fileio/microsoft-smb-protocol-packet-exchange-scenario)
