---
title: 存储空间直通性能历史记录编写脚本
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 05/15/2018
ms.localizationpriority: medium
ms.openlocfilehash: 53a5f2aa403c83d24acde1fc57e793141175d9b6
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474714"
---
# <a name="scripting-with-powershell-and-storage-spaces-direct-performance-history"></a>通过 PowerShell 编写脚本并存储空间直通性能历史记录

> 适用于：Windows Server 2019

在 Windows Server 2019 中，[存储空间直通](storage-spaces-direct-overview.md)记录和存储虚拟机、服务器、驱动器、卷、网络适配器等的广泛[性能历史记录](performance-history.md)。 在 PowerShell 中，可以轻松地查询和处理性能历史记录，因此，你可以快速地从*原始数据*转为*实际答案*，例如：

1. 上周是否有任何 CPU 高峰？
2. 任何物理磁盘是否存在异常延迟？
3. 目前哪些 Vm 消耗最多的存储 IOPS？
4. 网络带宽是否饱和？
5. 此卷何时会耗尽可用空间？
6. 过去一个月，哪些 Vm 使用最多的内存？

`Get-ClusterPerf`Cmdlet 是为编写脚本而构建的。 它接受来自 `Get-VM` 或管道的输入 `Get-PhysicalDisk` 来处理关联，还可以通过管道将输出传递到实用程序 cmdlet （如 `Sort-Object` 、 `Where-Object` 和）， `Measure-Object` 快速编写功能强大的查询。

**本主题提供并说明6个示例脚本，用于回答上述6个问题。** 它们提供了可应用于跨各种数据和时间段查找高峰、查找平均值、绘制趋势线、运行离群检测等功能的模式。 它们作为免费的入门代码提供，供你复制、扩展和重复使用。

   > [!NOTE]
   > 为简洁起见，示例脚本省略了可能需要高质量 PowerShell 代码的错误处理。 它们主要用于灵感和教育，而不是在生产环境中使用。

## <a name="sample-1-cpu-i-see-you"></a>示例1： CPU，我看到了！

此示例使用 `ClusterNode.Cpu.Usage` `LastWeek` 时间范围内的序列来显示群集中每个服务器的最大值（"高水位线"）、最小值和平均 CPU 使用率。 它还执行简单的分位分析来显示过去8天内 CPU 使用率超过25%、50% 和75% 的小时数。

### <a name="screenshot"></a>屏幕快照

在下面的屏幕截图中，我们发现*Server 02*在上周有一个无法解释的峰值：

![PowerShell 屏幕截图](media/performance-history/Show-CpuMinMaxAvg.png)

### <a name="how-it-works"></a>工作原理

管道的输出非常 `Get-ClusterPerf` 适合内置 `Measure-Object` cmdlet，只需指定 `Value` 属性即可。 对于其 `-Maximum` 、 `-Minimum` 和 `-Average` 标志， `Measure-Object` 为我们提供了几乎免费的前三列。 若要进行四分位分析，可以通过管道来 `Where-Object` 统计 `-Gt` （大于）25、50或75的值（大于）。 最后一步是 beautify `Format-Hours` 和 `Format-Percent` helper 函数-当然是可选的。

### <a name="script"></a>脚本

脚本如下：

```
Function Format-Hours {
    Param (
        $RawValue
    )
    # Weekly timeframe has frequency 15 minutes = 4 points per hour
    [Math]::Round($RawValue/4)
}

Function Format-Percent {
    Param (
        $RawValue
    )
    [String][Math]::Round($RawValue) + " " + "%"
}

$Output = Get-ClusterNode | ForEach-Object {
    $Data = $_ | Get-ClusterPerf -ClusterNodeSeriesName "ClusterNode.Cpu.Usage" -TimeFrame "LastWeek"

    $Measure = $Data | Measure-Object -Property Value -Minimum -Maximum -Average
    $Min = $Measure.Minimum
    $Max = $Measure.Maximum
    $Avg = $Measure.Average

    [PsCustomObject]@{
        "ClusterNode"    = $_.Name
        "MinCpuObserved" = Format-Percent $Min
        "MaxCpuObserved" = Format-Percent $Max
        "AvgCpuObserved" = Format-Percent $Avg
        "HrsOver25%"     = Format-Hours ($Data | Where-Object Value -Gt 25).Length
        "HrsOver50%"     = Format-Hours ($Data | Where-Object Value -Gt 50).Length
        "HrsOver75%"     = Format-Hours ($Data | Where-Object Value -Gt 75).Length
    }
}

$Output | Sort-Object ClusterNode | Format-Table
```

