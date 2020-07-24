---
title: 驱动器的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 2f54f06462818ca21ae10acee40d788211b38e37
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86964519"
---
# <a name="performance-history-for-drives"></a>驱动器的性能历史记录

> 适用于：Windows Server 2019

本主题中的[性能历史记录存储空间直通](performance-history.md)详细说明了为驱动器收集的性能历史记录。 性能历史记录适用于群集存储子系统中的每个驱动器，而不考虑总线或媒体类型。 但是，它不适用于 OS 引导驱动器。

   > [!NOTE]
   > 无法为关闭的服务器中的驱动器收集性能历史记录。 服务器重新启动时，收集将自动恢复。

## <a name="series-names-and-units"></a>序列名称和单位

为每个符合条件的驱动器收集这些系列：

| 系列                          | 计价单位             |
|---------------------------------|------------------|
| `physicaldisk.iops.read`        | 每秒       |
| `physicaldisk.iops.write`       | 每秒       |
| `physicaldisk.iops.total`       | 每秒       |
| `physicaldisk.throughput.read`  | 每秒字节数 |
| `physicaldisk.throughput.write` | 每秒字节数 |
| `physicaldisk.throughput.total` | 每秒字节数 |
| `physicaldisk.latency.read`     | seconds          |
| `physicaldisk.latency.write`    | seconds          |
| `physicaldisk.latency.average`  | seconds          |
| `physicaldisk.size.total`       | 字节            |
| `physicaldisk.size.used`        | 字节            |

## <a name="how-to-interpret"></a>如何解释

| 系列                          | 如何解释                                                            |
|---------------------------------|-----------------------------------------------------------------------------|
| `physicaldisk.iops.read`        | 驱动器每秒完成的读取操作数。                |
| `physicaldisk.iops.write`       | 驱动器每秒完成的写入操作数。               |
| `physicaldisk.iops.total`       | 驱动器每秒完成的读取或写入操作总数。 |
| `physicaldisk.throughput.read`  | 每秒从驱动器读取的数据量。                            |
| `physicaldisk.throughput.write` | 每秒写入驱动器的数据量。                           |
| `physicaldisk.throughput.total` | 每秒从驱动器读取或向驱动器写入的总数据量。        |
| `physicaldisk.latency.read`     | 从驱动器读取操作的平均延迟。                          |
| `physicaldisk.latency.write`    | 写入操作对驱动器的平均延迟。                           |
| `physicaldisk.latency.average`  | 驱动器中所有操作的平均延迟。                     |
| `physicaldisk.size.total`       | 驱动器的总存储容量。                                    |
| `physicaldisk.size.used`        | 驱动器的已用存储容量。                                     |

## <a name="where-they-come-from"></a>它们来自何处

`iops.*`、 `throughput.*` 和 `latency.*` 系列是从 `Physical Disk` 连接驱动器的服务器上的性能计数器集中收集的，每个驱动器一个实例。 这些计数器由度量 `partmgr.sys` ，并不包含大部分 Windows 软件堆栈和任何网络跃点。 它们代表设备硬件性能。

| 系列                          | 源计数器           |
|---------------------------------|--------------------------|
| `physicaldisk.iops.read`        | `Disk Reads/sec`         |
| `physicaldisk.iops.write`       | `Disk Writes/sec`        |
| `physicaldisk.iops.total`       | `Disk Transfers/sec`     |
| `physicaldisk.throughput.read`  | `Disk Read Bytes/sec`    |
| `physicaldisk.throughput.write` | `Disk Write Bytes/sec`   |
| `physicaldisk.throughput.total` | `Disk Bytes/sec`         |
| `physicaldisk.latency.read`     | `Avg. Disk sec/Read`     |
| `physicaldisk.latency.write`    | `Avg. Disk sec/Writes`   |
| `physicaldisk.latency.average`  | `Avg. Disk sec/Transfer` |

   > [!NOTE]
   > 计数器在整个间隔内进行测量，而不是采样。 例如，如果驱动器空闲了9秒，但第10秒完成了30个 IOs，则在 `physicaldisk.iops.total` 此10秒的时间间隔内，其平均记录为每秒3个 ios。 这可确保其性能历史记录捕获所有活动，并使干扰稳定。

`size.*`序列是从 `MSFT_PhysicalDisk` WMI 中的类收集的，每个驱动器一个实例。

| 系列                          | Source 属性        |
|---------------------------------|------------------------|
| `physicaldisk.size.total`       | `Size`                 |
| `physicaldisk.size.used`        | `VirtualDiskFootprint` |

## <a name="usage-in-powershell"></a>PowerShell 中的用法

使用[PhysicalDisk](/powershell/module/storage/get-physicaldisk) cmdlet：

```PowerShell
Get-PhysicalDisk -SerialNumber <SerialNumber> | Get-ClusterPerf
```

## <a name="additional-references"></a>其他参考

- [存储空间直通的性能历史记录](performance-history.md)
