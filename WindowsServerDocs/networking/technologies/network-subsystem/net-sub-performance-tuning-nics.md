---
title: 性能优化网络适配器
description: 本主题是 Windows Server 2016 的网络子系统性能优化指南的一部分。
audience: Admin - CI ID 111485 - CSSTroubleshoot
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 0b9b0f80-415c-4f5e-8377-c09b51d9c5dd
manager: dcscontentpm
ms.author: v-tea
author: Teresa-Motiv
ms.date: 12/23/2019
ms.openlocfilehash: eb402c9cd7bb4f9ae472859fcd45fcc050d1df85
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182133"
---
# <a name="performance-tuning-network-adapters"></a>性能优化网络适配器

> 适用于：Windows Server 2019、Windows Server 2016、Windows Server（半年频道）

使用本主题中的信息来优化运行 Windows Server 2016 及更高版本的计算机的性能网络适配器。 如果网络适配器提供了优化选项，则可以使用这些选项优化网络吞吐量和资源使用情况。

网络适配器的正确调整设置取决于以下变量：

- 网络适配器及其功能集
- 服务器执行的工作负荷类型
- 服务器硬件和软件资源
- 服务器的性能目标

以下各部分介绍了某些性能优化选项。

##  <a name="enabling-offload-features"></a><a name="bkmk_offload"></a>启用卸载功能

启用网络适配器卸载功能通常会带来好处。 但是，网络适配器可能不够强大，无法处理高吞吐量的卸载功能。

> [!IMPORTANT]
> 不要使用卸载功能**IPsec 任务卸载**或**TCP 烟囱卸载**。 这些技术在 Windows Server 2016 中已弃用，可能会对服务器和网络性能产生负面影响。 此外，Microsoft 将来可能不支持这些技术。

例如，假设有一个硬件资源有限的网络适配器。
在这种情况下，启用分段卸载功能可能会降低适配器的最大可持续吞吐量。 但是，如果可接受降低的吞吐量，则应该继续启用分段卸载功能。

> [!NOTE]
> 某些网络适配器要求独立于发送和接收路径启用卸载功能。

##  <a name="enabling-receive-side-scaling-rss-for-web-servers"></a><a name="bkmk_rss_web"></a>启用 web 服务器的接收方缩放（RSS）

当服务器上的网络适配器少于逻辑处理器时，RSS 可以提高 Web 的可伸缩性和性能。 当所有 web 流量都通过支持 RSS 的网络适配器时，服务器可以跨不同的 Cpu 同时处理来自不同连接的传入 web 请求。

> [!IMPORTANT]
> 避免在同一服务器上同时使用非 RSS 网络适配器和支持 RSS 的网络适配器。 由于 RSS 和超文本传输协议（HTTP）中存在负载分配逻辑，如果不支持 RSS 的网络适配器接受具有一个或多个支持 RSS 的网络适配器的服务器上的 web 流量，则性能可能会受到严重降级。 在此情况下，你应该使用支持 RSS 的网络适配器或在网络适配器属性“高级属性”**** 选项卡上禁用 RSS。
>
> 若要确定网络适配器是否支持 RSS，你可以在网络适配器属性“高级属性”**** 选项卡上查看 RSS 信息。

### <a name="rss-profiles-and-rss-queues"></a>RSS 配置文件和 RSS 队列

默认 RSS 预定义配置文件为**NUMAStatic**，不同于以前版本的 Windows 使用的默认配置文件。 开始使用 RSS 配置文件之前，请查看可用的配置文件，了解它们有哪些好处，以及如何将它们应用于网络环境和硬件。

例如，如果打开 "任务管理器" 并检查服务器上的逻辑处理器，而在接收流量看来没有充分利用，则可以尝试将 RSS 队列的数量从默认值从2增加到网络适配器支持的最大值。 你的网络适配器可能具有将 RSS 队列数目作为驱动程序的一部分进行更改的选项。

##  <a name="increasing-network-adapter-resources"></a><a name="bkmk_resources"></a>增加网络适配器资源

