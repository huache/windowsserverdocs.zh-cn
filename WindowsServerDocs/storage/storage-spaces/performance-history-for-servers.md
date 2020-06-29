---
title: 服务器的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7ed910aba376ba7f78c628d7f47bdd21b366459d
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474734"
---
# <a name="performance-history-for-servers"></a>服务器的性能历史记录

> 适用于：Windows Server 2019

本主题中的[存储空间直通性能历史记录](performance-history.md)详细说明了为服务器收集的性能历史记录。 性能历史记录适用于群集中的每个服务器。

   > [!NOTE]
   > 无法为关闭的服务器收集性能历史记录。 服务器重新启动时，收集将自动恢复。

## <a name="series-names-and-units"></a>序列名称和单位

为每个符合条件的服务器收集这些系列：

| 系列                           | 计价单位    |
|----------------------------------|---------|
| `clusternode.cpu.usage`          | % |
| `clusternode.cpu.usage.guest`    | % |
| `clusternode.cpu.usage.host`     | % |
| `clusternode.memory.total`       | 字节   |
| `clusternode.memory.available`   | 字节   |
| `clusternode.memory.usage`       | 字节   |
| `clusternode.memory.usage.guest` | 字节   |
| `clusternode.memory.usage.host`  | 字节   |

此外，对于附加到服务器的 `physicaldisk.size.total` 所有符合条件的驱动器，将对驱动器系列（例如）进行聚合，并为 `networkadapter.bytes.total` 连接到服务器的所有符合条件的网络适配器聚合网络适配器系列（例如）。

## <a name="how-to-interpret"></a>如何解释

| 系列                           | 如何解释                                                      |
|----------------------------------|-----------------------------------------------------------------------|
| `clusternode.cpu.usage`          | 处于非空闲状态的处理器时间百分比。                        |
| `clusternode.cpu.usage.guest`    | 用于来宾（虚拟机）需求的处理器时间百分比。 |
| `clusternode.cpu.usage.host`     | 用于主机需求的处理器时间百分比。                    |
| `clusternode.memory.total`       | 服务器的总物理内存。                              |
| `clusternode.memory.available`   | 服务器的可用内存。                                   |
| `clusternode.memory.usage`       | 服务器的已分配（不可用）内存。                   |
| `clusternode.memory.usage.guest` | 分配给来宾（虚拟机）需求的内存。               |
| `clusternode.memory.usage.host`  | 分配给主机需求的内存。                                  |

## <a name="where-they-come-from"></a>它们来自何处

根据 `cpu.*` 是否已启用 hyper-v，从不同的性能计数器收集序列。

如果启用了 Hyper-v：

| 系列                           | 源计数器 |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Hyper-V Hypervisor Logical Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.guest`    | `Hyper-V Hypervisor Virtual Processor` > `_Total` > `% Total Run Time`      |
| `clusternode.cpu.usage.host`     | `Hyper-V Hypervisor Root Virtual Processor` > `_Total` > `% Total Run Time` |

使用 `% Total Run Time` 计数器可确保性能历史记录所有使用情况。

如果未启用 Hyper-v：

| 系列                           | 源计数器 |
|----------------------------------|----------------|
| `clusternode.cpu.usage`          | `Processor` > `_Total` > `% Processor Time` |
| `clusternode.cpu.usage.guest`    | *无* |
| `clusternode.cpu.usage.host`     | *与总使用量相同* |

尽管完善同步， `clusternode.cpu.usage` 但始终 `clusternode.cpu.usage.host` 为 `clusternode.cpu.usage.guest` 。

同样要注意的 `clusternode.cpu.usage.guest` 是，始终是 `vm.cpu.usage` 主机服务器上所有虚拟机的总和。

`memory.*`序列为（即将推出）。

  > [!NOTE]
  > 计数器在整个间隔内进行测量，而不是采样。 例如，如果服务器的空闲时间为9秒，但10秒内高峰为100%，则在 `clusternode.cpu.usage` 10 秒的时间间隔内，其平均记录为10%。 这可确保其性能历史记录捕获所有活动，并使干扰稳定。

## <a name="usage-in-powershell"></a>PowerShell 中的用法

使用[start-clusternode](https://docs.microsoft.com/powershell/module/failoverclusters/get-clusternode) cmdlet：

```PowerShell
Get-ClusterNode <Name> | Get-ClusterPerf
```

## <a name="additional-references"></a>其他参考

- [存储空间直通的性能历史记录](performance-history.md)
