---
title: 卷的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/09/2018
ms.localizationpriority: medium
ms.openlocfilehash: 5f6acf062d2dba7c2a1a04d8a3f7cb4d7bd51a4d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856130"
---
# <a name="performance-history-for-volumes"></a>卷的性能历史记录

> 适用于： Windows Server 2019

本主题中的[性能历史记录存储空间直通](performance-history.md)详细说明了为卷收集的性能历史记录。 性能历史记录适用于群集中的每个群集共享卷（CSV）。 但是，它不适用于 OS 启动卷，也不适用于任何其他非 CSV 存储。

   > [!NOTE]
   > 收集可能需要几分钟时间才能开始新创建或重命名的卷。

## <a name="series-names-and-units"></a>序列名称和单位

为每个符合条件的卷收集这些系列：

| 序列                    | 单位             |
|---------------------------|------------------|
| `volume.iops.read`        | 每秒       |
| `volume.iops.write`       | 每秒       |
| `volume.iops.total`       | 每秒       |
| `volume.throughput.read`  | 每秒字节数 |
| `volume.throughput.write` | 每秒字节数 |
| `volume.throughput.total` | 每秒字节数 |
| `volume.latency.read`     | 秒          |
| `volume.latency.write`    | 秒          |
| `volume.latency.average`  | 秒          |
| `volume.size.total`       | 字节            |
| `volume.size.available`   | 字节            |

## <a name="how-to-interpret"></a>如何解释

| 序列                    | 如何解释                                                              |
|---------------------------|-------------------------------------------------------------------------------|
| `volume.iops.read`        | 此卷每秒完成的读取操作数。                |
| `volume.iops.write`       | 此卷每秒完成的写入操作数。               |
| `volume.iops.total`       | 此卷每秒完成的读取或写入操作的总数。 |
| `volume.throughput.read`  | 每秒从此卷读取的数据量。                            |
| `volume.throughput.write` | 每秒写入此卷的数据量。                           |
| `volume.throughput.total` | 每秒从该卷读取或写入的总数据量。        |
| `volume.latency.read`     | 从此卷读取操作的平均延迟。                          |
| `volume.latency.write`    | 对此卷进行写入操作的平均延迟。                           |
| `volume.latency.average`  | 此卷的所有操作的平均延迟。                     |
| `volume.size.total`       | 卷的总存储容量。                                     |
| `volume.size.available`   | 卷的可用存储容量。                                 |

## <a name="where-they-come-from"></a>它们来自何处

`iops.*`、`throughput.*`和 `latency.*` 序列是从 `Cluster CSVFS` 性能计数器集中收集的。 群集中的每个服务器都具有每个 CSV 卷的实例，而不考虑所有权。 为卷 `MyVolume` 记录的性能历史记录是群集中每个服务器上的 `MyVolume` 实例的聚合。

| 序列                    | 源计数器         |
|---------------------------|------------------------|
| `volume.iops.read`        | `Reads/sec`            |
| `volume.iops.write`       | `Writes/sec`           |
| `volume.iops.total`       | *以上的总和*     |
| `volume.throughput.read`  | `Read bytes/sec`       |
| `volume.throughput.write` | `Write bytes/sec`      |
| `volume.throughput.total` | *以上的总和*     |
| `volume.latency.read`     | `Avg. sec/Read`        |
| `volume.latency.write`    | `Avg. sec/Write`       |
| `volume.latency.average`  | *上述平均值* |

   > [!NOTE]
   > 计数器在整个间隔内进行测量，而不是采样。 例如，如果卷的空闲时间为9秒，但在第10秒内完成 30 Io，则在此10秒的时间间隔内，其 `volume.iops.total` 将平均记录为每秒3个 IOs。 这可确保其性能历史记录捕获所有活动，并使干扰稳定。

   > [!TIP]
   > 这些是常用[VM 汽油](https://github.com/Microsoft/diskspd/blob/master/Frameworks/VMFleet/watch-cluster.ps1)基准框架使用的相同计数器。

`size.*` 系列是从 WMI 中的 `MSFT_Volume` 类收集的，每个卷有一个实例。

| 序列                    | Source 属性 |
|---------------------------|-----------------|
| `volume.size.total`       | `Size`          |
| `volume.size.available`   | `SizeRemaining` |

## <a name="usage-in-powershell"></a>在 PowerShell 中的用法

使用[获取量](https://docs.microsoft.com/powershell/module/storage/get-volume)cmdlet：

```PowerShell
Get-Volume -FriendlyName <FriendlyName> | Get-ClusterPerf
```

## <a name="see-also"></a>另请参阅

- [存储空间直通的性能历史记录](performance-history.md)