对于允许手动配置资源（如接收和发送缓冲区）的网络适配器，应增加分配的资源。

某些网络适配器将它们的接收缓冲区设置得较低以节省从主机分配的内存。 较低的值会导致数据包丢弃和性能降低。 因此，对于接收密集型的方案，我们建议你将接收缓冲区值增加到最大值。

> [!NOTE]
> 如果网络适配器未公开手动资源配置，则它会动态配置资源，或资源设置为无法更改的固定值。

### <a name="enabling-interrupt-moderation"></a>启用中断裁决

为控制中断裁决，某些网络适配器公开不同的中断裁决级别、不同的缓冲区合并参数（有时单独用于发送和接收缓冲区）或两者。

对于 CPU 绑定的工作负荷，应考虑中断裁决。 使用中断裁决时，请考虑在主机 CPU 节省和延迟之间进行权衡，同时降低主机 CPU 的节省，因为有更多中断，延迟更少。 如果网络适配器不执行中断裁决，但它确实公开了缓冲区合并，则可以通过增加合并的缓冲区数来允许每个发送或接收更多的缓冲区，从而提高性能。

##  <a name="performance-tuning-for-low-latency-packet-processing"></a><a name="bkmk_low"></a>低延迟数据包处理的性能优化

许多网络适配器提供选项来优化由操作系统触发的延迟。 延迟是处理网络驱动程序传入数据包和网络驱动程序发回数据包之间经过的时间。 此时间通常以微秒为单位。 为了进行比较，远距离的数据包传输的传输时间通常以毫秒为单位（增大一个数量级）。 此优化不会减少数据包在传输过程中所花的时间。

以下是某些针对微秒敏感网络的性能优化建议。