## <a name="sample-2-fire-fire-latency-outlier"></a>示例2：火灾、火灾、延迟离群

此示例使用 `PhysicalDisk.Latency.Average` 时间范围内的序列 `LastHour` 来查找统计离群值，并将其定义为具有每小时平均延迟的驱动器（超过 +3 σ（三个标准偏差）高于总体平均值。

   > [!IMPORTANT]
   > 为简洁起见，此脚本不会实现低差异的安全措施，不处理部分丢失的数据，也不区分模型或固件等。请毋庸置疑，不要独自依赖此脚本来确定是否更换硬盘。 此处仅提供教育目的。

### <a name="screenshot"></a>屏幕快照

在下面的屏幕截图中，我们看到没有离群值：

![PowerShell 屏幕截图](media/performance-history/Show-LatencyOutlierHDD.png)

### <a name="how-it-works"></a>工作原理

首先，通过检查是否一致，排除空闲或近空闲驱动器 `PhysicalDisk.Iops.Total` `-Gt 1` 。 对于每个活动 HDD，我们将 `LastHour` 按10秒的时间间隔，将其时间段传输为360，以 `Measure-Object -Average` 获取其在最近一小时内的平均延迟。 这会设置总体。

我们实现了[众所周知的公式](http://www.mathsisfun.com/data/standard-deviation.html)来找出总体的平均值 `μ` 和标准偏差 `σ` 。 对于每个活动 HDD，将其平均延迟与总体平均值进行比较并除以标准偏差。 我们保留原始值，因此我们可以获得 `Sort-Object` 结果，但使用 `Format-Latency` 和 `Format-StandardDeviation` 帮助程序函数来 beautify 我们所要显示的内容-当然是可选的。

如果任何驱动器超过 +3 σ，则 `Write-Host` 为红色; 否则为绿色。

### <a name="script"></a>脚本

脚本如下：

```
Function Format-Latency {
    Param (
        $RawValue
    )
    $i = 0 ; $Labels = ("s", "ms", "μs", "ns") # Petabits, just in case!
    Do { $RawValue *= 1000 ; $i++ } While ( $RawValue -Lt 1 )
    # Return
    [String][Math]::Round($RawValue, 2) + " " + $Labels[$i]
}

Function Format-StandardDeviation {
    Param (
        $RawValue
    )
    If ($RawValue -Gt 0) {
        $Sign = "+"
    }
    Else {
        $Sign = "-"
    }
    # Return
    $Sign + [String][Math]::Round([Math]::Abs($RawValue), 2) + "σ"
}

$HDD = Get-StorageSubSystem Cluster* | Get-PhysicalDisk | Where-Object MediaType -Eq HDD

$Output = $HDD | ForEach-Object {

    $Iops = $_ | Get-ClusterPerf -PhysicalDiskSeriesName "PhysicalDisk.Iops.Total" -TimeFrame "LastHour"
    $AvgIops = ($Iops | Measure-Object -Property Value -Average).Average

    If ($AvgIops -Gt 1) { # Exclude idle or nearly idle drives

        $Latency = $_ | Get-ClusterPerf -PhysicalDiskSeriesName "PhysicalDisk.Latency.Average" -TimeFrame "LastHour"
        $AvgLatency = ($Latency | Measure-Object -Property Value -Average).Average

        [PsCustomObject]@{
            "FriendlyName"  = $_.FriendlyName
            "SerialNumber"  = $_.SerialNumber
            "MediaType"     = $_.MediaType
            "AvgLatencyPopulation" = $null # Set below
            "AvgLatencyThisHDD"    = Format-Latency $AvgLatency
            "RawAvgLatencyThisHDD" = $AvgLatency
            "Deviation"            = $null # Set below
            "RawDeviation"         = $null # Set below
        }
    }
}

If ($Output.Length -Ge 3) { # Minimum population requirement

    # Find mean μ and standard deviation σ
    $μ = ($Output | Measure-Object -Property RawAvgLatencyThisHDD -Average).Average
    $d = $Output | ForEach-Object { ($_.RawAvgLatencyThisHDD - $μ) * ($_.RawAvgLatencyThisHDD - $μ) }
    $σ = [Math]::Sqrt(($d | Measure-Object -Sum).Sum / $Output.Length)

    $FoundOutlier = $False

    $Output | ForEach-Object {
        $Deviation = ($_.RawAvgLatencyThisHDD - $μ) / $σ
        $_.AvgLatencyPopulation = Format-Latency $μ
        $_.Deviation = Format-StandardDeviation $Deviation
        $_.RawDeviation = $Deviation
        # If distribution is Normal, expect >99% within 3σ
        If ($Deviation -Gt 3) {
            $FoundOutlier = $True
        }
    }

    If ($FoundOutlier) {
        Write-Host -BackgroundColor Black -ForegroundColor Red "Oh no! There's an HDD significantly slower than the others."
    }
    Else {
        Write-Host -BackgroundColor Black -ForegroundColor Green "Good news! No outlier found."
    }

    $Output | Sort-Object RawDeviation -Descending | Format-Table FriendlyName, SerialNumber, MediaType, AvgLatencyPopulation, AvgLatencyThisHDD, Deviation

}
Else {
    Write-Warning "There aren't enough active drives to look for outliers right now."
}
```

## <a name="sample-3-noisy-neighbor-thats-write"></a>示例3：干扰邻居？ 编写！

性能历史记录也可以回答*right now*问题。 新度量值每10秒实时可用。 此示例使用 `VHD.Iops.Total` `MostRecent` 时间范围内的序列来确定最繁忙的虚拟机（某些可能会说 "noisiest"）虚拟机消耗最多的存储 IOPS，并跨群集中的每个主机，并显示其活动的读/写细分。

### <a name="screenshot"></a>屏幕快照

在下面的屏幕截图中，我们将看到按存储活动列出的前10个虚拟机：

![PowerShell 屏幕截图](media/performance-history/Show-TopIopsVMs.png)

### <a name="how-it-works"></a>工作原理

与不同 `Get-PhysicalDisk` 的 `Get-VM` 是，该 cmdlet 不是群集感知的–它仅返回本地服务器上的 vm。 若要从每个服务器并行查询，我们将在中包装调用 `Invoke-Command (Get-ClusterNode).Name { ... }` 。 对于每个 VM，我们将获得 `VHD.Iops.Total` 、 `VHD.Iops.Read` 和 `VHD.Iops.Write` 度量。 如果不指定 `-TimeFrame` 参数，则将获取 `MostRecent` 每个的单个数据点。

   > [!TIP]
   > 这些系列反映了此 VM 的活动对其所有 VHD/VHDX 文件的总和。 这是一个示例，其中会自动聚合性能历史记录。 若要获取每个 VHD/VHDX 细目细目，可以通过管道将个体传递 `Get-VHD` 到 `Get-ClusterPerf` 而不是 VM。

每个服务器的结果都作为 `$Output` ，我们可以将其作为 `Sort-Object` `Select-Object -First 10` 。 请注意， `Invoke-Command` 使用属性修饰结果以 `PsComputerName` 指示它们的来源，我们可以打印这些结果来了解 VM 的运行位置。

### <a name="script"></a>脚本

脚本如下：

```
$Output = Invoke-Command (Get-ClusterNode).Name {
    Function Format-Iops {
        Param (
            $RawValue
        )
        $i = 0 ; $Labels = (" ", "K", "M", "B", "T") # Thousands, millions, billions, trillions...
        Do { if($RawValue -Gt 1000){$RawValue /= 1000 ; $i++ } } While ( $RawValue -Gt 1000 )
        # Return
        [String][Math]::Round($RawValue) + " " + $Labels[$i]
    }

    Get-VM | ForEach-Object {
        $IopsTotal = $_ | Get-ClusterPerf -VMSeriesName "VHD.Iops.Total"
        $IopsRead  = $_ | Get-ClusterPerf -VMSeriesName "VHD.Iops.Read"
        $IopsWrite = $_ | Get-ClusterPerf -VMSeriesName "VHD.Iops.Write"
        [PsCustomObject]@{
            "VM" = $_.Name
            "IopsTotal" = Format-Iops $IopsTotal.Value
            "IopsRead"  = Format-Iops $IopsRead.Value
            "IopsWrite" = Format-Iops $IopsWrite.Value
            "RawIopsTotal" = $IopsTotal.Value # For sorting...
        }
    }
}

$Output | Sort-Object RawIopsTotal -Descending | Select-Object -First 10 | Format-Table PsComputerName, VM, IopsTotal, IopsRead, IopsWrite
```

## <a name="sample-4-as-they-say-25-gig-is-the-new-10-gig"></a>示例4：正如说，"25-g 是新的 10-g"

此示例使用 `NetAdapter.Bandwidth.Total` `LastDay` 时间范围内的序列来查找网络饱和标志，定义为 >90% 的理论最大带宽。 对于群集中的每个网络适配器，它将上一天中观测到的最大带宽与它所规定的链接速度进行比较。

### <a name="screenshot"></a>屏幕快照

在下面的屏幕截图中，我们看到，最后一天的*FABRIKAM NX-4 Pro #2*达到高峰：

![PowerShell 屏幕截图](media/performance-history/Show-NetworkSaturation.png)

### <a name="how-it-works"></a>工作原理

我们会 `Invoke-Command` `Get-NetAdapter` 在每个服务器和管道上重复我们的技巧 `Get-ClusterPerf` 。 在此过程中，我们将提取两个相关属性：其 `LinkSpeed` 字符串（如 "10 Gbps"）及其原始 `Speed` 整数（如10000000000）。 我们使用 `Measure-Object` 来获取最后一天的平均和峰值（提醒：时间范围内的每个度量值都 `LastDay` 表示5分钟），并乘以每个字节8位以获得苹果比较。

   > [!NOTE]
   > 某些供应商（如 Chelsio）在其*网络适配器*性能计数器中包括远程直接内存访问（RDMA）活动，因此它包含在 `NetAdapter.Bandwidth.Total` 系列中。 其他类（如 Mellanox）可能不会。 如果你的供应商没有，只需 `NetAdapter.Bandwidth.RDMA.Total` 在此脚本的版本中添加该系列。

### <a name="script"></a>脚本

脚本如下：

```
$Output = Invoke-Command (Get-ClusterNode).Name {

    Function Format-BitsPerSec {
        Param (
            $RawValue
        )
        $i = 0 ; $Labels = ("bps", "kbps", "Mbps", "Gbps", "Tbps", "Pbps") # Petabits, just in case!
        Do { $RawValue /= 1000 ; $i++ } While ( $RawValue -Gt 1000 )
        # Return
        [String][Math]::Round($RawValue) + " " + $Labels[$i]
    }

    Get-NetAdapter | ForEach-Object {

        $Inbound = $_ | Get-ClusterPerf -NetAdapterSeriesName "NetAdapter.Bandwidth.Inbound" -TimeFrame "LastDay"
        $Outbound = $_ | Get-ClusterPerf -NetAdapterSeriesName "NetAdapter.Bandwidth.Outbound" -TimeFrame "LastDay"

        If ($Inbound -Or $Outbound) {

            $InterfaceDescription = $_.InterfaceDescription
            $LinkSpeed = $_.LinkSpeed

            $MeasureInbound = $Inbound | Measure-Object -Property Value -Maximum
            $MaxInbound = $MeasureInbound.Maximum * 8 # Multiply to bits/sec

            $MeasureOutbound = $Outbound | Measure-Object -Property Value -Maximum
            $MaxOutbound = $MeasureOutbound.Maximum * 8 # Multiply to bits/sec

            $Saturated = $False

            # Speed property is Int, e.g. 10000000000
            If (($MaxInbound -Gt (0.90 * $_.Speed)) -Or ($MaxOutbound -Gt (0.90 * $_.Speed))) {
                $Saturated = $True
                Write-Warning "In the last day, adapter '$InterfaceDescription' on server '$Env:ComputerName' exceeded 90% of its '$LinkSpeed' theoretical maximum bandwidth. In general, network saturation leads to higher latency and diminished reliability. Not good!"
            }

            [PsCustomObject]@{
                "NetAdapter"  = $InterfaceDescription
                "LinkSpeed"   = $LinkSpeed
                "MaxInbound"  = Format-BitsPerSec $MaxInbound
                "MaxOutbound" = Format-BitsPerSec $MaxOutbound
                "Saturated"   = $Saturated
            }
        }
    }
}

$Output | Sort-Object PsComputerName, InterfaceDescription | Format-Table PsComputerName, NetAdapter, LinkSpeed, MaxInbound, MaxOutbound, Saturated
```

## <a name="sample-5-make-storage-trendy-again"></a>示例5：再次使存储时髦！

若要查看宏趋势，性能历史记录将保留一年。 此示例使用 `Volume.Size.Available` 时间范围内的序列 `LastYear` 来确定存储空间填满的速率，并估计其最大值。

### <a name="screenshot"></a>屏幕快照

在下面的屏幕截图中，我们看到*备份*卷每日增加了 15 GB：

![PowerShell 屏幕截图](media/performance-history/Show-StorageTrend.png)

在此期间，它将在42天内达到其容量。

### <a name="how-it-works"></a>工作原理

`LastYear`时间范围每天有一个数据点。 尽管你只需要两个点来容纳趋势线，但实际上，更好的做法是需要更多的时间，如14天。 我们使用 `Select-Object -Last 14` 为 [1，14] 范围内的*x*设置 *（x，y）* 点的数组。 利用这些要点，我们实现了直接[线性最小二乘法算法](http://mathworld.wolfram.com/LeastSquaresFitting.html)，以查找 `$A` `$B` 最适合*y = ax + b*的行并将其参数化。 欢迎使用高中的高中。

按趋势（斜度）将卷的属性除以该量， `SizeRemaining` `$A` 可以让我们 crudely 估计在该卷已满之前，当前的存储增长速率。 `Format-Bytes`、 `Format-Trend` 和 `Format-Days` helper 函数 beautify 输出。

   > [!IMPORTANT]
   > 此估计值是线性的，仅基于最新的14个日常度量值。 存在更复杂且更准确的方法。 请毋庸置疑，不要独自依赖此脚本来确定是否投资扩展存储。 此处仅提供教育目的。

### <a name="script"></a>脚本

脚本如下：

```

Function Format-Bytes {
    Param (
        $RawValue
    )
    $i = 0 ; $Labels = ("B", "KB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB")
    Do { $RawValue /= 1024 ; $i++ } While ( $RawValue -Gt 1024 )
    # Return
    [String][Math]::Round($RawValue) + " " + $Labels[$i]
}

Function Format-Trend {
    Param (
        $RawValue
    )
    If ($RawValue -Eq 0) {
        "0"
    }
    Else {
        If ($RawValue -Gt 0) {
            $Sign = "+"
        }
        Else {
            $Sign = "-"
        }
        # Return
        $Sign + $(Format-Bytes [Math]::Abs($RawValue)) + "/day"
    }
}

Function Format-Days {
    Param (
        $RawValue
    )
    [Math]::Round($RawValue)
}

$CSV = Get-Volume | Where-Object FileSystem -Like "*CSV*"

$Output = $CSV | ForEach-Object {

    $N = 14 # Require 14 days of history

    $Data = $_ | Get-ClusterPerf -VolumeSeriesName "Volume.Size.Available" -TimeFrame "LastYear" | Sort-Object Time | Select-Object -Last $N

    If ($Data.Length -Ge $N) {

        # Last N days as (x, y) points
        $PointsXY = @()
        1..$N | ForEach-Object {
            $PointsXY += [PsCustomObject]@{ "X" = $_ ; "Y" = $Data[$_-1].Value }
        }

        # Linear (y = ax + b) least squares algorithm
        $MeanX = ($PointsXY | Measure-Object -Property X -Average).Average
        $MeanY = ($PointsXY | Measure-Object -Property Y -Average).Average
        $XX = $PointsXY | ForEach-Object { $_.X * $_.X }
        $XY = $PointsXY | ForEach-Object { $_.X * $_.Y }
        $SSXX = ($XX | Measure-Object -Sum).Sum - $N * $MeanX * $MeanX
        $SSXY = ($XY | Measure-Object -Sum).Sum - $N * $MeanX * $MeanY
        $A = ($SSXY / $SSXX)
        $B = ($MeanY - $A * $MeanX)
        $RawTrend = -$A # Flip to get daily increase in Used (vs decrease in Remaining)
        $Trend = Format-Trend $RawTrend

        If ($RawTrend -Gt 0) {
            $DaysToFull = Format-Days ($_.SizeRemaining / $RawTrend)
        }
        Else {
            $DaysToFull = "-"
        }
    }
    Else {
        $Trend = "InsufficientHistory"
        $DaysToFull = "-"
    }

    [PsCustomObject]@{
        "Volume"     = $_.FileSystemLabel
        "Size"       = Format-Bytes ($_.Size)
        "Used"       = Format-Bytes ($_.Size - $_.SizeRemaining)
        "Trend"      = $Trend
        "DaysToFull" = $DaysToFull
    }
}

$Output | Format-Table
```

## <a name="sample-6-memory-hog-you-can-run-but-you-cant-hide"></a>示例6：内存占用，可以运行但无法隐藏

由于将为整个群集集中收集和存储性能历史记录，因此无论 Vm 在主机之间移动多少次，都不需要将数据从不同的计算机中汇聚在一起。 此示例使用 `VM.Memory.Assigned` 时间范围内的序列 `LastMonth` 来识别过去35天消耗最多内存的虚拟机。

### <a name="screenshot"></a>屏幕快照

在下面的屏幕截图中，我们将按上个月的内存使用量查看前10个虚拟机：

![PowerShell 屏幕截图](media/performance-history/Show-TopMemoryVMs.png)

### <a name="how-it-works"></a>工作原理

我们 `Invoke-Command` `Get-VM` 在每个服务器上重复我们在上面介绍的技巧。 我们使用 `Measure-Object -Average` 获取每个 VM 每月的平均时间，然后获取 `Sort-Object` `Select-Object -First 10` 我们的排行榜。 （或许是我们*最需要*的列表？）

### <a name="script"></a>脚本

脚本如下：

```
$Output = Invoke-Command (Get-ClusterNode).Name {
    Function Format-Bytes {
        Param (
            $RawValue
        )
        $i = 0 ; $Labels = ("B", "KB", "MB", "GB", "TB", "PB", "EB", "ZB", "YB")
        Do { if( $RawValue -Gt 1024 ){ $RawValue /= 1024 ; $i++ } } While ( $RawValue -Gt 1024 )
        # Return
        [String][Math]::Round($RawValue) + " " + $Labels[$i]
    }

    Get-VM | ForEach-Object {
        $Data = $_ | Get-ClusterPerf -VMSeriesName "VM.Memory.Assigned" -TimeFrame "LastMonth"
        If ($Data) {
            $AvgMemoryUsage = ($Data | Measure-Object -Property Value -Average).Average
            [PsCustomObject]@{
                "VM" = $_.Name
                "AvgMemoryUsage" = Format-Bytes $AvgMemoryUsage.Value
                "RawAvgMemoryUsage" = $AvgMemoryUsage.Value # For sorting...
            }
        }
    }
}

$Output | Sort-Object RawAvgMemoryUsage -Descending | Select-Object -First 10 | Format-Table PsComputerName, VM, AvgMemoryUsage
```

就这么简单！ 希望这些示例能够吸引您并帮助您入门。 通过存储空间直通性能历史记录和功能强大的脚本编写式 `Get-ClusterPerf` cmdlet，你可以提出问题并进行解答！ –管理和监视 Windows Server 2019 基础结构时的复杂问题。

## <a name="additional-references"></a>其他参考

- [Windows PowerShell 入门](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell)
- [存储空间直通概述](storage-spaces-direct-overview.md)
- [性能历史记录](performance-history.md)
