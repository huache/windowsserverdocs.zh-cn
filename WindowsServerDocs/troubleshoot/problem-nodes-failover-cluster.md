---
title: 删除节点时出现问题
description: 本文介绍了从活动故障转移群集成员身份中删除节点时遇到的问题。
ms.prod: windows-server
ms.technology: server-general
ms.date: 05/28/2020
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: 30714e8a9c5ca4ad13ed6757c6ce1da211b279ac
ms.sourcegitcommit: ef089864980a1d4793a35cbf4cbdd02ce1962054
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84150225"
---
# <a name="having-a-problem-with-nodes-being-removed-from-active-failover-cluster-membership"></a>从活动故障转移群集成员身份中删除节点时遇到问题

本文介绍如何解决在其中随机从主动故障转移群集成员身份中删除节点的问题。

## <a name="symptoms"></a>症状

发生此问题时，你会看到类似于下面的事件日志：

![事件1135](media/problem-nodes-failover-cluster/1135-1.png)

此事件将在群集中的所有节点上进行记录，但删除的节点除外。 此事件的原因是群集中的节点之一将该节点标记为关闭。 然后，它会通知事件的所有其他节点。 当向节点发出通知时，它们将停止并将其检测信号连接中断到关闭的节点。

## <a name="what-caused-the-node-to-be-marked-down"></a>将节点标记为关闭状态的原因

Windows 2008 或 2008 R2 故障转移群集中的所有节点都通过设置为允许在此网络上进行群集网络通信的网络相互通信。 节点将跨这些网络将检测信号数据包发送到所有其他节点。 这些数据包应由其他节点接收，然后发回响应。 群集中的每个节点都有其自己的检测信号，它会进行监视以确保网络正常运行，其他节点处于启动状态。 下面的示例可帮助阐明这一点：

![Nodes](media/problem-nodes-failover-cluster/Node2.png)

如果未返回这些数据包中的任何一个，则会将特定检测信号视为失败。 例如，W2K8 将发送请求并接收从 W2K8 到检测信号数据包的响应，以便它确定网络和节点是否已启动。  如果 W2K8 将请求发送到 W2K8-W2K8-节点 2-节点 2-节点2和 W2K8，则会将其视为丢失的检测信号，-节点将跟踪该请求。  此缺少的响应可能会让 W2K8 在收到另一个检测信号请求之前关闭网络。

默认情况下，群集节点在5秒内限制为5秒，然后将连接标记为关闭状态。 因此，如果 W2K8-节点在时间段内未收到响应5次，则会将该特定路由视为 W2K8。 如果其他路由仍被视为向上路由，W2K8 将保留为活动成员。

如果所有路由都标记为关闭，则会将其从活动的故障转移群集成员身份中删除，并记录在第一部分中看到的事件1135。 在 W2K8-节点2上，群集服务将终止并重新启动，因此它可以尝试重新加入群集。

有关如何处理使用三个或更多节点的特定路由的详细信息，请参阅 Jeff Hughes 编写的["已分区" 群集网络](/archive/blogs/askcore/partitioned-cluster-networks)博客。

## <a name="now-that-we-know-how-the-heartbeat-process-works-what-are-some-of-the-known-causes-for-the-process-to-fail"></a>现在我们知道了检测信号过程的工作原理，该过程的一些已知原因会失败。

1. 实际网络硬件故障。 如果数据包在节点之间的某个位置丢失，则检测信号会失败。 涉及两个节点的网络跟踪会显示此情况。

2. 网络连接的配置文件可能会从域弹跳为公用，并再次返回到域。 在这些更改的转换过程中，可能会阻止网络 i/o。 查看网络配置文件操作日志可查看是否是这种情况。 可以通过打开 "事件查看器" 并导航到 "应用程序和服务 Logs\Microsoft\Windows\NetworkProfile\Operational." 找到此日志。 查看事件 ID 为1135中提到的节点上此日志中的事件，并查看此时是否正在更改该配置文件。 如果是这样，请查看知识库文章：[从 "域" 更改为 windows 7 或 Windows Server 2008 R2 中的 "公共"](https://support.microsoft.com/help/2524478/the-network-location-profile-changes-from-domain-to-public-in-windows)。

3. 已在服务器上启用了 IPv6，但在 Windows 防火墙中为入站和出站禁用了以下两个规则：

    - 核心网络-邻居发现播发
    - 核心网络-邻居发现请求

4. 防病毒软件也可能干扰此过程。 如果怀疑这样做，请通过禁用或卸载软件进行测试。 为此，请自行承担风险，因为此时将不会受到病毒防护。

5. 网络延迟也可能导致这种情况发生。 它们可能不会在节点之间丢失，但在超时期限过期之前，它们可能无法快速到达节点。

6. IPv6 是故障转移群集将用于其检测信号的默认协议。 检测信号本身是 UDP 单播网络数据包，通过端口3343进行通信。 如果未正确配置交换机、防火墙或路由器以允许此流量，则可能会遇到此类问题。

7. IPsec 安全策略刷新也可能导致此问题。 具体的问题是，在 IPSec 组策略更新过程中，具有高级安全性的 Windows 防火墙（WFAS）已对所有 IPsec 安全关联（SAs）进行了破坏。 发生这种情况时，将阻止所有网络连接。 当 renegotiating 安全关联时，如果使用 Active Directory 执行身份验证时出现延迟，则这些延迟（其中所有网络通信都被阻止）也会阻止群集检测信号，从而导致群集运行状况监视在节点未在5秒阈值内响应的情况下检测到停机。

8. 旧或过期网卡驱动程序和/或固件。  有时，网络卡或交换机的错误配置还可能会导致检测信号丢失。

9. 新式网卡和虚拟网卡可能出现数据包丢失。  这可以通过打开性能监视器并添加计数器 "Network Interface\Packets Received Discarded" 进行跟踪。  此计数器是累积计数器，只会增加服务器重启。  在此看到大量的数据包可能是因为网卡上的接收缓冲区设置得太低，或者服务器执行缓慢，无法处理入站流量。  每个网卡制造商选择是否在网卡的属性中公开这些设置，因此，您需要参考制造商的网站以了解如何增加这些值，并使用建议的值。  如果你在 VMware 上运行，以下博客更详细地讨论了这一问题，其中包括如何判断这是否是问题，并使你在 VMWare 文章中了解要更改的设置。

    [正在从 VMWare ESX 上的故障转移群集成员身份中删除的节点](/archive/blogs/askcore/nodes-being-removed-from-failover-cluster-membership-on-vmware-esx)

这些事件是记录这些事件的最常见原因，但也有其他原因。 此博客的要点是让您深入了解该过程，并提供要查找的内容的想法。 有些会将以下值提升到其最大值，以尝试使此问题停止。

|参数|默认|范围|
|---|---|---|
|**SameSubnetDelay**|1000毫秒|250-2000 毫秒|
|**CrossSubnetDelay**|1000毫秒|250-4000 毫秒|
|**SameSubnetThreshold**|5|3-10|
|**CrossSubnetThreshold**|5|3-10|
||||

将这些值增大到最大值可能会使事件和节点删除消失，而只是掩盖问题。 它不会修复任何问题。 最好的做法是发现检测信号故障的根本原因，并修复它。 增加这些值的唯一真正需求是在多站点方案中，节点驻留在不同的位置，并且不能克服网络延迟。
