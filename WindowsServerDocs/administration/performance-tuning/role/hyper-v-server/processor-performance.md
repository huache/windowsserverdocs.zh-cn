---
title: Hyper-v 处理器性能
description: Hyper-v 性能优化中的处理器性能注意事项
ms.topic: article
ms.author: asmahi
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 4691f71b98cbbe0993a6e837f5d13b4b5c5a21b6
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078225"
---
# <a name="hyper-v-processor-performance"></a>Hyper-v 处理器性能


## <a name="virtual-machine-integration-services"></a>虚拟机 integration services

虚拟机 Integration Services 包括特定于 Hyper-v 的 i/o 设备的启用驱动程序，这大大减少了 i/o 相比模拟设备的 CPU 开销。 你应在每个受支持的虚拟机中安装最新版本的虚拟机 Integration Services。 服务会降低来宾的 CPU 使用情况，从空闲来宾到过度使用的来宾，并提高 i/o 吞吐量。 这是在运行 Hyper-v 的服务器中优化性能的第一步。 有关支持的来宾操作系统的列表，请参阅 [Hyper-v 概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))。

## <a name="virtual-processors"></a>虚拟处理器

Windows Server 2016 中的 hyper-v 支持每个虚拟机最多支持240个虚拟处理器。 如果虚拟机的负载不会消耗大量 CPU，则应该将其配置为使用一个虚拟处理器。 这是因为与多个虚拟处理器关联的额外开销，例如来宾操作系统中的额外同步成本。

如果虚拟机在高峰负载下需要多个 CPU 处理，则增加虚拟处理器的数量。

## <a name="background-activity"></a>后台活动

最大程度地降低空闲虚拟机中的后台活动会释放可在其他虚拟机其他地方使用的 CPU 周期。 当 Windows 来宾处于空闲状态时，通常会使用不到1% 的 CPU。 下面是将虚拟机的后台 CPU 使用降至最低的几个最佳做法：

-   安装最新版本的虚拟机 Integration Services。

-   通过 "虚拟机设置" 对话框删除仿真网络适配器 (使用 Microsoft Hyper-V 特定的适配器) 。

-   删除未使用的设备，如 CD-ROM 和 COM 端口，或断开其媒体的连接。

-   如果未使用 Windows 来宾操作系统，请将其保存在登录屏幕上，并禁用屏幕保护程序。

-   查看默认情况下启用的计划任务和服务。

-   通过运行**logman.exe ets** ，查看默认情况下启用的 ETW 跟踪提供程序

-   改善服务器应用程序以减少定期活动 (如计时器) 。

-   关闭主机和来宾操作系统上的服务器管理器。

-   请勿让 Hyper-v 管理器运行，因为它会持续刷新虚拟机的缩略图。

下面是在虚拟机中配置 Windows 的 *客户端版本* 以降低总体 CPU 使用率的其他最佳方案：

-   禁用诸如 SuperFetch 和 Windows Search 等后台服务。

-   禁用计划的任务，例如定期碎片整理。

## <a name="virtual-numa"></a>虚拟 NUMA

为了能够虚拟化较大的扩展工作负载，Windows Server 2016 中的 Hyper-v 扩展了虚拟机规模限制。 可以为单个虚拟机分配最多240个虚拟处理器和 12 TB 内存。 创建如此大的虚拟机时，可能会使用主机系统上多个 NUMA 节点中的内存。 在此类虚拟机配置中，如果虚拟处理器和内存未从同一 NUMA 节点分配，则工作负荷可能会因为无法利用 NUMA 优化而导致性能不佳。

在 Windows Server 2016 中，Hyper-v 将向虚拟机提供虚拟 NUMA 拓扑。 在默认情况下，将优化此虚拟 NUMA 拓扑以匹配基础主计算机的 NUMA 拓扑。 通过在虚拟机中公开虚拟 NUMA 拓扑，可允许来宾操作系统以及在其中运行的任何 NUMA 感知应用程序利用 NUMA 性能优化，就像在物理计算机上运行时的行为一样。

从工作负载的角度来看，虚拟和物理 NUMA 之间没有区别。 在虚拟机中，当工作负载为数据分配本地内存并在同一个 NUMA 节点中访问该数据时，将在基础物理系统上快速访问本地内存结果。 可成功避免由于远程内存访问而引起的性能损失。 只有 NUMA 感知应用程序才能受益于 vNUMA。

Microsoft SQL Server 是 NUMA 感知应用程序的一个示例。 有关详细信息，请参阅 [了解非一致性内存访问](/previous-versions/sql/sql-server-2008-r2/ms178144(v=sql.105))。

无法同时使用虚拟 NUMA 和动态内存功能。 有效启用了动态内存的虚拟机只有一个虚拟 NUMA 节点，并且不会向虚拟机提供任何 NUMA 拓扑，无论虚拟 NUMA 设置如何。

有关虚拟 NUMA 的详细信息，请参阅 [Hyper-v 虚拟 Numa 概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282282(v=ws.11))。

## <a name="additional-references"></a>其他参考

-   [Hyper-V 术语](terminology.md)

-   [Hyper-V 体系结构](architecture.md)

-   [Hyper-V 服务器配置](configuration.md)

-   [Hyper-V 内存性能](memory-performance.md)

-   [Hyper-V 存储 I/O 性能](storage-io-performance.md)

-   [Hyper-V 网络 I/O 性能](network-io-performance.md)

-   [检测虚拟化环境中的瓶颈](detecting-virtualized-environment-bottlenecks.md)

-   [Linux 虚拟机](linux-virtual-machine-considerations.md)