---
title: 虚拟硬盘的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/09/2018
ms.localizationpriority: medium
ms.openlocfilehash: 18694975e48d199f2f690aebe8af2a4613a4b1f0
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474704"
---
# <a name="performance-history-for-virtual-hard-disks"></a>虚拟硬盘的性能历史记录

> 适用于：Windows Server 2019

本主题中的[存储空间直通性能历史记录](performance-history.md)详细说明了为虚拟硬盘（VHD）文件收集的性能历史记录。 性能历史记录适用于连接到正在运行的群集虚拟机的每个 VHD。 性能历史记录适用于 VHD 和 VHDX 格式，但不适用于共享 VHDX 文件。

   > [!NOTE]
   > 收集新创建或移动的 VHD 文件可能需要几分钟时间。

## <a name="series-names-and-units"></a>序列名称和单位

为每个符合条件的虚拟硬盘收集这些系列：

| 系列                    | 计价单位             |
|---------------------------|------------------|
| `vhd.iops.read`           | 每秒       |
| `vhd.iops.write`          | 每秒       |
| `vhd.iops.total`          | 每秒       |
| `vhd.throughput.read`     | 每秒字节数 |
| `vhd.throughput.write`    | 每秒字节数 |
| `vhd.throughput.total`    | 每秒字节数 |
| `vhd.latency.average`     | seconds          |
| `vhd.size.current`        | 字节            |
| `vhd.size.maximum`        | 字节            |

## <a name="how-to-interpret"></a>如何解释

| 系列                    | 如何解释                                                                                                 |
|---------------------------|------------------------------------------------------------------------------------------------------------------|
| `vhd.iops.read`           | 虚拟硬盘每秒完成的读取操作数。                                         |
| `vhd.iops.write`          | 虚拟硬盘每秒完成的写入操作数。                                        |
| `vhd.iops.total`          | 虚拟硬盘每秒完成的读取或写入操作总数。                          |
| `vhd.throughput.read`     | 每秒从虚拟硬盘读取的数据量。                                                     |
| `vhd.throughput.write`    | 每秒写入虚拟硬盘的数据量。                                                    |
| `vhd.throughput.total`    | 每秒从虚拟硬盘读取或写入的总数据量。                                 |
| `vhd.latency.average`     | 虚拟硬盘的所有操作的平均延迟。                                              |
| `vhd.size.current`        | 如果动态扩展，则为虚拟硬盘的当前文件大小。 如果已修复，则不收集序列。 |
| `vhd.size.maximum`        | 如果动态扩展，则为虚拟硬盘的最大大小。 如果是固定的，则为大小。                  |

## <a name="where-they-come-from"></a>它们来自何处

`iops.*` `throughput.*` `latency.*` 从 `Hyper-V Virtual Storage Device` 运行虚拟机的服务器上的性能计数器集中收集、和序列，每个 VHD 或 VHDX 一个实例。

| 系列                    | 源计数器         |
|---------------------------|------------------------|
| `vhd.iops.read`           | `Read Operations/Sec`  |
| `vhd.iops.write`          | `Write Operations/Sec` |
| `vhd.iops.total`          | *以上的总和*     |
| `vhd.throughput.read`     | `Read Bytes/sec`       |
| `vhd.throughput.write`    | `Write Bytes/sec`      |
| `vhd.throughput.total`    | *以上的总和*     |
| `vhd.latency.average`     | `Latency`              |

   > [!NOTE]
   > 计数器在整个间隔内进行测量，而不是采样。 例如，如果 VHD 在9秒内处于非活动状态，但在第10秒内完成了30个 IOs，则在 `vhd.iops.total` 此10秒的时间间隔内平均将其记录为每秒3个 ios。 这可确保其性能历史记录捕获所有活动，并使干扰稳定。

## <a name="usage-in-powershell"></a>PowerShell 中的用法

使用 "[获取 VHD](https://docs.microsoft.com/powershell/module/hyper-v/get-vhd) " cmdlet：

```PowerShell
Get-VHD <Path> | Get-ClusterPerf
```

若要从虚拟机中获取每个 VHD 的路径：

```PowerShell
(Get-VM <Name>).HardDrives | Select Path
```

   > [!NOTE]
   > 获取 VHD cmdlet 需要提供文件路径。 它不支持枚举。

## <a name="additional-references"></a>其他参考

- [存储空间直通的性能历史记录](performance-history.md)