- 请将计算机的 BIOS 设置为**高性能**，并禁用 CPU 电源状态。 但是，请注意这与系统和 BIOS 相关，如果操作系统控制电源管理，则某些系统将提供更高的性能。 可以通过**设置**或使用**powercfg**命令来检查和调整电源管理设置。 有关详细信息，请参阅[Powercfg 命令行选项](https://docs.microsoft.com/windows-hardware/design/device-experiences/powercfg-command-line-options)。

- 请将操作系统电源管理配置文件设置为**高性能系统**。
   > [!NOTE]
   > 如果系统 BIOS 设置为禁用电源管理的操作系统控制，则此设置不能正常工作。

- 启用静态卸载。 例如，启用 UDP 校验和、TCP 校验和，并发送大卸载（LSO）设置。

- 如果流量经过多流式处理（例如，在接收大容量多播流量时），请启用 RSS。

- 针对需要可能的最低延迟的网卡驱动程序，禁用**中断裁决**设置。 请记住，此配置可以使用更多的 CPU 时间，它表示一个折衷。

- 在内核处理器上处理网络适配器中断和 DPC，该处理器与处理数据包的程序（用户线程）所用的内核共享 CPU 缓存。 可以使用 CPU 相关性优化将进程定向到特定的逻辑处理器并结合 RSS 配置来实现此目的。 将相同的内核用于中断、DPC 和用户模式线程会随着负载的增加而表现出最差的性能，因为 ISR、DPC 和线程会争夺对内核的使用。

##  <a name="system-management-interrupts"></a><a name="bkmk_smi"></a>系统管理中断

许多硬件系统使用系统管理中断（SMI-S）来实现多种维护功能，如报告错误纠正代码（ECC）内存错误、维护旧的 USB 兼容性、控制风扇以及管理 BIOS 控制的电源设置。

SMI 是系统上的最高优先级中断，并将 CPU 置于管理模式下。 此模式抢先于所有其他活动，而 SMI 运行中断服务例程（通常包含在 BIOS 中）。

遗憾的是，这种行为可能导致延迟达100微秒或更长时间。

如果你需要达到最低延迟，应要求你的硬件提供商提供可将 SMI 降低到可能的最低程度的 BIOS 版本。 这些 BIOS 版本经常称为 "低延迟 BIOS" 或 "SMI-S 免费 BIOS"。 在某些情况下，硬件平台不可能完全消除 SMI 活动，因为 SMI 用于控制基本功能（例如，冷却风扇）。

> [!NOTE]
> 操作系统无法控制 SMIs，因为逻辑处理器在特殊维护模式下运行，这会阻止操作系统介入。

##  <a name="performance-tuning-tcp"></a><a name="bkmk_tcp"></a>性能优化 TCP

 你可以使用以下项来优化 TCP 性能。

###  <a name="tcp-receive-window-autotuning"></a><a name="bkmk_tcp_params"></a>TCP 接收窗口自动优化

在 Windows Vista、Windows Server 2008 和更高版本的 Windows 中，Windows 网络堆栈使用名为*tcp 接收窗口自动优化级别*的功能来协商 tcp 接收窗口大小。 此功能可以在 TCP 握手期间为每个 TCP 通信协商定义的接收窗口大小。

在 Windows 的早期版本中，Windows 网络堆栈使用固定大小的接收窗口（65535字节），该窗口限制了连接的总体可能吞吐量。 TCP 连接的总可实现吞吐量可能会限制网络使用方案。 TCP 接收窗口自动优化可使这些方案完全使用网络。

对于具有特定大小的 TCP 接收窗口，可以使用以下公式来计算单一连接的总吞吐量。

> 可*实现的总吞吐量（以字节为单位）*  = *TCP 接收窗口大小（字节）* \*（1/*连接延迟，以秒为单位*）

例如，对于滞后时间为10毫秒的连接，总可实现吞吐量只有 51 Mbps。 对于大型企业网络基础结构，此值是合理的。 但是，通过使用自动优化调整接收窗口，连接可以实现 1 Gbps 连接的全部线路速率。

某些应用程序定义 TCP 接收窗口的大小。 如果应用程序未定义接收窗口大小，则链接速度将确定大小，如下所示：

- 小于1兆位/秒（Mbps）：8千字节（KB）
- 1 mbps 到 100 Mbps： 17 KB
- 100 Mbps 到10千兆位/秒（Gbps）： 64 KB
- 10 Gbps 或更快： 128 KB

例如，在安装了 1 Gbps 网络适配器的计算机上，窗口大小应为 64 KB。

此功能还充分利用了其他功能以提高网络性能。 这些功能包括[RFC 1323](https://tools.ietf.org/html/rfc1323)中定义的其他 TCP 选项。 通过使用这些功能，基于 Windows 的计算机可以协商较小但按定义的值进行缩放的 TCP 接收窗口大小，具体取决于配置。 这种情况下，更易于处理网络设备的大小。

> [!NOTE]
> 你可能会遇到这样的问题：网络设备不符合[RFC 1323](https://tools.ietf.org/html/rfc1323)中定义的**TCP 窗口缩放选项**，因此不支持缩放系数。 在这种情况下，请参阅此[KB 934430，当你尝试使用防火墙设备后面的 Windows Vista 时网络连接失败，](https://support.microsoft.com/help/934430/network-connectivity-fails-when-you-try-to-use-windows-vista-behind-a)或与网络设备供应商的支持团队联系。

#### <a name="review-and-configure-tcp-receive-window-autotuning-level"></a>查看和配置 TCP 接收窗口自动调谐级别

可以使用 netsh 命令或 Windows PowerShell cmdlet 来查看或修改 TCP 接收窗口自动优化级别。

> [!NOTE]
> 与 windows 10 或 Windows Server 2019 之前的版本不同，你不能再使用注册表来配置 TCP 接收窗口大小。 有关不推荐使用的设置的详细信息，请参阅不[推荐使用的 TCP 参数](#deprecated-tcp-parameters)。

> [!NOTE]
> 有关可用自动优化级别的详细信息，请参阅自动[调谐级别](#autotuning-levels)。

**使用 netsh 查看或修改自动调谐级别**

若要查看当前设置，请打开命令提示符窗口，并运行以下命令：

```cmd
netsh interface tcp show global
```

此命令的输出应如下所示：

```
Querying active state...

TCP Global Parameters
-----
Receive-Side Scaling State : enabled
Chimney Offload State : disabled
Receive Window Auto-Tuning Level : normal
Add-On Congestion Control Provider : default
ECN Capability : disabled
RFC 1323 Timestamps : disabled
Initial RTO : 3000
Receive Segment Coalescing State : enabled
Non Sack Rtt Resiliency : disabled
Max SYN Retransmissions : 2
Fast Open : enabled
Fast Open Fallback : enabled
Pacing Profile : off
```

若要修改此设置，请在命令提示符下运行以下命令：

```cmd
netsh interface tcp set global autotuninglevel=<Value>
```

> [!NOTE]
> 在前面的命令中， \<*Value*> 表示自动优化级别的新值。

有关此命令的详细信息，请参阅[Interface 传输控制协议的 Netsh 命令](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731258(v=ws.10))。

**使用 Powershell 查看或修改自动调谐级别**

若要查看当前设置，请打开 PowerShell 窗口并运行以下 cmdlet。

```PowerShell
Get-NetTCPSetting | Select SettingName,AutoTuningLevelLocal
```

此 cmdlet 的输出应如下所示。

```
SettingName           AutoTuningLevelLocal
-----------          --------------------
Automatic
InternetCustom       Normal
DatacenterCustom     Normal
Compat               Normal
Datacenter           Normal
Internet             Normal
```

若要修改此设置，请在 PowerShell 命令提示符下运行以下 cmdlet。

```PowerShell
Set-NetTCPSetting -AutoTuningLevelLocal <Value>
```

> [!NOTE]
> 在前面的命令中， \<*Value*> 表示自动优化级别的新值。

有关这些 cmdlet 的详细信息，请参阅以下文章：

- [NetTCPSetting](https://docs.microsoft.com/powershell/module/nettcpip/get-nettcpsetting?view=win10-ps)
- [NetTCPSetting](https://docs.microsoft.com/powershell/module/nettcpip/set-nettcpsetting?view=win10-ps)

#### <a name="autotuning-levels"></a>自动优化级别

可以将接收窗口自动调谐设置为任意一种级别。 默认级别为 "**正常**"。 下表介绍了这些级别。

|Level |十六进制值 |注释 |
| --- | --- | --- |
|标准（默认值） |0x8 （比例因子为8） |设置 TCP 接收窗口以适应几乎所有方案。 |
|已禁用 |没有可用的缩放比例 |将 TCP 接收窗口设置为其默认值。 |
|受限制 |0x4 （缩放系数为4） |设置 TCP 接收窗口，使其超出其默认值，但在某些情况下限制此类增长。 |
|高度限制 |0x2 （缩放比例为2） |设置 TCP 接收窗口，使其超出其默认值，但要非常谨慎。 |
|实验 |0xE （缩放比例为14） |设置 TCP 接收窗口以适应极端方案。 |

如果使用应用程序来捕获网络数据包，则应用程序应为不同的窗口自动优化级别设置报告类似于以下内容的数据。

- 自动调谐级别：**普通（默认状态）**

   ```
   Frame: Number = 492, Captured Frame Length = 66, MediaType = ETHERNET
   + Ethernet: Etype = Internet IP (IPv4),DestinationAddress:[D8-FE-E3-65-F3-FD],SourceAddress:[C8-5B-76-7D-FA-7F]
   + Ipv4: Src = 192.169.0.5, Dest = 192.169.0.4, Next Protocol = TCP, Packet ID = 2667, Total IP Length = 52
   - Tcp: [Bad CheckSum]Flags=......S., SrcPort=60975, DstPort=Microsoft-DS(445), PayloadLen=0, Seq=4075590425, Ack=0, Win=64240 ( Negotiating scale factor 0x8 ) = 64240
   SrcPort: 60975
   DstPort: Microsoft-DS(445)
   SequenceNumber: 4075590425 (0xF2EC9319)
   AcknowledgementNumber: 0 (0x0)
   + DataOffset: 128 (0x80)
   + Flags: ......S. ---------------------------------------------------------> SYN Flag set
   Window: 64240 ( Negotiating scale factor 0x8 ) = 64240 ---------> TCP Receive Window set as 64K as per NIC Link bitrate. Note it shows the 0x8 Scale Factor.
   Checksum: 0x8182, Bad
   UrgentPointer: 0 (0x0)
   - TCPOptions:
   + MaxSegmentSize: 1
   + NoOption:
   + WindowsScaleFactor: ShiftCount: 8 -----------------------------> Scale factor, defined by AutoTuningLevel
   + NoOption:
   + NoOption:
   + SACKPermitted:
   ```

- 自动调谐级别：**已禁用**

   ```
   Frame: Number = 353, Captured Frame Length = 62, MediaType = ETHERNET
   + Ethernet: Etype = Internet IP (IPv4),DestinationAddress:[D8-FE-E3-65-F3-FD],SourceAddress:[C8-5B-76-7D-FA-7F]
   + Ipv4: Src = 192.169.0.5, Dest = 192.169.0.4, Next Protocol = TCP, Packet ID = 2576, Total IP Length = 48
   - Tcp: [Bad CheckSum]Flags=......S., SrcPort=60956, DstPort=Microsoft-DS(445), PayloadLen=0, Seq=2315885330, Ack=0, Win=64240 ( ) = 64240
   SrcPort: 60956
   DstPort: Microsoft-DS(445)
   SequenceNumber: 2315885330 (0x8A099B12)
   AcknowledgementNumber: 0 (0x0)
   + DataOffset: 112 (0x70)
   + Flags: ......S. ---------------------------------------------------------> SYN Flag set
   Window: 64240 ( ) = 64240 ----------------------------------------> TCP Receive Window set as 64K as per NIC Link bitrate. Note there is no Scale Factor defined. In this case, Scale factor is not being sent as a TCP Option, so it will not be used by Windows.
   Checksum: 0x817E, Bad
   UrgentPointer: 0 (0x0)
   - TCPOptions:
   + MaxSegmentSize: 1
   + NoOption:
   + NoOption:
   + SACKPermitted:
   ```

- 自动调谐级别：**受限**

   ```
   Frame: Number = 3, Captured Frame Length = 66, MediaType = ETHERNET
   + Ethernet: Etype = Internet IP (IPv4),DestinationAddress:[D8-FE-E3-65-F3-FD],SourceAddress:[C8-5B-76-7D-FA-7F]
   + Ipv4: Src = 192.169.0.5, Dest = 192.169.0.4, Next Protocol = TCP, Packet ID = 2319, Total IP Length = 52
   - Tcp: [Bad CheckSum]Flags=......S., SrcPort=60890, DstPort=Microsoft-DS(445), PayloadLen=0, Seq=1966088568, Ack=0, Win=64240 ( Negotiating scale factor 0x4 ) = 64240
   SrcPort: 60890
   DstPort: Microsoft-DS(445)
   SequenceNumber: 1966088568 (0x75302178)
   AcknowledgementNumber: 0 (0x0)
   + DataOffset: 128 (0x80)
   + Flags: ......S. ---------------------------------------------------------> SYN Flag set
   Window: 64240 ( Negotiating scale factor 0x4 ) = 64240 ---------> TCP Receive Window set as 64K as per NIC Link bitrate. Note it shows the 0x4 Scale Factor.
   Checksum: 0x8182, Bad
   UrgentPointer: 0 (0x0)
   - TCPOptions:
   + MaxSegmentSize: 1
   + NoOption:
   + WindowsScaleFactor: ShiftCount: 4 -------------------------------> Scale factor, defined by AutoTuningLevel.
   + NoOption:
   + NoOption:
   + SACKPermitted:
   ```

- 自动调谐级别：**高度限制**

   ```
   Frame: Number = 115, Captured Frame Length = 66, MediaType = ETHERNET
   + Ethernet: Etype = Internet IP (IPv4),DestinationAddress:[D8-FE-E3-65-F3-FD],SourceAddress:[C8-5B-76-7D-FA-7F]
   + Ipv4: Src = 192.169.0.5, Dest = 192.169.0.4, Next Protocol = TCP, Packet ID = 2388, Total IP Length = 52
   - Tcp: [Bad CheckSum]Flags=......S., SrcPort=60903, DstPort=Microsoft-DS(445), PayloadLen=0, Seq=1463725706, Ack=0, Win=64240 ( Negotiating scale factor 0x2 ) = 64240
   SrcPort: 60903
   DstPort: Microsoft-DS(445)
   SequenceNumber: 1463725706 (0x573EAE8A)
   AcknowledgementNumber: 0 (0x0)
   + DataOffset: 128 (0x80)
   + Flags: ......S. ---------------------------------------------------------> SYN Flag set
   Window: 64240 ( Negotiating scale factor 0x2 ) = 64240 ---------> TCP Receive Window set as 64K as per NIC Link bitrate. Note it shows the 0x2 Scale Factor.
   Checksum: 0x8182, Bad
   UrgentPointer: 0 (0x0)
   - TCPOptions:
   + MaxSegmentSize: 1
   + NoOption:
   + WindowsScaleFactor: ShiftCount: 2 ------------------------------> Scale factor, defined by AutoTuningLevel
   + NoOption:
   + NoOption:
   + SACKPermitted:
   ```

- 自动调谐级别：**实验**

   ```
   Frame: Number = 238, Captured Frame Length = 66, MediaType = ETHERNET
   + Ethernet: Etype = Internet IP (IPv4),DestinationAddress:[D8-FE-E3-65-F3-FD],SourceAddress:[C8-5B-76-7D-FA-7F]
   + Ipv4: Src = 192.169.0.5, Dest = 192.169.0.4, Next Protocol = TCP, Packet ID = 2490, Total IP Length = 52
   - Tcp: [Bad CheckSum]Flags=......S., SrcPort=60933, DstPort=Microsoft-DS(445), PayloadLen=0, Seq=2095111365, Ack=0, Win=64240 ( Negotiating scale factor 0xe ) = 64240
   SrcPort: 60933
   DstPort: Microsoft-DS(445)
   SequenceNumber: 2095111365 (0x7CE0DCC5)
   AcknowledgementNumber: 0 (0x0)
   + DataOffset: 128 (0x80)
   + Flags: ......S. ---------------------------------------------------------> SYN Flag set
   Window: 64240 ( Negotiating scale factor 0xe ) = 64240 ---------> TCP Receive Window set as 64K as per NIC Link bitrate. Note it shows the 0xe Scale Factor.
   Checksum: 0x8182, Bad
   UrgentPointer: 0 (0x0)
   - TCPOptions:
   + MaxSegmentSize: 1
   + NoOption:
   + WindowsScaleFactor: ShiftCount: 14 -----------------------------> Scale factor, defined by AutoTuningLevel
   + NoOption:
   + NoOption:
   + SACKPermitted:
   ```

#### <a name="deprecated-tcp-parameters"></a>不推荐使用的 TCP 参数

Windows Server 2003 中的以下注册表设置不再受支持，在更高版本中将被忽略。

- **TcpWindowSize**
- **NumTcbTablePartitions**
- **MaxHashTableSize**

所有这些设置都位于以下注册表子项中：

> **HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services\Tcpip\Parameters**

###  <a name="windows-filtering-platform"></a><a name="bkmk_wfp"></a>Windows 筛选平台

Windows Vista 和 Windows Server 2008 引进了 Windows 筛选平台（WFP）。 WFP 为非 Microsoft 独立软件供应商（Isv）提供 Api 来创建数据包处理筛选器。 其示例包括防火墙和防病毒软件。

> [!NOTE]
> 编写不当的 WFP 筛选器可能会显著降低服务器的网络性能。 有关详细信息，请参阅 Windows 开发人员中心中的将[包处理驱动程序和应用程序移植到 WFP](https://docs.microsoft.com/windows-hardware/drivers/network/porting-packet-processing-drivers-and-apps-to-wfp) 。

有关本指南中的所有主题的链接，请参阅[网络子系统性能优化](net-sub-performance-top.md)。
