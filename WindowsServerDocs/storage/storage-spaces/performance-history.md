---
title: 存储空间直通的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 09/07/2018
ms.localizationpriority: medium
ms.openlocfilehash: ab9b6016d49725b7f25d2ad3c40bd6265ac811a9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856150"
---
# <a name="performance-history-for-storage-spaces-direct"></a>存储空间直通的性能历史记录

> 适用于： Windows Server 2019

性能历史记录是一项新功能，可让[存储空间直通](storage-spaces-direct-overview.md)管理员通过主机服务器、驱动器、卷、虚拟机等轻松访问历史计算、内存、网络和存储度量。 性能历史记录将自动收集并存储在群集上，最多可达一年。

   > [!IMPORTANT]
   > 此功能是 Windows Server 2019 中的新增功能。 它在 Windows Server 2016 中不可用。

## <a name="get-started"></a>入门

默认情况下，在 Windows Server 2019 中存储空间直通收集性能历史记录。 无需安装、配置或启动任何内容。 不需要建立 Internet 连接，系统中心不是必需的，不需要外部数据库。

若要以图形方式查看群集的性能历史记录，请使用[Windows 管理中心](../../manage/windows-admin-center/understand/windows-admin-center.md)：

![Windows 管理中心中的性能历史记录](media/performance-history/perf-history-in-wac.png)

