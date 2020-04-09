---
title: RAS 网关 GRE 隧道吞吐量和性能
description: 本主题面向信息技术（IT）专业人员，提供有关 RAS 网关通用路由封装（GRE）隧道的吞吐量性能信息。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: c051b2ec-de0f-49d1-82b9-5742b259cd7c
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 3ac381270714ecebc0aa624152700155fe170400
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80814460"
---
# <a name="ras-gateway-gre-tunnel-throughput-and-performance"></a>RAS 网关 GRE 隧道吞吐量和性能

>适用于： Windows Server \(半年通道\)

本主题介绍如何在非软件定义的网络 \(SDN\) 基于 SDN 的测试环境中，了解远程访问服务器 \(RAS\) 网关通用路由封装 \(GRE\) 在 Windows Server 版本1709上的隧道性能。

RAS 网关是一种软件路由器和网关，可在单租户模式或多租户模式下使用。 本主题讨论单租户模式，具有故障转移群集的高可用性配置。 本主题中提供的 GRE 隧道性能统计信息对 singele 租户和多租户模式下的 RAS 网关都有效。

>[!NOTE]
>故障转移群集是一种 Windows Server 功能，可让你将多台服务器组合到容错群集中。 有关详细信息，请参阅[故障转移群集](../../../failover-clustering/failover-clustering-overview.md)

单租户模式允许任意规模的组织将网关部署为外部网关，或将 Internet\-面向 Internet 的虚拟专用网络 \(VPN\) 服务器。 在单租户模式下，可以在物理服务器或虚拟机 \(VM\)上部署 RAS 网关。 本主题介绍在故障转移群集中配置的两个虚拟机 \(Vm\) 上的 RAS 网关部署。

>[!IMPORTANT]
>由于 GRE 隧道提供了封装但未加密，因此不应将 RAS 网关配置为使用 GRE 作为 Internet 边缘网关。 若要了解有关使用 GRE 隧道的 RAS 网关的最佳用法，请参阅[Windows Server 中的 GRE 隧道](gre-tunneling-windows-server.md)。

GRE 是一种轻型隧道协议，可以将虚拟点中的各种网络层协议封装\-到 Internet 协议 Internet 上\-点链接。 Microsoft GRE 实现封装了 IPv4 和 IPv6。

有关详细信息，请参阅 " [Ras 网关](https://docs.microsoft.com/windows-server/remote/remote-access/ras-gateway/ras-gateway#bkmk_deploy)" 主题中的**Ras 网关部署方案**部分。 

在此测试方案（如下图中所示）中，测量的流量流从组织 Intranet 2 移到组织 Intranet 1。 租户工作负荷 Vm 使用 RAS 网关将网络流量从 Intranet 2 发送到 Intranet 1。

![RAS 网关 GRE 隧道测试方案概述](../../media/GRE-Tunnel-Perf/Gre-Infrastructure.jpg)

## <a name="test-environment-configuration"></a>测试环境配置

本部分提供有关测试环境和 RAS 网关配置的信息。

在测试环境中，RAS 网关 Vm 部署在故障转移群集中的\-Hyper-v 主机上，以实现高可用性。

### <a name="hyper-v-host-configuration"></a>Hyper-v 主机配置\-

两个\-Hyper-v 主机配置为支持测试方案，采用以下方式。 

- 两个双\-宿主物理计算机配置了 Windows Server 1709 版
- 这两个服务器中的两个物理网络适配器均连接到不同的子网，这两者都表示组织 Intranet 的子网。 网络和支持硬件的容量均为 10 GBps。
- 物理服务器上的超线程已禁用。 这提供了物理 Nic 的最大吞吐量。
- 超级\-V server 角色安装在两台服务器上，并配置了两个外部超\-V 虚拟交换机，每个物理网络适配器一个虚拟交换机。
- 由于这两个服务器都连接到相同的 intranet，因此这些服务器可以互相通信。
- 通过 intranet 网络在故障转移群集中配置 Hyper-v 主机的\-Hyper-v 主机。 

