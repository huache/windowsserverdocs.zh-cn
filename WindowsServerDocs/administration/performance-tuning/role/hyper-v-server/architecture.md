---
title: Hyper-V 体系结构
description: 用于性能优化的 hyper-v 体系结构 condsiderations
ms.topic: article
ms.author: asmahi; sandysp; jopoulso
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 62b7d0a235285e0e85d38860f629dfe046eee0c6
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87896165"
---
# <a name="hyper-v-architecture"></a>Hyper-V 体系结构

Hyper-v 的功能是基于类型1的虚拟机监控程序体系结构。 虚拟机监控程序虚拟化处理器和内存，并为根分区中的虚拟化堆栈提供了一些机制，用于管理 (虚拟机) 的子分区，并向虚拟机公开 i/o 设备等服务。

根分区拥有并可以直接访问物理 i/o 设备。 根分区中的虚拟化堆栈为虚拟机、管理 Api 和虚拟化 i/o 设备提供了内存管理器。 它还实现了模拟设备，例如集成设备电子设备 (IDE) 磁盘控制器和 PS/2 输入设备端口，并支持 Hyper-v 特定的合成设备，以提高性能并降低开销。

![基于 hyper-v 虚拟机监控程序的体系结构](../../media/perftune-guide-hyperv-arch.png)

Hyper-v 特定 i/o 体系结构由根分区中的虚拟化服务提供程序和虚拟化服务客户端中的 (.Vsps) 组成，子分区 (Vsc) 。 每个服务都是通过 VMBus 作为设备公开的，它充当 i/o 总线，并在使用诸如共享内存等机制的虚拟机之间实现高性能的通信。 来宾操作系统的即插即用管理器枚举这些设备，包括 VMBus，并将适当的设备驱动程序加载 (虚拟服务客户端) 。 除 i/o 以外的服务还通过此体系结构公开。

从 Windows Server 2008 开始，操作系统功能自旋在虚拟机中运行时优化其行为。 优点包括降低内存虚拟化的成本、提高多核的可伸缩性并降低来宾操作系统的后台 CPU 使用率。

以下各部分提供了在运行 Hyper-v 角色的服务器上提高性能的最佳做法。

## <a name="additional-references"></a>其他参考

-   [Hyper-V 术语](terminology.md)

-   [Hyper-V 服务器配置](configuration.md)

-   [Hyper-V 处理器性能](processor-performance.md)

-   [Hyper-V 内存性能](memory-performance.md)

-   [Hyper-V 存储 I/O 性能](storage-io-performance.md)

-   [Hyper-V 网络 I/O 性能](network-io-performance.md)

-   [检测虚拟化环境中的瓶颈](detecting-virtualized-environment-bottlenecks.md)

-   [Linux 虚拟机](linux-virtual-machine-considerations.md)