若要以编程方式查询和处理它，请使用 new `Get-ClusterPerf` cmdlet。 请参阅[PowerShell 中的用法](#usage-in-powershell)。

## <a name="whats-collected"></a>收集的内容

为7种类型的对象收集性能历史记录：

![对象的类型](media/performance-history/types-of-object.png)

每个对象类型都有许多系列：例如，为每个服务器收集 `ClusterNode.Cpu.Usage`。

有关为每个对象类型收集的内容以及如何解释它们的详细信息，请参阅以下子主题：

| Object             | 序列                                                                               |
|--------------------|--------------------------------------------------------------------------------------|
| 驱动器             | [为驱动器收集的内容](performance-history-for-drives.md)                     |
| 网络适配器   | [为网络适配器收集的内容](performance-history-for-network-adapters.md) |
| 服务器            | [为服务器收集的内容](performance-history-for-servers.md)                   |
| 虚拟硬盘 | [为虚拟硬盘收集的内容](performance-history-for-vhds.md)           |
| 虚拟机   | [为虚拟机收集的内容](performance-history-for-vms.md)              |
| 卷            | [为卷收集的内容](performance-history-for-volumes.md)                   |
| 群集           | [为群集收集的内容](performance-history-for-clusters.md)                 |

许多序列都在对等对象和父对象之间进行聚合：例如，为每个网络适配器单独收集 `NetAdapter.Bandwidth.Inbound`，并聚合到整个服务器上;同样 `ClusterNode.Cpu.Usage` 聚合到整个群集;依此类推。

## <a name="timeframes"></a>期限

性能历史记录最多存储一年，并且具有较长的粒度。 最近一小时内，每10秒提供一次度量值。 此后，它们会在更精细的序列中智能地（根据需要求平均值或求和）。 最近一天，每5分钟提供一次度量值;对于最近一周，每15分钟;依此类推。

在 Windows 管理中心，可以选择图表右上角的时间范围。

![Windows 管理中心的时间范围](media/performance-history/timeframes-in-honolulu.png)

在 PowerShell 中，使用 `-TimeFrame` 参数。

下面是可用的时间范围：

| 时间范围   | 度量频率 | 保留给 |
|-------------|-----------------------|--------------|
| `LastHour`  | 每10秒         | 1 小时       |
| `LastDay`   | 每5分钟       | 25小时     |
| `LastWeek`  | 每 15 分钟      | 8天       |
| `LastMonth` | 每1小时          | 35天      |
| `LastYear`  | 每1天           | 400天     |

## <a name="usage-in-powershell"></a>在 PowerShell 中的用法

使用 `Get-ClusterPerformanceHistory` cmdlet 可在 PowerShell 中查询和处理性能历史记录。

```PowerShell
Get-ClusterPerformanceHistory
```

   > [!TIP]
   > 使用**ClusterPerf**别名保存一些击键。

### <a name="example"></a>示例

获取虚拟机*MyVM*在最后一个小时的 CPU 使用率：

```PowerShell
Get-VM "MyVM" | Get-ClusterPerf -VMSeriesName "VM.Cpu.Usage" -TimeFrame LastHour
```

有关更高级的示例，请参阅发布的[示例脚本](performance-history-scripting.md)，这些脚本提供了入门代码以查找峰值值、计算平均值、绘制趋势线、运行离群值检测等。

### <a name="specify-the-object"></a>指定对象

可以指定管道所需的对象。 这适用于7种类型的对象：

| 管道中的对象 | 示例     |
|----------------------|-------------|
| `Get-PhysicalDisk`   | <code>Get-PhysicalDisk -SerialNumber "XYZ456" &#124; Get-ClusterPerf</code>         |
| `Get-NetAdapter`     | <code>Get-NetAdapter "Ethernet" &#124; Get-ClusterPerf</code>                       |
| `Get-ClusterNode`    | <code>Get-ClusterNode "Server123" &#124; Get-ClusterPerf</code>                     |
| `Get-VHD`            | <code>Get-VHD "C:\ClusterStorage\MyVolume\MyVHD.vhdx" &#124; Get-ClusterPerf</code> |
| `Get-VM`             | <code>Get-VM "MyVM" &#124; Get-ClusterPerf</code>                                   |
| `Get-Volume`         | <code>Get-Volume -FriendlyName "MyVolume"  &#124; Get-ClusterPerf</code>            |
| `Get-Cluster`        | <code>Get-Cluster "MyCluster" &#124; Get-ClusterPerf</code>                         |

如果不指定，将返回整个群集的性能历史记录。

### <a name="specify-the-series"></a>指定序列

可以通过以下参数指定所需的序列：


| 参数                 | 示例                       | 列表                                                                                 |
|---------------------------|-------------------------------|--------------------------------------------------------------------------------------|
| `-PhysicalDiskSeriesName` | `"PhysicalDisk.Iops.Read"`    | [为驱动器收集的内容](performance-history-for-drives.md)                     |
| `-NetAdapterSeriesName`   | `"NetAdapter.Bandwidth.Outbound"` | [为网络适配器收集的内容](performance-history-for-network-adapters.md) |
| `-ClusterNodeSeriesName`  | `"ClusterNode.Cpu.Usage"`     | [为服务器收集的内容](performance-history-for-servers.md)                   |
| `-VHDSeriesName`          | `"Vhd.Size.Current"`          | [为虚拟硬盘收集的内容](performance-history-for-vhds.md)           |
| `-VMSeriesName`           | `"Vm.Memory.Assigned"`        | [为虚拟机收集的内容](performance-history-for-vms.md)              |
| `-VolumeSeriesName`       | `"Volume.Latency.Write"`      | [为卷收集的内容](performance-history-for-volumes.md)                   |
| `-ClusterSeriesName`      | `"PhysicalDisk.Size.Total"`   | [为群集收集的内容](performance-history-for-clusters.md)                 |


   > [!TIP]
   > 使用 tab 自动补全来发现可用的序列。

如果未指定，则返回指定对象的每个可用序列。

### <a name="specify-the-timeframe"></a>指定时间范围

您可以用 `-TimeFrame` 参数指定所需的历史记录的时间范围。

   > [!TIP]
   > 使用 tab 自动补全来发现可用时间范围。

如果未指定，则返回 `MostRecent` 度量。

## <a name="how-it-works"></a>工作原理

### <a name="performance-history-storage"></a>性能历史记录存储

启用存储空间直通之后不久，将创建一个名为 `ClusterPerformanceHistory` 的大约 10 GB 的卷，并在此处预配一个可扩展存储引擎（也称为 Microsoft JET）的实例。 此轻型数据库存储性能历史记录，无需任何管理员参与或管理。

![性能历史记录存储的卷](media/performance-history/perf-history-volume.png)

卷由存储空间支持，并使用简单的双向镜像或三向镜像复原功能，具体取决于群集中的节点数。 它在驱动器或服务器发生故障后进行修复，就像存储空间直通中的其他卷。

卷使用 ReFS 但不群集共享卷（CSV），因此它仅出现在群集组的 "所有者" 节点上。 除了自动创建外，此卷没有什么特别之处：你可以查看、浏览、调整大小或将其删除（不推荐）。 如果出现问题，请参阅[故障排除](#troubleshooting)。

### <a name="object-discovery-and-data-collection"></a>对象发现和数据收集

性能历史记录自动发现群集中任何位置的相关对象（例如虚拟机）并开始流式传输其性能计数器。 计数器进行聚合、同步，并插入到数据库中。 流连续运行，经过优化，可实现最小系统影响。

集合由运行状况服务（高度可用）进行处理：如果运行该节点的节点出现故障，则它将在群集中的另一个节点后面恢复片刻。 性能历史记录可能短暂，但会自动恢复。 可以通过在 PowerShell 中运行 `Get-ClusterResource Health` 来查看运行状况服务及其所有者节点。

### <a name="handling-measurement-gaps"></a>处理测量间隙

当度量值合并到跨越更多时间的更细化系列中[时，会](#timeframes)排除丢失数据的时间段。 例如，如果服务器在30分钟内停机，然后在50% 的 CPU 上运行30分钟，则该小时的 `ClusterNode.Cpu.Usage` 平均将正确地记录为50% （而非25%）。

### <a name="extensibility-and-customization"></a>可扩展性和自定义

性能历史记录易于编写。 使用 PowerShell 直接从数据库中提取任何可用历史记录，以生成自动报告或警报，导出历史记录以进行保管，滚动你自己的可视化效果等。有关有用的起始代码，请参阅已发布的[示例脚本](performance-history-scripting.md)。

不能为其他对象、时间范围或序列收集历史记录。

度量频率和保持期当前不可配置。

## <a name="start-or-stop-performance-history"></a>启动或停止性能历史记录

### <a name="how-do-i-enable-this-feature"></a>如何实现启用此功能？

除非 `Stop-ClusterPerformanceHistory`，否则默认情况下会启用性能历史记录。

若要重新启用它，请以管理员身份运行以下 PowerShell cmdlet：

```PowerShell
Start-ClusterPerformanceHistory
```

### <a name="how-do-i-disable-this-feature"></a>如何实现禁用此功能？

若要停止收集性能历史记录，请以管理员身份运行以下 PowerShell cmdlet：

```PowerShell
Stop-ClusterPerformanceHistory
```

若要删除现有度量，请使用 `-DeleteHistory` 标志：

```PowerShell
Stop-ClusterPerformanceHistory -DeleteHistory
```

   > [!TIP]
   > 在初始部署期间，可以通过将 `Enable-ClusterStorageSpacesDirect` 的 `-CollectPerformanceHistory` 参数设置为 `$False`来阻止性能历史记录开始。

## <a name="troubleshooting"></a>故障排除

### <a name="the-cmdlet-doesnt-work"></a>Cmdlet 不起作用

类似于 "ClusterPerf" 一词的错误消息*未被识别为 cmdlet 的名称*，这意味着该功能不可用或未安装。 验证你是否具有 Windows Server 有问必答 Preview build 17692 或更高版本，以及你是否已安装故障转移群集，并且你正在运行存储空间直通。

   > [!NOTE]
   > 此功能在 Windows Server 2016 或更早版本上不可用。

### <a name="no-data-available"></a>无可用数据 

如果图表显示 "*无可用数据*" （如图所示），以下是解决方法：

![无可用数据](media/performance-history/no-data-available.png)

1. 如果该对象是新添加或创建的，请等待它被发现（最多15分钟）。

2. 刷新页面，或等待下一次后台刷新（最多30秒）。

3. 某些特殊对象从性能历史记录中排除–例如，未群集的虚拟机，以及不使用群集共享卷（CSV）文件系统的卷。 对于 "精细打印"，请检查对象类型的子主题，如[卷的性能历史记录](performance-history-for-volumes.md)。

4. 如果问题仍然存在，请以管理员身份打开 PowerShell 并运行 `Get-ClusterPerf` cmdlet。 Cmdlet 包含疑难解答逻辑来识别常见问题，例如，如果缺少 ClusterPerformanceHistory 卷，则提供修正说明。

5. 如果上一步骤中的命令未返回任何内容，则可以尝试通过在 PowerShell 中运行 `Stop-ClusterResource Health ; Start-ClusterResource Health` 来重新启动运行状况服务（收集性能历史记录）。

## <a name="see-also"></a>另请参阅

- [存储空间直通概述](storage-spaces-direct-overview.md)
