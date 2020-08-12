---
title: Windows Server 2016 的时间准确性改进
description: Windows Server 2016 已改进用于纠正时间和调整本地时钟的算法，方便与 UTC 同步。
author: dcuomo
ms.author: dacuo
manager: dougkim
ms.date: 10/17/2018
ms.topic: article
ms.openlocfilehash: 7c0644d88e158050b83873f4398fe7ee87b120d5
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87997401"
---
# <a name="time-accuracy-improvements-for-windows-server-2016"></a>Windows Server 2016 的时间准确性改进

Windows Server 2016 已改进用于纠正时间和调整本地时钟的算法，方便与 UTC 同步。 NTP 根据客户端请求/响应和服务器请求/响应的时间戳使用 4 个值来计算时间偏移。 但网络充满干扰，且由于网络拥塞以及影响网络延迟的其他因素，可能导致 NTP 数据出现峰值。 Windows 2016 算法使用各种技术来平衡这类干扰，从而获得稳定且准确的时钟。 此外，用于获取精确时间的源还可引用改进的 API，从而为我们提供更高的分辨率。 通过这些改进功能，我们可以使跨域 UTC 的精确度达到 1 毫秒。

## <a name="hyper-v"></a>Hyper-V

Windows 2016 已改进 Hyper-V TimeSync 服务。 改进内容包括：提高了 VM 启动或 VM 还原的初始时间的准确性并纠正了提供给 Windows 时间 (W32time) 服务的示例的中断延迟。 这项改进允许按 RMS（均方根，表示方差）计与主机保持在 10µs 方差内，且即使计算机负载为 75%，也可以与主机保持在 50µs 方差内。 有关详细信息，请参阅 [Hyper-V 体系结构](https://msdn.microsoft.com/library/cc768520.aspx)。

> [!NOTE]
> 负载是使用均衡的配置文件通过 prime95 基准测试创建的。

此外，主机向来宾报告的层次级别更透明。 以前，无论主机准确性如何，它都会呈现固定层次 2。 随着 Windows Server 2016 中的更改，主机报告的层次要比主机层次大 1，从而得到更精确的虚拟来宾时间。 主机使用 w32time 根据其源时间按常规方式确定它的层次。 已加入域的 Windows 2016 来宾将得到最准确的时钟，而不是主机的默认时钟。 出于此原因，建议在 Windows 2012R2 及更低版本中手动禁用加入域的计算机的 Hyper-V 时间提供程序设置。

## <a name="monitoring"></a>监视

已添加性能监视器计数器。 可使用这些计数器对时间准确性进行基线处理、监视和故障排除。 这些计数器包括：

|计数器|说明|
|----- | ----- |
|计算时间偏移| 系统时钟与所选时间源之间的绝对时间偏移通过 W32Time 服务进行计算（以微秒为单位）。 新的有效样本可用时，将按样本指示的时间偏移更新计算时间。 这是本地时钟的实际时间偏移。 W32time 使用此偏移启动时钟更正，并使用其余时间偏移更新样本之间的计算时间，需要将后一个偏移应用于本地时钟。 可以使用此性能计数器以低轮询间隔（例如 256 秒或更短时间），通过寻找小于所需时钟精度限制的计数器值来跟踪时钟精度。|
|时钟频率调整| W32Time 以纳秒为单位对本地系统时钟进行的绝对时钟频率调整。 此计数器有助于可视化 W32time 所执行的操作。|
|NTP 往返延迟| NTP 客户端从服务器接收响应时的最新往返延迟，以微秒为单位。 这是在 NTP 客户端向 NTP 服务器传输请求和从服务器接收有效响应之间经历的时间。 此计数器有助于描述 NTP 客户端遇到的延迟。 较大或多变的往返可能会增加对 NTP 时间计算的干扰，而这些干扰又可能会通过 NTP 影响时间同步的准确性。|
|NTP 客户端源计数| NTP 客户端所使用的 NTP 时间源的有效数目。 这是时间服务器的有效且独立的 IP 地址计数，这些服务器可响应此客户端的请求。 此数字可能大于或小于配置的对等数，具体取决于对等数名称的 DNS 解析和当前的可达性。|
|NTP 服务器传入请求| NTP 服务器接收的请求数（请求数/秒）。|
|NTP 服务器传出响应| NTP 服务器应答的请求数（响应数/秒）。|

前 3 个计数器适用于对准确性问题进行故障排除的方案。 如需获取更多详细信息，请参阅“最佳做法”下方的“对时间准确性和 NTP 进行故障排除”部分。
后 3 个计数器适用于 NTP 服务器方案，有助于确定负载和对当前性能进行基线处理。

## <a name="configuration-updates-per-environment"></a>基于环境的配置更新

以下内容介绍了在 Windows 2016 和早期版本之间针对每个角色的默认配置中的变更。 Windows Server 2016 和 Windows 10 周年更新（版本 14393）的设置目前是唯一的，这也是显示为单独列的原因。

|Role|设置|Windows Server 2016|Windows 10|Windows Server 2012 R2<br>Windows Server 2008 R2<br>Windows 10|
|---|---|---|---|---|
|**独立服务器/Nano Server**||||
| |时间服务器 |time.windows.com|NA|time.windows.com|
| |轮询频率|64 - 1024 秒|NA|一周一次|
| |时钟更新频率 |一秒一次|NA|一小时一次|
|**独立客户端**||||
| |时间服务器 |NA|time.windows.com|time.windows.com|
| |轮询频率|NA|一天一次|一周一次|
| |时钟更新频率 |NA|一天一次|一周一次|
|**域控制器**||||
| |时间服务器 |PDC/GTIMESERV|NA|PDC/GTIMESERV|
| |轮询频率|64 - 1024 秒|NA|1024 - 32768 秒|
| |时钟更新频率 |一天一次|NA|一周一次|
|**域成员服务器**||||
| |时间服务器 |DC|NA|DC|
| |轮询频率|64 - 1024 秒|NA|1024 - 32768 秒|
| |时钟更新频率 |一秒一次|NA|每 5 分钟一次|
|**域成员客户端**||||
| |时间服务器 |NA|DC|DC|
| |轮询频率|NA|1204 - 32768 秒|1024 - 32768 秒|
| |时钟更新频率 |NA|每 5 分钟一次|每 5 分钟一次|
|**Hyper-V 来宾**||||
| |时间服务器 |根据主机和时间服务器的层次选择最佳选项|根据主机和时间服务器的层次选择最佳选项|默认为“主机”|
| |轮询频率|基于上述角色|基于上述角色|基于上述角色|
| |时钟更新频率 |基于上述角色|基于上述角色|基于上述角色|

>[!NOTE]
>对于 Hyper-V 中的 Linux，请参阅下方的“允许 Linux 使用 Hyper-V 主机时间”部分。

## <a name="impact-of-increased-polling-and-clock-update-frequency"></a>增大轮询和时钟更新频率的影响

为提供更准确的时间，增大了轮询频率和时钟更新的默认值，以便更频繁地进行一些小调整。 这将导致 UDP/NTP 流量增大，但这些数据包很小，因此对宽带连接的影响应很小或没有影响。 但优点在于，各种硬件和环境中的时间应会更精确。

对于电池供电的设备，增大轮询频率可能会导致问题。 电池设备在关闭时不会存储时间。 重启时，可能需要频繁地更正时钟。 增大轮询频率将导致时钟变得不稳定，并且还可能会增大能耗。 Microsoft 建议不要更改客户端的默认设置。

即使增加 AD 域中 NTP 客户端的更新导致影响翻倍，域控制器受到的影响也会降到最低。 与其他协议相比，NTP 消耗的资源要少得多，并且影响很小。 在因 Windows Server 2016 的设置增加而受影响之前，你更有可能会先受到其他域功能的限制。 Active Directory 使用的是安全的 NTP，相较于简单的 NTP，往往它的时间同步要差一些，但我们已经证实它可以扩展到距离 PDC 两个层次的客户端。

保守计划是，每个内核每秒应保留 100 个 NTP 请求。 例如，4 个 DC（每个 DC 具有 4 个内核）组成的域应能够每秒处理 1600 个 NTP 请求。 如果将 10,000 个客户端配置为每 64 秒同步一次时间，且随时间均匀地接收请求，你将在所有 DC 上看到 10,000/64 个请求/秒，即约 160 个请求/秒。 根据此示例，此数据远小于 1600 个 NTP 请求/秒。 这些都是保守计划建议，明显非常依赖网络、处理器速度和负载，因此始终要在环境中进行基线处理和测试。

另外，请务必注意，如果 DC 以相当大的 CPU 负载（大于 40%）运行，几乎可以肯定的是，将会增大对 NTP 响应的干扰并影响域中的时间准确性。 同样，你需要在环境中进行测试，以便了解实际结果。

## <a name="time-accuracy-measurements"></a>时间准确性度量

### <a name="methodology"></a>方法

为测量 Windows Server 2016 的时间准确性，我们使用了各种工具、方法和环境。 你可以使用这些方法测量和优化环境，并确定准确性结果是否符合要求。

域源时钟由两个具有 GPS 硬件的高精度 NTP 服务器组成。 我们还使用单独的参考测试计算机进行了测量，该计算机也安装了其他制造商提供的高精度 GPS 硬件。 对于某些测试，除域时钟源以外，你还需要一个准确可靠的时钟源用作参考。

我们使用四种不同方法测量了物理计算机和虚拟机的准确性。 多种方法都提供了独立方法来验证结果。

1. 根据具有独立 GPS 硬件的参考测试计算机，测量通过 w32tm 进行调整的本地时钟。

2. 使用 W32tm“stripchart”测量从 NTP 服务器到客户端的 NTP ping

3. 使用 W32tm“stripchart”测量从客户端到 NTP 服务器的 NTP ping

4. 使用时间戳计数器 (TSC) 测量从主机到来宾的 Hyper-V 结果。 此计数器可在两个分区和两个分区的系统时间之间进行共享。 我们计算了虚拟机中主机时间和客户端时间的差值。 接着，由于测量不会同时进行，因此使用 TSC 时钟从来宾插入主机时间。 此外，我们还在 API 中将 TSV 时钟系数用作输出延时和延迟。

W32tm 是内置工具，但对于 GitHub 上的 Microsoft 存储库，可将我们在测试期间使用的其他工具用作开放源代码工具进行测试和使用。 要详细了解如何使用工具来进行测量，请参阅 [Windows 时间校准工具 Wiki](https://github.com/Microsoft/Windows-Time-Calibration-Tools)

下方所示的测试结果是我们在某一测试环境中进行的部分测量。 它们说明了时间层次结构始端的准确性，以及时间层次结构末端的子域客户端。 这可与基于 2012 的拓扑中的相同计算机进行比较，以便对比。

### <a name="topology"></a>拓扑

为进行对比，我们测试了基于 Windows Server 2012R2 和基于 Windows Server 2016 的拓扑。 两种拓扑都包含两个物理 Hyper-V 主机，这些主机都引用了安装有 GPS 时钟硬件的 Windows Server 2016 计算机。 每个主机都可运行 3 个 Windows 来宾，这些来宾已加入域且按以下拓扑进行排列。 行表示时间层次结构和使用的协议/传输。

![Windows 时间拓扑图](../media/Windows-Time-Service/Windows-2016-Accurate-Time/topology1.png)

![Windows 时间拓扑图](../media/Windows-Time-Service/Windows-2016-Accurate-Time/topology2.png)

### <a name="graphical-results-overview"></a>图形结果概述

以下两个图形基于上述拓扑表示域中两个特定成员的时间准确性。 每个图均显示了 Windows Server 2012R2 和 Windows Server 2016 的叠加结果，以直观显示改进。 与主机相比，准确性是来宾计算机内部的度量。 图形数据表示已完成的全部测试的一部分，并显示最佳服务案例方案和最差服务案例情况。

![Windows 时间拓扑图](../media/Windows-Time-Service/Windows-2016-Accurate-Time/topology3.png)

### <a name="performance-of-the-root-domain-pdc"></a>根域 PDC 的性能

根 PDC 使用 VMIC 同步到 Hyper-V 主机，该主机是具有 GPS 硬件的 Windows Server 2016，GPS 硬件既准确又稳定。 这是实现 1 ms 准确性的必要条件，显示为绿色阴影区域。

![Windows 时间](../media/Windows-Time-Service/Windows-2016-Accurate-Time/chart1.png)

### <a name="performance-of-the-child-domain-client"></a>子域客户端的性能

子域客户端连接到与根 PDC 通信的子域 PDC。 It 时间也是 1 ms 的必要条件。

![Windows 时间](../media/Windows-Time-Service/Windows-2016-Accurate-Time/chart2.png)

### <a name="long-distance-test"></a>远距离测试

下表对比了 Windows Server 2016 中的 1 个虚拟网络跃点和 6 个物理网络跃点。 两个表彼此重叠，并以透明方式显示重叠的数据。 增加网络跃点意味着增大延迟和时间偏差。 图表放大，绿色区域表示的 1 ms 边界也会放大。 如你所见，多个跃点的时间仍在 1 ms 以内。 它发生了负向偏移，表明网络不对称。 当然，每个网络都不同，并且度量取决于多种环境因素。

![Windows 时间](../media/Windows-Time-Service/Windows-2016-Accurate-Time/chart3.png)

## <a name="best-practices-for-accurate-timekeeping"></a>准确报时的最佳做法

### <a name="solid-source-clock"></a>固态源时钟

计算机时间恰好与其所同步的源时钟一致。 为实现 1 ms 的准确性，你将需要 GPS 硬件或网络上作为主源时钟引用的时间设备。 使用默认的 time.windows.com 无法提供稳定的本地时间源。 此外，由于你远离源时钟，网络会影响准确性。 为获得最佳准确性，每个数据中心都需要有一个主源时钟。

### <a name="hardware-gps-options"></a>硬件 GPS 选项

有多种硬件解决方案可以提供准确时间。 通常，当前的解决方案都基于 GPS 天线。 还有使用专用线路的无线电和拨号调制解调器解决方案。 它们既可以作为设备连接到网络，也可以作为插头插入电脑（例如通过 PCIe 或 U 盘插入 Windows）。 不同的选项将提供不同级别的准确性，并且结果始终取决于环境。 影响准确性的变量包括 GPS 可用性、网络稳定性和负载以及电脑硬件。 这些都是选择源时钟时需要考虑的所有重要因素，也是实现稳定和准确时间的必要条件。

### <a name="domain-and-synchronizing-time"></a>域和同步时间

域成员使用域层次结构来确定用作同步时间的源计算机。 每个域成员都会找到另一台要与之同步的计算机，然后将其保存为时钟源。 每种类型的域成员都遵循不同的规则集，以便查找用于时间同步的时钟源。 林根中的 PDC 是所有域的默认时钟源。 下面列出了各种角色以及这些角色对源查找方式的高级说明：

- **具有 PDC 角色的域控制器** - 此计算机是域的权威时间源。 除非启用了 GTIMESERV 角色，否则它将具有域中最准确的时间，且一定会与父域中的 DC 同步。
- **任何其他域控制器** - 此计算机将充当域中客户端和成员服务器的时间源。 DC 可以与其域的 PDC 或其父域中的任何 DC 同步。
- **客户端/成员服务器** - 此计算机可以与其域的任何 DC 或 PDC，或者其父域中的 DC 或 PDC 同步。

根据可用的候选项，评分系统用于查找最佳时间源。 此系统会考虑时间源及其相对位置的可靠性。 时间服务启动时，就会考虑一次。 如果需要更好地控制时间同步的方式，你可以在特定位置添加适当的时间服务器或添加冗余。 如需了解详细信息，请参阅“使用 GTIMESERV 指定本地可靠时间服务”部分。

#### <a name="mixed-os-environments-win2012r2-and-win2008r2"></a>混合 OS 环境（Win2012R2 和 Win2008R2）

尽管需要纯 Windows Server 2016 域环境才能获得最佳准确性，但在混合环境中仍有好处。 由于上述改进，在 Windows 2012 域中部署 Windows Server 2016 Hyper-V 将使来宾受益，但前提是来宾也是 Windows Server 2016。 由于改进了算法，Windows Server 2016 PDC 将能够提供更准确的时间，成为更稳定的源。 由于可能无法替换 PDC，因此你可以转而添加具有 GTIMESERV 卷集的 Windows Server 2016 DC，以便提高域的准确性。 Windows Server 2016 DC 可为下游时间客户端提供更准确的时间，但最多与其源 NTP 时间一致。

同样，如上所述，Windows Server 2016 中已修改时钟轮询和刷新频率。 这些可以手动更改为下层 DC，也可以通过组策略进行应用。 尽管我们尚未测试这些配置，但在 Win2008R2 和 Win2012R2 中，这些配置应能运行良好，并提供一些好处。

Windows Server 2016 之前的版本在保持准确报时方面存在多个问题，导致系统时间在调整后会立即出现偏差。 因此，频繁从准确的 NTP 源获取时间样本并使用数据调整本地时钟可以在内部采用期间使系统时钟产生更小的偏差，从而在低层次的 OS 版本中实现更准确的报时。 如果 Windows Server 2012R2 NTP 客户端的准确性设置配置较高，当从准确的 Windows 2016 NTP 服务器同步其时间时，观测到的最佳准确性约为 5 ms。

在某些涉及来宾域控制器的方案中，Hyper-V TimeSync 示例可能会中断域时间同步。 对于在 Server 2016 Hyper-V 主机上运行的 Server 2016 来宾，这应不再是个问题。

若要禁止 Hyper-V TimeSync 服务向 w32time 提供示例，请设置以下来宾注册表项：`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\VMICTimeProvider
 "Enabled"=dword:00000000`

#### <a name="allowing-linux-to-use-hyper-v-host-time"></a>允许 Linux 使用 Hyper-V 主机时间

对于在 Hyper-V 中运行的 Linux 来宾，客户端通常配置为使用 NTP 守护程序针对 NTP 服务器进行时间同步。 如果 Linux 发行版支持 TimeSync 版本 4 协议，并且 Linux 来宾启用了 TimeSync 集成服务，则它将针对主机时间进行同步。 如果同时启用这两种方法，可能会导致报时不一致。

若仅针对主机时间进行同步，建议通过以下任一方法禁用 NTP 时间同步：

- 禁用 ntp.conf 文件中的任何 NTP 服务器

- 或禁用 NTP 守护程序

在此配置中，时间服务器参数为此主机。 其轮询频率为 5 秒，时钟更新频率也是 5 秒。

若仅针对 NTP 进行同步，建议在来宾中禁用 TimeSync 集成服务。

> [!NOTE]
> 注意：若要对 Linux 来宾中的准确时间提供支持，需要一项功能，该功能仅在最新版上游 Linux 内核中受支持，并且尚未在所有 Linux 发行版中广泛使用。 有关支持分发版的详细信息，请参阅 [Windows 上面向 Hyper-V 的受支持 Linux 和 FreeBSD 虚拟机](../../virtualization/hyper-v/supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows.md)。

#### <a name="specify-a-local-reliable-time-service-using-gtimeserv"></a>使用 GTIMESERV 指定本地可靠时间服务

你可以使用 GTIMESERV（即正确时间服务器）标志将一个或多个域控制器指定为准确源时钟。 例如，具有 GPS 硬件的特定域控制器可以标记为 GTIMESERV。 这可确保域引用基于 GPS 硬件的时钟。

> [!NOTE]
> 有关域标志的详细信息，请参阅 [MS-ADTS 协议文档](/openspecs/windows_protocols/ms-winerrata/fe563333-6e4f-4198-9bf5-741a523cd0d7)。

TIMESERV 是另一个相关的域服务标志，表示计算机当前是否具有权威性，如果 DC 失去连接，它可能会发生更改。 通过 NTP 查询时，处于此状态的 DC 将返回“未知层次”。 尝试多次后，DC 将记录系统事件 Time-Service 事件 36。

如果要将 DC 配置为 GTIMESERV，可以使用以下命令手动配置。 在这种情况下，DC 将其他计算机用作主时钟。 这可以是设备或专用计算机。

```
w32tm /config /manualpeerlist:"master_clock1,0x8 master_clock2,0x8" /syncfromflags:manual /reliable:yes /update
```

> [!NOTE]
> 有关详细信息，请参阅[配置 Windows 时间服务](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731191(v=ws.10))

如果 DC 安装了 GPS 硬件，你需要按这些步骤禁用 NTP 客户端并启用 NTP 服务器。

首先，禁用 NTP 客户端，然后使用这些注册表项更改启用 NTP 服务器。

```
reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\w32time\TimeProviders\NtpClient /v Enabled /t REG_DWORD /d 0 /f

reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\w32time\TimeProviders\NtpServer /v Enabled /t REG_DWORD /d 1 /f
```

接下来，重启 Windows 时间服务

```
net stop w32time && net start w32time
```

最后，指示此计算机使用的是可靠时间源。

```
w32tm /config /reliable:yes /update
```

若要检查是否已正确完成更改，你可以运行以下命令，这些命令会影响结果，如下所示。

```
w32tm /query /configuration

Value|Expected Setting|
----- | ----- |
AnnounceFlags| 5 (Local)|
NtpServer |(Local)|
DllName |C:\WINDOWS\SYSTEM32\w32time.DLL (Local)|
Enabled |1 (Local)|
NtpClient| (Local)|

w32tm /query /status /verbose

Value| Expected Setting|
----- | ----- |
Stratum| 1 (primary reference - syncd by radio clock)|
ReferenceId| 0x4C4F434C (source name: "LOCAL")|
Source| Local CMOS Clock|
Phase Offset| 0.0000000s|
Server Role| 576 (Reliable Time Service)|
```

#### <a name="windows-server-2016-on-3rd-party-virtual-platforms"></a>第三方虚拟平台上的 Windows Server 2016

Windows 虚拟化后，默认由管理程序负责提供时间。 但是，要使 Active Directory 正常工作，已加入域的成员需要与域控制器同步。 最好禁用来宾与任何第三方虚拟平台的主机之间的任何时间虚拟化。

#### <a name="discovering-the-hierarchy"></a>发现层次结构

由于到主时钟源的时间层次链在域中是动态的且可协商处理，因此你将需要查询特定计算机的状态，以便了解其时间源以及到主源时钟的链。 这有助于诊断时间同步问题。

假设你想要对特定客户端进行故障排除，则第一步是使用此 w32tm 命令了解其时间源。

```
w32tm /query /status
```

结果将显示源及其他内容。 “源”指示域中与你同步时间的用户。 这是此计算机时间层次结构的第一步。
接下来，依次使用上述源条目和 /StripChart 参数查找链中的下一个时间源。

```
w32tm /stripchart /computer:MySourceEntry /packetinfo /samples:1
```

以下命令同样有效，此命令列出了其在指定域中可以查找到的每个域控制器，并打印出结果，让你可以确定每个合作伙伴。 此命令将包括已手动配置的计算机。

 w32tm /monitor /domain:my_domain

使用列表，你可以在整个域中跟踪结果，并了解层次结构以及每个步骤中的时间偏移。 通过找到时间偏移明显增大的点，你可以查明导致时间错误的根源。 然后你可以打开 w32tm 日志记录，尝试了解导致时间错误的原因。

#### <a name="using-group-policy"></a>使用组策略
你可以使用组策略来实现更严格的准确性，例如，指定客户端来使用特定 NTP 服务器或控制低层次 OS 在虚拟化时的配置方式。
以下是可行方案和相关组策略设置的列表：

**虚拟化域** - 为控制 Windows 2012R2 中的虚拟化域控制器，确保这些控制器与其域而不是与 Hyper-V 主机同步时间，你可以禁用此注册表项。  对于 PDC，不建议禁用条目，因为 Hyper-V 主机将提供最稳定的时间源。 根据注册表的要求，你应在 w32time 服务变更后重启该服务。

 [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\VMICTimeProvider] "Enabled"=dword:00000000

**准确性敏感负载** - 对于时间准确性敏感工作负载，你可以配置计算机组以设置 NTP 服务器和任何相关的时间设置，例如轮询和时钟更新频率。 这通常由域来处理，但若要获得更多控制，你可以将特定计算机设置为直接指向主时钟。

组策略设置| “新值”|
----- | ----- |
NtpServer| ClockMasterName,0x8|
MinPollInterval| 6 - 64 秒|
MaxPollInterval| 6|
UpdateInterval| 100 - 每秒一次|
EventLogFlags| 3 - 所有特殊时间日志记录|

> [!NOTE]
> NtpServer 和 EventLogFlags 设置位于使用“配置 Windows NTP 客户端”设置的 System\Windows Time Service\Time 提供程序的下方。 其余 3 个设置位于使用“全局配置”设置的 System\Windows Time Service 的下方。

**远程准确性敏感负载（远程控制）** - 对于零售和支付信用行业 (PCI) 等分支域中的系统，除非配置了手动 NTP 时间源，否则 Windows 会使用当前站点信息和 DC 定位器来查找本地 DC。 此环境需要准确性达到 1 秒，以更快的收敛速度获得正确时间。 此选项允许 w32time 服务将时钟调整到之前的时间。 如果此时间可以接受且符合要求，则你可以创建以下策略。  与任何环境一样，请确保对网络进行测试和基线处理。

组策略设置| “新值”|
----- | ----- |
MaxAllowedPhaseOffset| 1，如果大于 1 秒，则将时钟设置为正确时间。|

MaxAllowedPhaseOffset 位于使用“全局配置”设置的 System\Windows Time Service 的下方。

> [!NOTE]
> 有关组策略和相关条目的详细信息，请参阅 TechNet 中的“[Windows 时间服务工具](windows-time-service-tools-and-settings.md)和设置”一文。

## <a name="azure-and-windows-iaas-considerations"></a>Azure 和 Windows IaaS 注意事项

### <a name="azure-virtual-machine-active-directory-domain-services"></a>Azure 虚拟机：Active Directory 域服务
如果运行 Active Directory 域服务的 Azure VM 属于现有的本地 Active Directory 林，则应禁用 TimeSync(VMIC)。 这将允许林中的所有 DC（无论是物理的还是虚拟的）使用单个时间同步层次结构。 请参阅最佳做法白皮书[“在 Hyper-V 中运行域控制器”](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd363553(v=ws.10))

### <a name="azure-virtual-machine-domain-joined-machine"></a>Azure 虚拟机：加入域的计算机
如果你托管的计算机是加入到现有 Active Directory 林的虚拟域或物理域，则最佳做法是禁用来宾的 TimeSync，并确保通过配置 Type=NTP5 的时间将 W32Time 配置为与其域控制器同步

### <a name="azure-virtual-machine-standalone-workgroup-machine"></a>Azure 虚拟机：独立工作组计算机
如果 Azure VM 既未加入域，也不是域控制器，则建议保留默认时间配置，并同步 VM 与主机。

## <a name="windows-application-requiring-accurate-time"></a>要求提供准确时间的 Windows 应用程序
### <a name="time-stamp-api"></a>时间戳 API
对 UTC（而不是时间）要求提供最高准确性的程序应使用 [GetSystemTimePreciseAsFileTime API](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimepreciseasfiletime)。 这可确保应用程序获取由 Windows 时间服务调整的系统时间。

### <a name="udp-performance"></a>UDP 性能
如果你的应用程序使用 UDP 通信处理事务，并且它有助于最大限度地降低延迟，则你可以使用一些相关的注册表项来配置一系列端口，使其从基本筛选引擎的端口中排除。 这种配置可降低延迟并增加吞吐量。 但只有经验丰富的管理员才能够对注册表进行更改。 此外，此变通办法会阻止防火墙保护端口。 有关详细信息，请参阅以下文章参考。

对于 Windows Server 2012 和 Windows Server 2008，你需要先安装修补程序。 请参考以下知识库文章：[在 Windows 8 和 Windows Server 2012 中运行多播接收器应用程序时数据报丢失](https://support.microsoft.com/kb/2808584)

### <a name="update-network-drivers"></a>更新网络驱动程序
某些网络供应商提供了驱动程序更新，可以提高驱动程序延迟和缓冲 UDP 数据包方面的性能。 请与网络供应商联系，查看是否存在有助于改善 UDP 吞吐量的更新。

## <a name="logging-for-auditing-purposes"></a>用于审核的日志记录
为符合时间跟踪规定，你可以手动存档 w32tm 日志、事件日志和性能监视器信息。 之后，存档的信息可用于证明过去特定时间的合规性。 以下要素用于指示准确性。

1. 使用“计算时间偏移”性能监视器计数器的时钟准确度。 这样可以以所需的准确性显示时钟。
2. 在 w32tm 日志中寻找“对等响应源”的时钟源。  消息文本后是 IP 地址或 VMIC，用于描述时间源以及要验证的参考时钟链中的下一个时间源。
3. 时钟调整状态，使用 w32tm 日志验证“ClockDispl Discipline: \*SKEW\*TIME\*”是否出现。 这表示此时 w32tm 处于有效状态。

### <a name="event-logging"></a>事件日志记录
若要获取全部情况，你还需要事件日志信息。 通过收集系统事件日志并筛选 Time-Server、Microsoft-Windows-Kernel-Boot 和 Microsoft-Windows-Kernel-General，你可能能够发现是否存在更改了时间的其他影响因素，例如，第三方。 排除外部干扰可能需要这些日志。 组策略会影响写入日志的事件日志。 有关详细信息，请参阅上述有关“使用组策略”部分。

### <a name="w32time-debug-logging"></a><a name="W32Logging"></a>W32time 调试日志记录
若要启用 w32tm 进行审核，可使用以下命令启用日志记录，该日志记录可显示时钟的定期更新并指示源时钟。 重启服务以启用新的日志记录。

有关详细信息，请参阅[如何启用 Windows 时间服务中的调试日志记录](https://support.microsoft.com/kb/816043)。

 w32tm /debug /enable /file:C:\Windows\Temp\w32time-test.log /size:10000000 /entries:0-73,103,107,110

### <a name="performance-monitor"></a>性能监视器
Windows Server 2016 Windows 时间服务公开了性能计数器，这些计数器可用于收集日志记录以进行审核。 可本地或远程记录这些计数器。 你可以记录“计算机时间偏移”和“往返”延时计数器。
与任何性能计数器类似，你可以远程监视它们并使用 System Center Operations Manager 创建警报。 例如，“时间偏移”偏离预期准确性时，你可以使用警报提醒自己。 有关详细信息，请参阅 [System Center 管理包](https://www.microsoft.com/download/details.aspx?id=44231)。

### <a name="windows-traceability-example"></a>Windows 可跟踪性示例
根据 w32tm 日志文件，你需要验证两部分信息。 第一部分指示日志文件当前为调整时钟。 这表明时钟在时间有争议时由 Windows 时间服务进行调整。

 151802 20:18:32.9821765s - ClockDispln Discipline:*SKEW*TIME* - PhCRR:223 CR:156250 UI:100 phcT:65 KPhO:14307 151802 20:18:33.9898460s - ClockDispln Discipline:*SKEW*TIME* - PhCRR:1 CR:156250 UI:100 phcT:64 KPhO:41 151802 20:18:44.1090410s - ClockDispln Discipline:*SKEW*TIME* - PhCRR:1 CR:156250 UI:100 phcT:65 KPhO:38

关键是你可以看到以 ClockDispln Discipline 为前缀的消息，它表明 w32time 正在与系统时钟交互。

接下来，你需要查找日志中争议时间点前的最新报告，从中了解当前用作参考时钟的源计算机。 这可能是 IP 地址、计算机名或 VMIC 提供程序，可表示它正在与 Hyper-V 的主机同步。 以下示例提供了 IPv4 地址 10.197.216.105。

 151802 20:18:54.6531515s - Response from peer 10.197.216.105,0x8 (ntp.m|0x8|0.0.0.0:123->10.197.216.105:123), ofs: +00.0012218s

验证参考时间链中的第一个系统后，你需要研究参考时间源中的日志文件并重复相同的步骤。 持续进行此操作，直到获取物理时钟（例如 GPS）或已知时间源（例如 NIST）。 如果参考时钟是 GPS 硬件，则可能还需要制造商的日志。

## <a name="network-considerations"></a>网络注意事项
NTP 协议算法取决于网络的对称性。 随着网络跃点的增加，不对称的可能性也会增加。 因此，很难预测你将在特定环境中看到的准确性类型。

Windows Server 2016 中的性能监视器和新的 Windows 时间计数器可用于评估环境的准确性和创建基线。 此外，你还可以执行故障排除，以确定网络中任何计算机的当前偏移。

对于网络的准确时间，有两个通用标准。 PTP（[精度时间协议 - IEEE 1588](https://www.nist.gov/el/intelligent-systems-division-73500/introduction-ieee-1588)）对网络基础结构有更严格的要求，但通常可以提供亚微秒的准确性。 NTP（[网络时间协议 - RFC 1305](https://tools.ietf.org/html/rfc1305)）可用于更广泛的网络和环境，以便于管理。

对于加入非域的计算机，Windows 默认支持简单 NTP (RFC2030)。 对于加入域的计算机，请使用名为 [MS-SNTP](/openspecs/windows_protocols/ms-sntp/8106cb73-ab3a-4542-8bc8-784dd32031cc) 的安全 NTP，它可利用域协商机密，并且与 RFC1305 和 RFC5905 中所述的 Authenticated NTP 相比，更便于管理。

加入域和非域的协议都需要 UDP 端口 123。 有关 NTP 最佳做法的详细信息，请参阅[网络时间协议当前最佳做法 IETF 草案](https://tools.ietf.org/html/draft-ietf-ntp-bcp-00)。

### <a name="reliable-hardware-clock-rtc"></a>可靠硬件时钟 (RTC)

除非超出某些限制，否则 Windows 不会逐步计时，而是严格控制时钟。 这意味着 w32tm 可以使用“时钟更新频率”设置定期调整时钟的频率，该设置在 Windows Server 2016 中默认设置为每秒 1 次。 如果时钟变慢了，它将提高频率，如果变快了，则会降低频率。 但是，在时钟频率调整之间的这段时间内，硬件时钟始终可控。 如果固件或硬件时钟存在问题，则计算机上的时间可能会变得不太准确。

这是你需要在环境中进行测试和基线处理的另一个原因。 如果“计算时间偏移”性能计数器在目标准确性方面不稳定，建议验证固件是否为最新。 作为另一项测试，你可以查看相同的硬件是否会出现相同的问题。

### <a name="troubleshooting-time-accuracy-and-ntp"></a>对时间准确性和 NTP 进行故障排除

你可以根据上述“发现层次结构”部分了解导致时间不准确的原因。 查看时间偏移，在层次结构中找到时间与其 NTP 源相差最大的点。 了解层次结构后，建议尝试了解该特定时间源未接收到准确时间的原因。

对于时间有所偏差的系统，你可以使用以下工具收集更多信息，以帮助确定问题和寻找解决方案。 下方的 UpstreamClockSource 引用是使用“w32tm/config/status”发现的时钟。

- 系统事件日志
- 使用以下内容启用日志记录：w32tm logs - w32tm /debug /enable /file:C:\Windows\Temp\w32time-test.log /size:10000000 /entries:0-300
- w32Time Registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W32Time
- 本地网络跟踪
- 性能计数器（来自本地计算机或 UpstreamClockSource）
- W32tm /stripchart /computer:UpstreamClockSource
- PING UpstreamClockSource，用于了解延迟以及源的跃点数
- Tracert UpstreamClockSource

问题| 症状| 解决方法|
----- | ----- | ----- |
| 本地 TSC 时钟不稳定。| 使用 Perfmon（物理计算机）- 同步时钟稳定时钟，但你仍会看到每 1-2 分钟出现多个 100us。 | 更新固件或验证不同的硬件不会显示相同的问题。|
| 网络延迟| w32tm stripchart 显示的 RoundTripDelay 超过 10 ms。 延时的变化会导致干扰且干扰时间长达往返时间的 1/2，例如，延时仅发生在单一方向上。<br><br>如 PING 所示，UpstreamClockSource 是多跃点。 TTL 应接近 128。<br><br>使用 Tracert 查找每个跃点处的延迟。  | 查找时间上更接近的时钟源。 解决方案是将源时钟安装在同一段上，或手动指向地理位置更近的源时钟。 对于域方案，请添加具有 GTimeServ 角色的计算机。 |
无法可靠地访问 NTP 源| W32tm/stripchart 周期性返回“请求超时” |NTP 源无响应|
NTP 源无响应| 检查用于 NTP 客户端源计数、NTP 服务器传入请求、NTP 服务器传出响应的 Perfmon 计数器，然后确定与基线相比的用法。| 使用服务器性能计数器确定关于基线的负载是否已更改。<br><br>是否存在网络拥塞问题？|
未使用最准确时钟的域控制器| 拓扑中的更改或最近添加的主时间时钟。| w32tm /resync /rediscover|
客户端时钟出现偏差| 系统事件日志中的 Time-Service 事件 36 和/或日志文件中的文本描述了以下内容：“NTP 客户端时间源计数”计数器从 1 变为 0|对上游源进行故障排除，然后了解其是否出现了性能问题。|

### <a name="baselining-time"></a>对时间进行基线处理

基线处理至关重要，可确保你率先了网络的性能和准确性，然后在将来出现问题时与基线进行对比。 建议对根 PDC 或标记有 GTIMESRV 的任何计算机进行基线处理。 此外，建议在每个林中对 PDC 进行基线处理。 最后，选择具有重要特征（例如距离或高负载）的任何关键 DC 或计算机，然后对它们进行基线处理。

对 Windows Server 2016 vs 2012 R2 进行基线处理也有帮助，但由于 Windows Server 2012R2 不具有性能计数器，因此你只能将 w32tm/stripchart 用作对比工具。 你应选择两台具有相同特征的计算机，或者更新计算机并在更新后对比结果。 如需详细了解如何在版本 2016 和 2012 之间进行详细测量，请参阅“Windows 时间测量附录”。

使用所有的 w32time 性能计数器，收集至少一周的数据。 这将确保你有足够的引用来说明网络中一段时间的各种情况，并确保你有足够的运行来保证时间准确性是稳定的。

### <a name="ntp-server-redundancy"></a>NTP 服务器冗余

对于加入非域的计算机或 PDC 中使用的手动 NTP 服务器配置，在可用情况下采用多个服务器是一种很好的冗余措施。 假设所有源都准确且稳定，它还可以提供更高的准确性。 但如果拓扑设计不佳或时间源不稳定，则相应的准确性可能会较差，因此请务必谨慎。 w32time 可手动引用的受支持时间服务器的限制为 10。

## <a name="leap-seconds"></a>闰秒

因气候和地质事件，地球的自转周期会随时间而变化。 通常，周期每隔几年变化约 1 秒。 原子时间变化太大时，会插入大约 1 秒的校正值，称为闰秒。 这样做后差值不会超过 0.9 秒。 宣布此校正的时间比实际校正时间提早六个月。 在 Windows Server 2016 的早期版本中，Microsoft 时间服务尚未注意到闰秒概念，而是依靠外部时间服务来解决此问题。 随着 Windows Server 2016 的时间准确性提高，Microsoft 正在研究一种更合适的解决方案来解决闰秒问题。

## <a name="secure-time-seeding"></a>安全时间种子设定

Server 2016 中的 W32time 包含安全时间种子设定功能。 此功能确定传出 SSL 连接中的大致当前时间。 此时间值用于监视本地系统时钟和纠正任何重大错误。 有关该功能的详细信息，请参阅[这篇博客文章](/archive/blogs/w32time/secure-time-seeding-improving-time-keeping-in-windows)。 在使用可靠时间源和监视状态良好的计算机（包括对时间偏移的监视）进行部署的过程中，你可以选择不使用“安全时间种子设定”功能，而是依靠现有的基础结构。

可以按以下步骤禁用此功能：

1. 在特定计算机上，将 UtilizeSSLTimeData 注册表配置值设置为 0：

    ```
    reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\w32time\Config /v UtilizeSslTimeData /t REG_DWORD /d 0 /f
    ```

2. 如果由于某种原因无法立即重启计算机，你可以通知 W32time 服务有关配置更新的信息。 根据从 SSL 连接中收集的时间数据，这会停止进行时间监视和执行。

    ```
    W32tm.exe /config /update
    ```

3. 重启计算机会使设置立即生效，还会使它停止从 SSL 连接收集任何时间数据。 后者开销非常小，不会影响性能。

4. 若要在整个域中应用此设置，请将 W32time 组策略设置中的 UtilizeSSLTimeData 值设置为 0 并公布该设置。 组策略客户端修改设置时，W32time 服务会收到通知，然后它将使用 SSL 时间数据停止进行时间监视和执行。 每个计算机重启时，SSL 时间数据收集都会停止。 如果域中有便携式超薄笔记本电脑/平板电脑和其他设备，建议将此类计算机从此策略更改中排除。 这些设备最终会遇到电源耗尽这种情况，因此需要“安全时间种子设定”功能来引导其时间。