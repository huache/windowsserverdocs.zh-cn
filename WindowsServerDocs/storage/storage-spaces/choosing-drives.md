---
ms.assetid: 1368bc83-9121-477a-af09-4ae73ac16789
title: 选择存储空间直通驱动器
ms.author: cosdar
manager: eldenc
ms.topic: article
author: cosmosdarwin
ms.date: 07/01/2020
ms.localizationpriority: medium
ms.openlocfilehash: e01966d268968a5bdec3d704d32bcc84b2638b27
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87961030"
---
# <a name="choosing-drives-for-storage-spaces-direct"></a>选择存储空间直通驱动器

>适用于：Windows Server 2019、Windows Server 2016

本主题提供有关如何选择[存储空间直通](storage-spaces-direct-overview.md)驱动器以满足你的性能和容量要求的指南。

## <a name="drive-types"></a>驱动器类型

存储空间直通目前适用于四种类型的驱动器：

<table>
    <tr style="border: 0;">
        <td style="padding: 10px; border: 0; width:70px">
            <img src="media/understand-the-cache/pmem-100px.png" alt="Image of PMem (persistent memory)">
        </td>
        <td style="padding: 10px; border: 0;" valign="middle">PMem 是指永久性内存，一种新的低延迟、高性能存储类型。
        </td>
    </tr>
    <tr style="border: 0;">
        <td style="padding: 10px; border: 0; width:70px">
            <img src="media/understand-the-cache/NVMe-100px.png" alt="Image of NVMe (Non-Volatile Memory Express)">
        </td>
        <td style="padding: 10px; border: 0;" valign="middle">
            <b>NVMe</b>（非易失性快速内存）是指直接位于 PCIe 总线上的固态硬盘。 常见外形规格为 2.5 英寸 U.2、PCIe 附加卡 (AIC) 和 M.2。 NVMe 提供更高的 IOPS 和 IO 吞吐量，延迟时间比我们目前支持的任何其他类型的驱动器（持久性内存除外）的延迟更高。
        </td>
    </tr>
    <tr style="border: 0;">
        <td style="padding: 10px; border: 0; width:70px" >
            <img src="media/understand-the-cache/SSD-100px.png" alt="Image of SSD drive">
        </td>
        <td style="padding: 10px; border: 0;" valign="middle">
            <b>SSD</b>是指通过传统 SATA 或 SAS 连接的固态硬盘。
        </td>
    </tr>
    <tr style="border: 0;">
        <td style="padding: 10px; border: 0; width:70px">
            <img src="media/understand-the-cache/HDD-100px.png" alt="Image of HDD">
        </td>
        <td style="padding: 10px; border: 0;" valign="middle">
            <b>HDD</b>指的是提供巨大存储容量的旋转磁盘驱动器。
        </td>
    </tr>
</table>

## <a name="built-in-cache"></a>内置缓存

存储空间直通提供内置的服务器端缓存。 此缓存是一个大型的持久性实时读取和写入缓存。 在包含多种类型的驱动器的部署中，该缓存自动配置为使用“最快”类型的所有驱动器。 剩余的驱动器用于提供容量。

有关详细信息，请查看[了解存储空间直通中的缓存](understand-the-cache.md)。

## <a name="option-1--maximizing-performance"></a>选项 1 - 最大化性能