>[!NOTE]
>有关详细信息，请参阅 [Hyper-V 虚拟交换机](https://docs.microsoft.com/windows-server/virtualization/hyper-v-virtual-switch/hyper-v-virtual-switch)。

### <a name="vm-configuration"></a>VM 配置

配置了两个 Vm 以按以下方式支持测试方案。

- 在每台服务器上，安装了运行 Windows Server 版本1709的虚拟机。 为每个 VM 配置了10个核心和 8 GB RAM。
- 还为每个 VM 配置了两个虚拟网络适配器。 一个虚拟网络适配器连接到 Intranet 1 虚拟交换机，另一个虚拟网络适配器连接到 Intranet 2 虚拟交换机。
- 每个 VM 都安装了 RAS 网关，并配置为基于 GRE\-的 VPN 服务器。
- 在故障转移群集中配置网关 Vm。 群集后，一个 VM 处于活动状态，而另一个 VM 为被动 VM。

### <a name="workload-hyper-v-hosts-and-vms"></a>工作负荷超级\-V 主机和 Vm

对于此测试，在 intranet 上安装了两个工作负荷\-V 主机，每个主机都安装了一个 VM。 如果要在自己的测试环境中复制此测试，可以根据自己的需要安装任意多个工作负荷服务器和 Vm。

- 工作负荷\-V 主机上安装了一个连接到组织 Intranet 的物理网络适配器。
- 在 "超级\-V 虚拟交换机" 中，每个主机上创建一个虚拟交换机。 交换机为外部交换机，并绑定到连接到 intranet 的一个网络适配器。
- 工作负荷 Vm 配置为具有 2 GB RAM 和2个内核。
- 工作负荷 Vm 每个都有一个连接到 intranet 虚拟交换机的虚拟网络适配器。

### <a name="traffic-generator-tool"></a>流量生成器工具

此测试中使用的流量生成器工具是 ctsTraffic 工具。 此工具的 Git 存储库位于[https://github.com/Microsoft/ctsTraffic](https://github.com/Microsoft/ctsTraffic)。

## <a name="ras-gateway-performance"></a>RAS 网关性能

本部分中的插图介绍了具有多个 TCP 连接的 GRE 隧道吞吐量的任务管理器显示。

在配置为 GRE RAS 网关的多个\-核心 Vm 上，最多可以达到 2.0 Gbps 的吞吐量。

### <a name="gre-tunnel-performance-with-multiple-tcp-sessions"></a>具有多个 TCP 会话的 GRE 隧道性能

对于多个 TCP 会话，CPU 利用率达到100%，且 GRE 隧道上的最大吞吐量为 2.0 Gbps。

下图描述了这两个 RAS 网关 Vm 上的 CPU 使用率。 Active VM、RAS 网关 VM #1 位于左侧，而被动 VM "RAS 网关 VM #2" 位于右侧。

![任务管理器中的网关 VM CPU 使用率](../../media/GRE-Tunnel-Perf/Gre-Tunnel-01.jpg)

下图描述了 RAS 网关 Vm 上的以太网网络吞吐量。 Active VM、RAS 网关 VM #1 位于左侧，而被动 VM "RAS 网关 VM #2" 位于右侧。

![任务管理器中的网关 VM 以太网网络吞吐量](../../media/GRE-Tunnel-Perf/Gre-Tunnel-02.jpg)


### <a name="gre-tunnel-performance-with-one-tcp-connection"></a>一个 TCP 连接的 GRE 隧道性能

由于测试配置已从多个 TCP 会话更改为单个 TCP 会话，因此只有一个 CPU 内核达到 RAS 网关 Vm 上的最大容量。

GRE 隧道上的最大吞吐量介于 400-500 Mbits/s 之间。

下图描述了这两个 RAS 网关 Vm 上的 CPU 使用率。 Active VM、RAS 网关 VM #1 位于左侧，而被动 VM "RAS 网关 VM #2" 位于右侧。

![任务管理器中的网关 VM CPU 使用率](../../media/GRE-Tunnel-Perf/Gre-Tunnel-03.jpg)


下图描述了 RAS 网关 Vm 上的以太网网络吞吐量。 Active VM、RAS 网关 VM #1 位于左侧，而被动 VM "RAS 网关 VM #2" 位于右侧。

![任务管理器中的网关 VM 以太网网络吞吐量](../../media/GRE-Tunnel-Perf/Gre-Tunnel-04.jpg)

有关 RAS 网关性能的详细信息，请参阅[软件定义的网络中的 HNV 网关性能优化](https://docs.microsoft.com/windows-server/administration/performance-tuning/subsystem/software-defined-networking/hnv-gateway-performance)。