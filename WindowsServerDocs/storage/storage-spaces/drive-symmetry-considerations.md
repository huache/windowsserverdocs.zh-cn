---
title: 存储空间直通的驱动对称注意事项
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 10/08/2018
ms.localizationpriority: medium
ms.openlocfilehash: b06d69c020ea38a2fb9f23df2cfd9cd4191ae315
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857550"
---
# <a name="drive-symmetry-considerations-for-storage-spaces-direct"></a>存储空间直通的驱动对称注意事项 

> 适用于： Windows Server 2019、Windows Server 2016

如果每个服务器都具有完全相同的驱动器，则[存储空间直通](storage-spaces-direct-overview.md)的效果最佳。

事实上，我们认识到这并不总是可行：存储空间直通设计为多年来运行，并随着组织需求的增长而扩展。 现在，你可以购买 spacious 3 TB 硬盘驱动器;明年，找不到小型的。 因此，支持一定数量的混合和匹配。

本主题介绍了这些限制，并提供了支持和不支持的配置的示例。

## <a name="constraints"></a>约束

### <a name="type"></a>类型

所有服务器都应具有相同[的驱动器类型](choosing-drives.md#drive-types)。

例如，如果一台服务器有 NVMe，则它们*都应有 nvme* 。

### <a name="number"></a>编号

所有服务器都应具有相同数量的每个类型的驱动器。

例如，如果一台服务器有六个 SSD，则它们*都应有六*个 ssd。

   > [!NOTE]
   > 在出现故障时或者在添加或删除驱动器时，驱动器数量会暂时不同。

### <a name="model"></a>模型

建议尽可能使用相同型号和固件版本的驱动器。 如果无法做到这一点，请仔细选择尽可能相似的驱动器。 我们防止混合和匹配的驱动器具有急剧不同的性能或耐用性特征（除非它是缓存，另一种是容量），因为存储空间直通平均分配 IO，而不会基于模型进行区分。

   > [!NOTE]
   > 可以混合搭配搭配使用类似的 SATA 和 SAS 驱动器。

### <a name="size"></a>大小

建议尽可能使用大小相同的驱动器。 使用不同大小的容量驱动器可能会导致某些容量不可用，使用不同大小的缓存驱动器可能不会提高缓存性能。 有关详细信息，请参阅下一节。

   > [!WARNING]
   > 不同服务器上的容量驱动器大小可能会导致闲置的容量。

## <a name="understand-capacity-imbalance"></a>了解：容量不平衡

对于跨服务器和跨服务器的容量不平衡，存储空间直通是可靠的。 即使不平衡很严重，所有内容仍将继续工作。 但是，根据多个因素，每个服务器中不可用的容量可能不可用。

若要查看发生此问题的原因，请考虑下面的简化图。 每个彩色框表示一个镜像数据副本。 例如，标记为、"" 和 "" 的框是相同数据的三个副本。 为了服从服务器容错，这些副本*必须*存储在不同的服务器中。

### <a name="stranded-capacity"></a>闲置容量

正如绘图，服务器1（10 TB）和服务器2（10 TB）已满。 服务器3具有更大的驱动器，因此它的总容量大于（15 TB）。 但是，若要在服务器3上存储更多的三向镜像数据，则还需要服务器1和服务器2上的副本（已满）。 不能使用服务器3上剩余的 5 TB 容量–它是 *"闲置的"* 容量。

![三向镜像，三台服务器，闲置容量](media/drive-symmetry-considerations/Size-Asymmetry-3N-Stranded.png)

### <a name="optimal-placement"></a>最佳放置

相反，对于4个 10 TB 的服务器、10 tb、10 TB 以及 15 TB 的容量和三向镜像复原 *，可以使用*所绘制的所有可用容量来有效地放置副本。 只要有可能，存储空间直通分配器将查找并使用最佳位置，而不会留下闲置的容量。

![三向镜像，四个服务器，无闲置容量](media/drive-symmetry-considerations/Size-Asymmetry-4N-No-Stranded.png)

服务器的数量、复原能力、容量不平衡的严重性以及其他因素将影响是否存在闲置的容量。 **最明智的一般规则是假设只有每个服务器中的可用容量保证可用。**

## <a name="understand-cache-imbalance"></a>了解：缓存不平衡

存储空间直通可以可靠地跨驱动器和跨服务器缓存不平衡。 即使不平衡很严重，所有内容仍将继续工作。 而且，存储空间直通始终使用所有可用缓存。

但是，使用不同大小的缓存驱动器可能不会以统一或可预测的方式提高缓存性能：只有 IO 才能驱动使用较大缓存驱动器的[绑定](understand-the-cache.md#server-side-architecture)，这可能会提高性能。 存储空间直通跨绑定平均分配 IO，并且不会根据缓存到容量的比率进行区分。

![缓存不平衡](media/drive-symmetry-considerations/Cache-Asymmetry.png)

   > [!TIP]
   > 请参阅[了解缓存](understand-the-cache.md)了解有关缓存绑定的详细信息。

## <a name="example-configurations"></a>示例配置

下面是一些受支持和不支持的配置：

### <a name="supported-supported-different-models-between-servers"></a>![受支持](media/drive-symmetry-considerations/supported.png) 支持：服务器之间的不同模型

前两台服务器使用 NVMe 模型 "X"，但第三个服务器使用 NVMe 模型 "Z"，这一点非常类似。

| 服务器 1                    | 服务器2                    | 服务器3                    |
|-----------------------------|-----------------------------|-----------------------------|
| 2 x NVMe 型号 X （缓存）    | 2 x NVMe 型号 X （缓存）    | 2 x NVMe 模型 Z （缓存）    |
| 10 x SSD 型号 Y （容量） | 10 x SSD 型号 Y （容量） | 10 x SSD 型号 Y （容量） |

这是受支持的。

### <a name="supported-supported-different-models-within-server"></a>![受支持](media/drive-symmetry-considerations/supported.png) 支持的：服务器中的不同模型

每台服务器都使用某种不同的 HDD 型号 "Y" 和 "Z"，这种模式非常相似。 每台服务器都有10个硬盘。

| 服务器 1                   | 服务器2                   | 服务器3                   |
|----------------------------|----------------------------|----------------------------|
| 2 x SSD 模型 X （缓存）    | 2 x SSD 模型 X （缓存）    | 2 x SSD 模型 X （缓存）    |
| 7 x HDD 型号 Y （容量） | 5 x HDD 型号 Y （容量） | 1 x HDD 型号 Y （容量） |
| 3 x HDD 型号 Z （容量） | 5 x HDD 型号 Z （容量） | 9 x HDD 型号 Z （容量） |

这是受支持的。

### <a name="supported-supported-different-sizes-across-servers"></a>![受支持](media/drive-symmetry-considerations/supported.png) 支持：跨服务器大小不同

前两台服务器使用 4 TB HDD，但第三个服务器使用非常相似的 6 TB HDD。

| 服务器 1                | 服务器2                | 服务器3                |
|-------------------------|-------------------------|-------------------------|
| 2 x 800 GB NVMe （缓存） | 2 x 800 GB NVMe （缓存） | 2 x 800 GB NVMe （缓存） |
| 4 x 4 TB HDD （容量） | 4 x 4 TB HDD （容量） | 4 x 6 TB HDD （容量） |

这是受支持的，但这会导致闲置的容量。

### <a name="supported-supported-different-sizes-within-server"></a>![受支持](media/drive-symmetry-considerations/supported.png) 支持：服务器内的大小不同

每台服务器使用 1.2 TB 和非常类似的 1.6 TB SSD 的混合。 每个服务器都有4个 SSD。

| 服务器 1                 | 服务器2                 | 服务器3                 |
|--------------------------|--------------------------|--------------------------|
| 3 x 1.2 TB SSD （缓存）   | 2 x 1.2 TB SSD （缓存）   | 4 x 1.2 TB SSD （缓存）   |
| 1 x 1.6 TB SSD （缓存）   | 2 x 1.6 TB SSD （缓存）   | -                        |
| 20 x 4 TB HDD （容量） | 20 x 4 TB HDD （容量） | 20 x 4 TB HDD （容量） |

这是受支持的。

### <a name="unsupported-not-supported-different-types-of-drives-across-servers"></a>![不支持](media/drive-symmetry-considerations/unsupported.png) 不受支持：跨服务器的不同类型的驱动器

服务器1具有 NVMe，但其他服务器不存在。

| 服务器 1            | 服务器2            | 服务器3            |
|---------------------|---------------------|---------------------|
| 6 x NVMe （缓存）    | -                   | -                   |
| -                   | 6 x SSD （缓存）     | 6 x SSD （缓存）     |
| 18 x HDD （容量） | 18 x HDD （容量） | 18 x HDD （容量） |

这不受支持。 每个服务器中的驱动器类型应相同。

### <a name="unsupported-not-supported-different-number-of-each-type-across-servers"></a>![不支持](media/drive-symmetry-considerations/unsupported.png) 不受支持：跨服务器的每种类型的数量不同

服务器3具有比其他驱动器更多的驱动器。

| 服务器 1            | 服务器2            | 服务器3            |
|---------------------|---------------------|---------------------|
| 2 x NVMe （缓存）    | 2 x NVMe （缓存）    | 4 x NVMe （缓存）    |
| 10 x HDD （容量） | 10 x HDD （容量） | 20 x HDD （容量） |

这不受支持。 每个服务器中的每个类型的驱动器数目应相同。

### <a name="unsupported-not-supported-only-hdd-drives"></a>![不支持](media/drive-symmetry-considerations/unsupported.png) 不支持：仅 HDD 驱动器

所有服务器仅连接了 HDD 驱动器。

|服务器 1|服务器2|服务器3|
|-|-|-| 
|18 x HDD （容量） |18 x HDD （容量）|18 x HDD （容量）|

这不受支持。 需要添加至少两个连接到每台服务器的缓存驱动器（NvME 或 SSD）。

## <a name="summary"></a>摘要

概括而言，群集中的每个服务器都应具有相同类型的驱动器和每种类型的相同编号。 支持根据需要混合搭配驱动器模型和驱动器大小，并提供上述注意事项。

| 约束                               |               |
|------------------------------------------|---------------|
| 每个服务器中的相同类型的驱动器     | **必填**  |
| 每个服务器中的每个类型都具有相同的数目 | **必填**  |
| 每个服务器中的相同驱动器型号        | 推荐   |
| 每个服务器中的相同驱动器大小         | 推荐   |

## <a name="see-also"></a>另请参阅

- [存储空间直通硬件要求](storage-spaces-direct-hardware-requirements.md)
- [存储空间直通概述](storage-spaces-direct-overview.md)