若要实现对任何数据的随机读取和写入的可预测且统一的亚毫秒级延迟，或者要实现极高的 IOPS（我们已实现了[超过六百万](https://www.youtube.com/watch?v=0LviCzsudGY&t=28m)！）或 IO 吞吐量（我们已实现了[超过 1 Tb/s](https://www.youtube.com/watch?v=-LK2ViRGbWs&t=16m50s)！），那么你应该选择“全闪存”。

目前有三种方法可以实现此目的：

![All-Flash-Deployment-Possibilities](media/choosing-drives-and-resiliency-types/All-Flash-Deployment-Possibilities.png)

1. **全使用 NVMe。** 全部使用 NVMe 可以提供无与伦比的性能，包括最容易预测的低延迟。 如果所有驱动器的型号相同，则不会配置缓存。 也可以混用高持久性和低持久性的 NVMe 型号，并将前者配置为针对后者中的写入内容提供缓存（[需要进行设置](understand-the-cache.md#manual-configuration)）。

2. **NVMe + SSD。** 将 NVMe 与 SSD 配合使用时，NVMe 将自动为 SSD 中的写入内容提供缓存。 这样，就可以在缓存中合并写入内容，并仅在需要时才解除暂存写入内容，以减轻 SSD 的磨损。 这种方式提供类似于 NVMe 的写入特征，而读取内容将直接从同样快速的 SSD 提供。

3. **全使用 SSD。** 与全使用 NVMe 一样，如果所有驱动器的型号相同，则不会配置缓存。 如果混用高持久性和低持久性的型号，可将前者配置为针对后者中的写入内容提供缓存（[需要进行设置](understand-the-cache.md#manual-configuration)）。

   >[!NOTE]
   > 全使用 NVMe 或全使用 SSD 且不配置缓存的优势是，可以从每个驱动器获取可用的存储容量。 不会有任何容量“耗费”在缓存上，如果部署规模较小，这可能颇具吸引力。

## <a name="option-2--balancing-performance-and-capacity"></a>选项 2 - 平衡性能和容量

在包含各种应用程序和工作负荷的环境中，有些环境会提出严格的性能要求，而有些环境则要求提供相当大的存储容量，在这种情况下，应“混合”使用 NVMe 或 SSD 来为较大的 HDD 提供缓存。

![Hybrid-Deployment-Possibilities](media/choosing-drives-and-resiliency-types/Hybrid-Deployment-Possibilities.png)

1. **NVMe + HDD**。 NVMe 驱动器通过缓存来加速读取和写入操作。 缓存读取可让 HDD 专注于写入。 缓存写入可以消减 IO 突发，使写入内容可以合并，并仅在需要时才将其解除暂存，这种人为的序列化方式可将 HDD IOPS 和 IO 吞吐量最大化。 此方式提供类似于 NVMe 的写入特征，而对于频繁读取或最近读取的数据，它还提供类似于 NVMe 的读取特征。

2. **SSD + HDD**。 与前面类似，SSD 将通过缓存读取和写入内容来加速这两种操作。 此方式提供类似于 SSD 的写入特征，并针对频繁读取或最近读取的数据提供类似于 SSD 的读取特征。

    还有一个额外的特殊选项：使用上述所有三种类型的驱动器。

3. **NVMe + SSD + HDD。** 使用所有三种类型的驱动器时，NVMe 将同时为 SSD 和 HDD 提供缓存。 此选项的吸引力在于，可以在同一群集中的 SSD 和 HDD 上创建并列的卷，而这些卷全部可以通过 NVMe 来加速。 前者完全如同前面所述的“全闪存”部署，后者完全如同“混合”部署。 这在概念上类似于有两个池，并且容量管理、故障和修复周期等等基本上都是独立的。

   >[!IMPORTANT]
   > 建议使用 SSD 层，以将对性能最敏感的工作负荷放在全闪存驱动器上。

## <a name="option-3--maximizing-capacity"></a>选项 3 - 最大化容量

对于不经常需要大量容量和写入的工作负载，例如存档、备份目标、数据仓库或“冷”存储，你应该将用于缓存的少量 SSD 与用于容量的许多较大的 HDD 结合在一起。

![最大化容量的部署选项](media/choosing-drives-and-resiliency-types/maximizing-capacity.png)

1. **SSD + HDD**。 SSD 将缓存读取和写入内容以消减 IO 突发，并提供类似于 SSD 的写入性能，以后还可以通过优化的方式将这些内容解除暂存到 HDD。

>[!IMPORTANT]
>仅包含 HDD 的配置不受支持。 不建议使用高持久性的 SSD 来为低持久性的 SSD 提供缓存。

## <a name="sizing-considerations"></a>大小调整注意事项

### <a name="cache"></a>缓存

每台服务器必须至少有两个缓存驱动器（实现冗余的最低要求）。 容量驱动器的数目最好是缓存驱动器数目的倍数。 例如，如果你有 4 个缓存驱动器，则配置 8 个容量驱动器（1:2 比例）的性能比配置 7 个或 9 个容量驱动器更稳定。

应该调整缓存的大小，以适应应用程序和工作负荷的工作集，即，在任何给定时间，它们正在主动读取和写入的所有数据。 除此之外，没有其他缓存大小要求。 对于使用 Hdd 的部署，一个合理的起点是容量的10% –例如，如果每个服务器具有 4 x 4 TB HDD = 16 TB 的容量，则 2 x 800 GB SSD = 1.6 TB 的缓存每个服务器。 对于所有闪存部署，尤其是对于非常[高](https://techcommunity.microsoft.com/t5/storage-at-microsoft/understanding-ssd-endurance-drive-writes-per-day-dwpd-terabytes/ba-p/426024)的 ssd，尤其是在容量非常高的情况下（例如，如果每台服务器具有 24 x 1.2 TB SSD = 28.8 TB 的容量），则 2 x 750 GB NVMe = 每个服务器的缓存 1.5 tb。 以后随时可以通过添加或移除缓存驱动器进行调整。

### <a name="general"></a>常规

建议将每台服务器的总存储容量限制为大约 400 TB。 每台服务器的存储容量越高，则停机或重新启动后（例如应用软件更新时），重新同步数据所需的时间就越长。 对于 Windows Server 2019，每个存储池的当前最大大小为 4 pb (PB)  (4000 TB) ，对于 windows Server 2016 为 1 pb。

## <a name="additional-references"></a>其他参考

- [存储空间直通概述](storage-spaces-direct-overview.md)
- [了解存储空间直通中的缓存](understand-the-cache.md)
- [存储空间直通硬件要求](storage-spaces-direct-hardware-requirements.md)
- [在存储空间直通中规划卷](plan-volumes.md)
- [容错和存储效率](storage-spaces-fault-tolerance.md)
