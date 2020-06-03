---
title: 排查事件 ID 1135 的群集问题
description: 描述如何排查事件 ID 1135 的群集服务启动问题。
ms.date: 05/28/2020
ms.openlocfilehash: d59f8b89e89ea7ff42aecd79670465aee8d63524
ms.sourcegitcommit: 5fac756c2c9920757e33ef0a68528cda0c85dd04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84306526"
---
# <a name="troubleshooting-cluster-issue-with-event-id-1135"></a>排查事件 ID 1135 的群集问题

本文将帮助你诊断和解决事件 ID 1135，该事件可能会在故障转移群集环境中的群集服务启动期间记录。

## <a name="start-page"></a>起始页

事件 ID 1135 表示从活动故障转移群集成员身份中删除了一个或多个群集节点。 可能伴随以下症状：

- 正在从 active 故障转移群集成员身份删除群集 Failover\nodes：[从活动故障转移群集成员身份中删除节点时遇到问题](/problem-nodes-failover-cluster.md)
- 事件 ID 1069[事件 id 1069-群集服务或应用程序可用性](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc756225(v=ws.10))
- 仲裁丢失[事件 id 1177](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc773498(v=ws.10))的事件 id 1177-仲裁需要仲裁和连接
- 群集服务暂停的事件 ID 1006：[事件 id 1006-群集服务启动](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc773418(v=ws.10))

建议将验证和网络测试作为一个初始故障排除步骤，以确保不存在可能导致问题的配置问题。

### <a name="check-if-installed-the-recommended-hot-fixes"></a>检查是否已安装推荐的热修补程序

群集服务是控制故障转移群集操作的所有方面并管理群集配置数据库的基本软件组件。 如果你看到事件 ID 1135，Microsoft 建议你安装以下知识库文章中提到的修补程序，并重新启动群集的所有节点，然后观察是否再次出现问题。

