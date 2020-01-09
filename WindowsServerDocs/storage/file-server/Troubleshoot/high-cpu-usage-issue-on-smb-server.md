---
title: SMB 服务器上的 CPU 使用率过高问题
description: 介绍如何对 SMB 服务器上的 CPU 使用率较高的问题进行故障排除。
author: Deland-Han
manager: dcscontentpm
audience: ITPro
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 8a14952ca90b6ee3bea901fd944d7c9843492fd4
ms.sourcegitcommit: 8cf04db0bc44fd98f4321dca334e38c6573fae6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654338"
---
# <a name="high-cpu-usage-issue-on-the-smb-server"></a>SMB 服务器上的 CPU 使用率过高问题

本文介绍了如何排查 SMB 服务器上的 CPU 使用率高的问题。

## <a name="high-cpu-usage-because-of-storage-performance-issues"></a>由于存储性能问题导致的 CPU 使用率过高

存储性能问题可能会导致 SMB 服务器上的 CPU 使用率很高。 在进行故障排除之前，请确保在 SMB 服务器上安装了最新的更新汇总，以消除 srv2 中的任何已知问题。

在大多数情况下，你会注意到系统进程中 CPU 使用率高的问题。 在继续之前，请使用进程资源管理器确保 srv2 或 .sys 消耗过多的 CPU 资源。

### <a name="storage-area-network-san-scenario"></a>存储区域网络（SAN）方案

在聚合级别中，总体 SAN 性能可能看起来很正常。 但是，在处理 SMB 问题时，单个请求响应时间是最重要的。

通常，此问题可能由 SAN 中的某种形式的命令队列导致。 可以使用**Perfmon**来捕获**Microsoft Windows-StorPort**跟踪，并对其进行分析以准确确定存储响应能力。

### <a name="disk-io-latency"></a>磁盘 IO 延迟

磁盘 IO 延迟是指创建和完成磁盘 IO 请求之间的延迟时间。

以 Perfmon 度量的 IO 延迟包括在硬件层中所用的时间，以及在 Microsoft 端口驱动程序队列中所用的时间（对于 SCSI 为 Storport）。 如果正在运行的进程生成较大的 StorPort 队列，则测量的延迟会增加。 这是因为 IO 必须等待，然后才能将它调度到硬件层。

在 Perfmon 中，以下计数器显示物理磁盘延迟：

- "物理磁盘性能对象"-\> "Avg. Disk sec/Read counter" –这会显示平均读取延迟。

- "物理磁盘性能对象"-\> "Avg. Disk sec/Write 计数器" –这会显示平均写入滞后时间。

- "物理磁盘性能对象"-\> "Avg. Disk sec/Transfer counter" –这会显示读写的组合平均值。

"\_Total" 实例是计算机中所有物理磁盘的延迟平均值。 其他每个实例表示单独的物理磁盘。

> [!NOTE]
> 不要将这些计数器与 Avg. Disk 传输/秒混淆。它们完全不同。

### <a name="windows-storage-stack-follows"></a>Windows 存储堆栈跟随

本部分提供了有关 Windows 存储堆栈的简要说明。

当应用程序创建 IO 请求时，它会将请求发送到堆栈顶部的 Windows IO 子系统。 IO 随后沿堆栈向下传递到硬件 "磁盘" 子系统。 然后，响应将一直向下移动。 在此过程中，每个层将执行其功能，然后将 IO 交给下一层。

![堆栈流](media/high-cpu-usage-issue-on-smb-server-1.png)

Perfmon 不会创建每秒的性能数据。 而是使用 Windows 中的其他子系统提供的数据。

对于 "物理磁盘性能对象"，将在存储堆栈中的 "分区管理器" 级别捕获数据。

当我们度量上一部分中提到的计数器时，我们将测量请求在 "分区管理器" 级别下面所用的所有时间。 当分区管理器沿堆栈向后发送 IO 请求时，我们将对其进行标记。 当它返回时，将再次对其进行标记并计算时间差。 时间差为延迟。

通过执行此操作，我们将考虑以下组件所用的时间：

- 类驱动程序-它管理设备类型，如磁盘和磁带等。

- 端口驱动程序-它管理传输协议，如 SCSI、FC、SATA 等。

- 设备微型端口驱动程序-这是存储适配器的设备驱动程序。 它由设备制造商提供，例如 Raid 控制器和 FC HBA。

- 磁盘子系统-其中包括设备微型端口驱动程序下的所有内容。 这可以像连接到单个物理硬盘的电缆一样简单，也可以像存储区域网络一样简单。 如果确定该问题是由该组件引起的，则可以与硬件供应商联系，以获取有关故障排除的详细信息。

### <a name="disk-queuing"></a>磁盘队列

磁盘子系统在给定的时间可以接受有限数量的 IO。 多余的 IO 将排队等候，直到磁盘可以再次接受 IO。 IO 在 "分区管理器" 级别下的队列中花费的时间将在 Perfmon 物理磁盘延迟度量值中进行考虑。 当队列增大并且 IO 必须等待更长时间时，测量的延迟也会增长。

"分区管理器" 级别下面有多个队列，如下所示：

- Microsoft 端口驱动程序队列-SCSIport 或 Storport 队列

- 制造商提供的设备驱动程序队列-OEM 设备驱动程序

- 硬件队列–如磁盘控制器队列、SAN 交换机队列、阵列控制器队列和硬盘队列

同时，我们还考虑到硬盘正在主动处理 IO 的时间，以及为请求返回到 "分区管理器" 级别以标记为已完成所需的行程时间。

最后，我们必须特别注意端口驱动程序队列（适用于 SCSI Storport）。 在将 IO 移交给制造商提供的设备微型端口驱动程序之前，端口驱动程序是最后一个要触摸 IO 的 Microsoft 组件。

如果设备微型端口驱动程序无法再接受 IO，原因是其队列或其下的硬件队列已饱和，我们将在端口驱动程序队列中开始累积 IO。 Microsoft 端口驱动程序队列的大小仅受可用系统内存（RAM）的限制，并且可能会变得非常大。 这将导致较大的测滞后时间。

## <a name="high-cpu-caused-by-enumerating-folders"></a>枚举文件夹导致的 CPU 使用率过高 

若要解决此问题，请禁用基于访问权限的枚举（ABE）功能。

若要确定哪些 SMB 共享启用了 ABE，请运行以下 PowerShell 命令：

```PowerShell
Get-SmbShare | Select Name, FolderEnumerationMode
```

无限制 = ABE 已禁用。 <br />
AccessBase = ABE 已启用。


可以在**服务器管理器**中启用 ABE。 Navigatie 到 > **共享**的**文件和存储服务**，请右键单击该共享，选择 "**属性**"，然后单击 "**设置**"，然后选择 "**启用基于访问权限的枚举**"。

![UI 选项](media/high-cpu-usage-issue-on-smb-server-2.png)

此外，还可以将**ABELevel**减少到较低级别（1或2），以提高性能。

通过控制台或 RDP 会话在本地打开文件夹时，可以检查磁盘性能。
