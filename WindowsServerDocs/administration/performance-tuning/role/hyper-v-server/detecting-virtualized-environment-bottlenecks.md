---
title: 检测虚拟化环境中的瓶颈
description: 如何检测和解决潜在的 Hyper-v 性能瓶颈
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: asmahi; sandysp; jopoulso
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 211f35c151e94bc8b8a11a614edad18053cb18b9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851772"
---
# <a name="detecting-bottlenecks-in-a-virtualized-environment"></a>检测虚拟化环境中的瓶颈

本部分应为您介绍如何使用性能监视器监视的有关内容的提示，以及如何确定当主机或某些虚拟机未按预期执行时问题可能出现的位置。

## <a name="processor-bottlenecks"></a>处理器瓶颈

下面是可能导致处理器瓶颈的一些常见情况：

-   加载一个或多个逻辑处理器

-   已加载一个或多个虚拟处理器

可以从主机使用以下性能计数器：

-   逻辑处理器利用率-\\Hyper-v 虚拟机监控程序逻辑处理器（\*）\\% 总运行时间

-   虚拟处理器利用率-\\Hyper-v 虚拟机监控程序虚拟处理器（\*）\\% 总运行时间

-   根虚拟处理器使用率-\\Hyper-v 虚拟机监控程序根虚拟处理器（\*）\\% 总运行时间

如果**Hyper-v 虚拟机监控程序逻辑处理器（总计）\\% Total Runtime counter\_** 超过90%，则会重载该主机。 应添加更多的处理能力，或者将一些虚拟机移到其他主机上。

如果**hyper-v 虚拟机监控程序虚拟处理器（VM 名称： VP x）\\% Total Runtime** counter 超过90%，则应执行以下操作：

-   验证主机是否未超载

-   了解工作负荷能否利用更多虚拟处理器

-   向虚拟机分配更多的虚拟处理器

如果**hyper-v 虚拟机监控程序虚拟处理器（VM 名称： VM 名称： x）\\% Total Runtime** counter 超过90%，则必须执行以下操作：

-   如果你的工作负荷接收到网络密集型，你应考虑使用 vRSS。

-   如果虚拟机未运行 Windows Server 2012 R2，你应添加更多网络适配器。

-   如果你的工作负荷占用大量存储空间，则应启用虚拟 NUMA 并添加更多虚拟磁盘。

如果**Hyper-v 虚拟机监控程序根虚拟处理器（根 VP x）\\% Total Runtime** counter 超过90%，但不是所有、虚拟处理器和**处理器（x）\\% 中断时间和处理器（x）\\% DPC time**计数器大约增加了到**根虚拟处理器（根 VP x）\\% Total Runtime**计数器的值，则应确保在网络适配器上启用 VMQ。

## <a name="memory-bottlenecks"></a>内存瓶颈

下面是可能导致内存瓶颈的一些常见情况：

-   主机未响应。

-   无法启动虚拟机。

-   虚拟机内存不足。

可以从主机使用以下性能计数器：

-   内存\\可用兆字节

-   Hyper-v 动态内存均衡器（\*）\\可用内存

你可以使用虚拟机中的以下性能计数器：

-   内存\\可用兆字节

如果**内存\\可用 mb**和**Hyper-v 动态内存均衡器（\*）\\** 主机上的可用内存计数器较低，则应停止非必要服务并将一个或多个虚拟机迁移到另一台主机。

如果虚拟机中的**内存\\可用兆字节**计数器不足，则应为虚拟机分配更多内存。 如果使用动态内存，则应增加 "最大内存" 设置。

## <a name="network-bottlenecks"></a>网络瓶颈

下面是可能导致网络瓶颈的一些常见情况：

-   主机是网络绑定的。

-   虚拟机为 "网络绑定"。

可以从主机使用以下性能计数器：

-   网络接口（*网络适配器名称*）\\字节数/秒

你可以使用虚拟机中的以下性能计数器：

-   Hyper-v 虚拟网络适配器（*虚拟机名称名称&lt;GUID&gt;* ）\\字节数/秒

如果**物理 NIC Bytes/sec**计数器大于或等于容量的90%，则应添加更多的网络适配器，将虚拟机迁移到另一台主机，并配置网络 QoS。

如果**Hyper-v 虚拟网络适配器 Bytes/sec**计数器大于或等于 250 MBps，则应在虚拟机中添加其他组合网络适配器，启用 vRSS，并使用 sr-iov。

如果你的工作负荷无法满足其网络延迟，请启用 SR-IOV 来向虚拟机提供物理网络适配器资源。

## <a name="storage-bottlenecks"></a>存储瓶颈

下面是可能导致存储瓶颈的一些常见情况：

-   主机和虚拟机操作缓慢或超时。

-   虚拟机速度缓慢。

可以从主机使用以下性能计数器：

-   物理磁盘（*磁盘号*）\\Avg. disk Sec/Read

-   物理磁盘（*磁盘号*）\\Avg. disk Sec/Write

-   物理磁盘（*磁盘号*）\\平均磁盘读取队列长度

-   物理磁盘（*磁盘号*）\\平均磁盘写入队列长度

如果延迟持续大于50ms，应执行以下操作：

-   跨附加存储传播虚拟机

-   考虑购买更快的存储

-   考虑在 Windows Server 2012 R2 中引入的分层存储空间

-   请考虑使用 Windows Server 2012 R2 中引入的存储 QoS

-   使用 VHDX

## <a name="see-also"></a>另请参阅

-   [Hyper-V 术语](terminology.md)

-   [Hyper-V 体系结构](architecture.md)

-   [Hyper-V 服务器配置](configuration.md)

-   [Hyper-V 处理器性能](processor-performance.md)

-   [Hyper-V 内存性能](memory-performance.md)

-   [Hyper-V 存储 I/O 性能](storage-io-performance.md)

-   [Hyper-V 网络 I/O 性能](network-io-performance.md)

-   [Linux 虚拟机](linux-virtual-machine-considerations.md)