- [Windows Server 2012 R2 修补程序](https://support.microsoft.com/help/2920151)
- [Windows Server 2012 修补程序](https://support.microsoft.com/help/2784261)
- [Windows Server 2008 R2 修补程序](https://support.microsoft.com/help/2545685)

### <a name="check-if-the-cluster-service-running-on-all-the-nodes"></a>检查是否在所有节点上运行的群集服务

按照 Windows 操作系统中的以下命令验证群集服务是否连续运行且可用。

#### <a name="for-windows-server-2008-r2-cluster"></a>对于 Windows Server 2008 R2 群集

从提升权限的 cmd 提示符运行： **cluster.exe 节点/stat**  

#### <a name="for-windows-server-2012-and-windows-server-2012-r2-cluster"></a>对于 Windows Server 2012 \ 和 Windows Server 2012 R2 群集

运行 PS 命令：**群集节点/status**  

群集服务是否在所有节点上持续运行和可用？

## <a name="solution-for-cluster-service-is-failing"></a>群集服务的解决方案失败

如果群集服务出现故障，请使用本文进行故障排除： [Windows Server 2008 和2008R2 故障转移群集启动开关](/archive/blogs/askcore/windows-server-2008-and-2008r2-failover-cluster-startup-switches)。


## <a name="several-scenarios-of-event-id-1135"></a>事件 ID 1135 的几个方案

我们希望你进一步了解群集的所有节点上的系统事件日志。 查看正在节点上看到的事件 ID 1135，并复制此事件的所有实例。 这样您就可以方便地查看和查看。

```console
Event ID 1135
Cluster node ' **NODE A** ' was removed from the active failover cluster membership. The Cluster service on this node may have stopped. This could also be due to the node having lost communication with other active nodes in the failover cluster. Run the Validate a Configuration wizard to check your network configuration. If the condition persists, check for hardware or software errors related to the network adapters on this node. Also check for failures in any other network components to which the node is connected such as hubs, switches, or bridges.
```

有三种典型方案：

### <a name="scenario-a"></a>方案 A

你正在查看所有事件，并且群集中的所有节点都指示节点 A 已失去通信。

![方案 a 方案 ](media/troubleshooting-cluster-event-id-1135/18647.png)
 ![ a](media/troubleshooting-cluster-event-id-1135/18648.png)

在节点 A 上看到系统日志时，可能会出现群集中所有剩余节点的事件。

#### <a name="solution"></a>解决方案

这很明显表明，出现问题时，原因可能是网络拥塞或与节点 A 的通信丢失。

应查看并验证网络配置和通信问题。 请记得查找与节点 A 相关的问题。

### <a name="scenario-b"></a>方案 B

你正在查看节点上的事件，并告诉我们你的群集分散在两个站点中。 站点1上的节点 A、节点 B 和节点 C 以及站点 2 & NODE E。

![方案 B](media/troubleshooting-cluster-event-id-1135/18649.png)

在节点 A、B 和 C 上，你会看到记录的事件与节点 D & 的连接。同样，当你在节点 D & E 上看到事件时，这些事件表明我们失去了与 A、B 和 C 的通信。

![方案 B](media/troubleshooting-cluster-event-id-1135/18650.png)

#### <a name="solution"></a>解决方案

如果看到类似活动，则表明存在通信故障，通过连接这些站点的链接。 建议你查看跨站点的连接，如果这是通过 WAN 连接进行的，我们建议你向 ISP 验证连接性。

### <a name="scenario-c"></a>方案 C

你正在查看节点上的事件，你会发现节点名称不会以任何特定模式进行计算。 假设你的群集分散在两个站点中。 节点 A、节点 B 和节点 C，在站点1和节点 D 上，在站点 2 & NODE E。

- 在节点 A 上：可以看到节点 B、D、E 的事件。
- 在节点 B 上：看到节点 C、D、E 的事件。
- 在节点 C 上：看到节点 A、B、E 的事件。
- 在节点 D 上：看到节点 A、C、E 的事件。
- 在节点 E 上：看到节点 B、C、D 的事件。
- 或任何其他组合。

![方案 C](media/troubleshooting-cluster-event-id-1135/18651.png)

#### <a name="solution"></a>解决方案

当节点之间的网络通道侧重点并且群集通信消息无法及时进入时，这种情况可能会发生，这使得群集可以感觉节点之间的通信会丢失，导致从群集成员身份中删除节点。

## <a name="review-cluster-networks"></a>查看群集网络

建议你查看群集网络，方法是逐个检查以下三个选项以继续此故障排除指南。

### <a name="check-for-antivirus-exclusion"></a>检查防病毒排除

从运行群集服务的服务器上的病毒扫描中排除以下文件系统位置：

- 文件共享见证的路径

- *%Systemroot%\Cluster 文件夹*

将防病毒软件中的实时扫描组件配置为排除以下目录和文件：

- 默认虚拟机配置目录（C:\ProgramData\Microsoft\Windows\Hyper-V）

- 自定义虚拟机配置目录

- 默认虚拟硬盘驱动器目录（C:\Users\Public\Documents\Hyper-V\Virtual 硬盘）

- 自定义虚拟硬盘驱动器目录

- 自定义复制数据目录（如果使用的是 Hyper-v 副本）

- 快照目录

- mms

    > [!NOTE]
    > 此文件可能必须配置为防病毒软件中的进程排除。）

- Vmwp

    > [!NOTE]
    > 此文件可能必须配置为防病毒软件中的进程排除。

此外，将实时迁移与群集共享卷一起使用时，请排除 CSV 路径*C:\Clusterstorage*及其所有子目录。 如果要解决故障转移问题或安装群集服务和防病毒软件的一般问题，请暂时卸载防病毒软件，或与软件制造商核实，以确定防病毒软件是否适用于群集服务。 在大多数情况下，只需禁用防病毒软件就会不足。 即使您禁用了防病毒软件，在您重新启动计算机时仍会加载筛选器驱动程序。

### <a name="check-for-network-port-configuration-in-firewall"></a>检查防火墙中的网络端口配置

群集服务控制服务器群集操作并管理群集数据库。 群集是充当单台计算机的独立计算机的集合。 管理者、程序员和用户将群集视为单个系统。 软件在群集的节点之间分发数据。 如果某个节点出现故障，其他节点将提供以前由缺少的节点提供的服务和数据。 添加或修复节点时，群集软件会将一些数据迁移到该节点。

系统服务名称： **ClusSvc**  

|应用程序|协议|端口|
|---|---|---|
|群集服务|UDP|3343|
|群集服务|TCP|3343（在执行节点加入操作期间，此端口是必需的。）|
|RPC|TCP|135|
|群集管理|UDP|137|
|Kerberos|UDP\TCP|464 *|
|SMB|TCP|445|
|随机分配的高 UDP 端口 * *|UDP|介于1024和65535之间的随机端口号<br/>介于49152和 65535 * * * 之间的随机端口号|
||||

> [!NOTE]
> 此外，对于 Windows Server 2008 及更高版本上的 Windows 故障转移群集的成功验证，允许 ICMP4、ICMP6 的入站和出站流量。

- 有关详细信息，请参阅[创建 Windows Server 2012 故障转移群集失败，出现错误 0xc000005e](https://support.microsoft.com/help/2830510)。

- 有关如何自定义这些端口的详细信息，请参阅 "参考" 部分中的[Windows 的服务概述和网络端口要求](https://support.microsoft.com/help/832017/)。

这是 Windows Server 2012、Windows 8、Windows Server 2008 R2、Windows 7、Windows Server 2008 和 Windows Vista 中的范围。

除此之外，请运行以下命令，检查防火墙中的网络端口配置。 例如：此命令可帮助确定用于故障转移群集的端口 3343 available\open：

```console
netsh advfirewall firewall show rule name="Failover Clusters (UDP-In)" verbose
```

### <a name="run-the-cluster-validation-report-for-any-errors-or-warnings"></a>为任何错误或警告运行群集验证报告

群集验证工具运行一组测试，以验证您的硬件和设置是否与故障转移群集兼容。

请按照以下说明执行操作：

1. 为任何错误或警告运行群集验证报告。 有关详细信息，请参阅[了解群集验证测试：网络](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771323(v=ws.11)?redirectedfrom=MSDN)

    ![subhatt1](media/troubleshooting-cluster-event-id-1135/18653.png)

2. 验证网络的警告和错误。 有关详细信息，请参阅[了解群集验证测试：网络](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771323(v=ws.11)?redirectedfrom=MSDN)。

    ![按类别网络列出的结果 ](media/troubleshooting-cluster-event-id-1135/18654.png) ![](media/troubleshooting-cluster-event-id-1135/18655.png)

#### <a name="check-the-list-network-binding-order"></a>检查列出网络绑定顺序

此测试将列出网络绑定到每个节点上的适配器的顺序。

"适配器和绑定" 选项卡按网络服务访问连接的顺序列出了连接。 这些连接的顺序反映了将一般 TCP/IP 调用/数据包发送到网络的顺序。

按照以下步骤更改网络适配器的绑定顺序：

1. 单击 "**开始**"，再单击 "**运行**"，键入 Ncpa，然后单击 **"确定"**。 可以在 "**网络连接**" 窗口的 " **LAN 和高速 Internet** " 部分中查看可用连接。

2. 在 "**高级**" 菜单上，单击 "**高级设置**"，然后单击 "**适配器和绑定**" 选项卡。

3. 在 "**连接**" 区域中，选择要在列表中向上移动的连接。 使用箭头按钮移动连接。 作为一般规则，与网络通信的卡（域连接、路由到其他网络等）应为第一个绑定（列表顶部）。

群集节点是多宿主系统。 网络优先级影响 DNS 客户端的出站网络连接。 用于客户端通信的网络适配器应位于绑定顺序的顶部。 非路由网络可处于较低优先级。 在 Windows Server 2012 和 Windows Server2012 R2 中，群集网络驱动程序（NETFT。SYS）适配器会自动置于绑定顺序列表的底部。

#### <a name="check-the-validate-network-communication"></a>选中 "验证网络通信"

网络延迟也可能导致这种情况发生。 它们可能不会在节点之间丢失，但在超时期限过期之前，它们可能无法快速到达节点。

此测试可验证被测服务器能否以可接受的延迟在所有网络上进行通信。

例如：在 "验证网络通信" 下，可能会看到以下消息，其中显示了网络延迟问题。

```console
Succeeded in pinging network interface node003.contoso.com IP Address 192.168.0.2 from network interface node004.contoso.com IP Address 192.168.0.3 with maximum delay 500 after 1 attempt(s).
Either address 10.0.0.96 is not reachable from 192.168.0.2 or **the ping latency is greater than the maximum allowed 2000 ms** This may be expected, since network interfaces node003.contoso.com - Heartbeat Network and node004.contoso.com - Production Network are on different cluster networks
Either address 192.168.0.2 is not reachable from 10.0.0.96 or **the ping latency is greater than the maximum allowed 2000 ms** This may be expected, since network interfaces node004.contoso.com - Production Network and node003.contoso.com - Heartbeat Network for MSCS are on different cluster networks
```

对于多站点群集，可以增加超时值。 有关详细信息，请参阅[在多站点故障转移群集中配置检测信号和 DNS 设置](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd197562(v=ws.10)?redirectedfrom=MSDN)。

请与 ISP 联系以了解是否存在任何 WAN 连接问题。

检查是否遇到以下任何问题。

##### <a name="network-packets-lost-between-nodes"></a>节点之间丢失的网络数据包

1. 使用性能检查数据包丢失

    如果数据包在节点之间的某个位置丢失，则检测信号会失败。 我们可以通过使用性能监视器查看 "网络 Interface\Packets 收到的丢弃" 计数器来轻松找出这一问题。 添加此计数器后，查看平均值、最小值和最大值，如果它们是大于零的任何值，则需要为适配器调整接收缓冲区。

    ![添加计数器](media/troubleshooting-cluster-event-id-1135/18652.png)

    如果在 VmWare 虚拟化平台上遇到网络数据包丢失的情况，请参阅 "VmWare 虚拟化平台上安装的群集" 部分。

2. 升级 NIC 驱动程序

    出现此问题的原因可能是已过时的 NIC drivers\Integration 组件（IC） \VmTools 或错误的 NIC 适配器。
    如果物理计算机上的节点之间丢失网络数据包，请将网络适配器驱动程序更新。 旧或过期网卡驱动程序和/或固件。
    有时，网络卡或交换机的错误配置还可能会导致检测信号丢失。

##### <a name="cluster-installed-in-the-vmware-virtualization-platform"></a>VmWare 虚拟化平台中安装的群集

在 VMware 环境下验证 VMware 适配器问题。 

如果在高流量突发期间丢弃数据包，则可能出现此问题。 确保没有发生流量筛选（例如，使用邮件筛选器）。 消除这种可能性后，逐渐增加来宾操作系统中的缓冲区数量并进行验证。

若要减少突发流量丢弃流量，请遵循以下步骤：

1. 使用 Windows 键 + R 打开 "运行" 框。
2. 键入 devmgmt.msc，然后按**enter**。
3. 展开 "**网络适配器**"  
4. 右键单击**vmxnet3，然后单击 "属性"。**  
5. 单击“高级”**** 选项卡。
6. 单击 " **Small Rx 缓冲区**" 并增加值。 默认值为512，最大值为8192。
7. 单击 " **Rx 环状 #1**大小并增加值。 默认值为1024，最大值为4096。

查看以下 Url，验证 vmware 适配器在 VMware 环境中的问题：

- [正在从 VMWARE ESX 上的故障转移群集成员身份中删除节点？](/archive/blogs/askcore/nodes-being-removed-from-failover-cluster-membership-on-vmware-esx)。

- [ESXi 中的 VMXNET3 vNIC 上的来宾操作系统级别的大数据包丢失](https://kb.vmware.com/s/article/2039495)

##### <a name="noticed-any-network-congestion"></a>注意到任何网络拥塞

网络拥塞也可能导致网络连接问题。

验证网络配置为每 MS 和供应商建议，请参阅[配置 Windows 故障转移群集网络](/archive/blogs/askcore/configuring-windows-failover-cluster-networks)。

##### <a name="check-the-network-configuration"></a>检查网络配置

如果仍不起作用，请检查是否已在群集 GUI 中查看分区网络，或者是否已在检测信号 NIC 上启用了 NIC 组合。

如果在群集 GUI 中看到分区网络，请参阅["已分区的群集网络"](/archive/blogs/askcore/partitioned-cluster-networks)以解决此问题。

如果在检测信号 NIC 上启用了 NIC 组合，请按照组供应商的建议检查组合软件功能。

##### <a name="upgrade-the-nic-drivers"></a>升级 NIC 驱动程序

此问题可能是由于 NIC 驱动程序过时或 NIC 适配器错误引起的。

如果物理计算机上的节点之间丢失了网络数据包，请将网络适配器驱动程序更新。 旧或过期网卡驱动程序和/或固件。

有时，网络卡或交换机的错误配置还可能会导致检测信号丢失。

##### <a name="check-the-network-configuration"></a>检查网络配置

如果仍不起作用，请检查是否已在群集 GUI 中查看分区网络，或者是否已在检测信号 NIC 上启用了 NIC 组合。
