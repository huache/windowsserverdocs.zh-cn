---
title: 了解和部署永久性内存
description: 有关永久性内存的详细信息以及如何在 Windows Server 2019 中通过存储空间直通对其进行设置的详细信息。
keywords: 存储空间直通、永久性内存、pmem、存储、S2D
ms.prod: windows-server
ms.author: adagashe
ms.technology: storage-spaces
ms.topic: article
author: adagashe
ms.date: 1/27/2020
ms.localizationpriority: medium
ms.openlocfilehash: a9070d2e2ab73c7882f4b2ef585ccb01986695bb
ms.sourcegitcommit: 07c9d4ea72528401314e2789e3bc2e688fc96001
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76822310"
---
# <a name="understand-and-deploy-persistent-memory"></a>了解和部署永久性内存

> 适用于： Windows Server 2019

永久性内存（或 PMem）是一种新类型的内存技术，可提供经济实惠的大容量和持久性的独特组合。 本文提供有关 PMem 的背景以及使用存储空间直通在 Windows Server 2019 中部署它的步骤。

## <a name="background"></a>后台

PMem 是一种非易失性 RAM （NVDIMM），它通过电源周期保留其内容。 即使在出现意外断电、用户启动了关机、系统崩溃等事件时，也会保留内存内容。 这一独特的特征是，还可以使用 PMem 作为存储。 这就是为什么你会听到人们将 PMem 称为 "存储类内存" 的原因。

若要查看其中一些优点，请查看 Microsoft Ignite 2018 中的以下演示。

[![Microsoft Ignite 2018 Pmem 演示](http://img.youtube.com/vi/8WMXkMLJORc/0.jpg)](http://www.youtube.com/watch?v=8WMXkMLJORc)

提供容错能力的任何存储系统都需要提供分布式写入副本。 此类操作必须遍历网络并放大后端写入流量。 出于此原因，通常只通过测量读取来实现最大的最大 IOPS 基准编号，尤其是在存储系统有可能的情况下，如果存储系统具有从本地副本读取的常见优化，则更是如此。 存储空间直通进行了优化。

**如果只使用读取操作来度量，则群集提供 13798674 IOPS。**

![13.7 m IOPS 记录屏幕快照](media/deploy-pmem/iops-record.png)

如果你密切观看视频，你会注意到，甚至会有更多的 jaw。 即使在超过13.7 的 IOPS，Windows 中的文件系统也报告的延迟始终小于40μs！ （这是毫秒数的符号，一秒的秒。）此速度比典型的所有闪存供应商骄傲公布的速度要快得多。

同时，Windows Server 2019 和 Intel® Optane 中的存储空间直通™ DC 持久性内存提供了突破性的性能。 这种业界领先的13.7 的 HCI 基准，超过了可预测性和极低的延迟，这比我们先前业界领先的 6.7 M IOPS 基准更多。 而且，这一次我们只需要12个服务器节点&mdash;比两年前少25%。

![IOPS 收益](media/deploy-pmem/iops-gains.png)

测试硬件是一个12服务器群集，它配置为使用三向镜像和分隔的 ReFS 卷、 **12** x INTEL® S2600WFT、 **384 GiB** memory、2 x 28 核心 "CASCADELAKE"、 **1.5 TB** Intel® Optane™ DC 永久性内存作为缓存、 **32 TB** NVME （4 x 8 TB Intel® DC P4510）作为容量， **2** x Mellanox ConnectX-4 25 Gbps。

下表显示了完整的性能数字。  

| 测                   | 性能         |
|-----------------------------|---------------------|
| 4K 100% 随机读取         | 13800000 IOPS   |
| 4K 90/10% 随机读/写 | 9450000 IOPS   |
| 2 MB 顺序读取         | 549 GB/秒的吞吐量 |

### <a name="supported-hardware"></a>支持的硬件

下表显示了 Windows Server 2019 和 Windows Server 2016 支持的永久性内存硬件。  

| 永久性内存技术                                      | WIN ENT LTSB 2016 Finnish 64 Bits | Windows Server Standard 2012 R2 |
|-------------------------------------------------------------------|--------------------------|--------------------------|
| 在持续模式下**的 nvdimm-n**                                  | 支持                | 支持                |
| Intel Optane 在应用程序直接模式下**™ DC 永久性内存**             | 不受支持            | 支持                |
| **Intel Optane™ DC 永久性内存（** 内存模式） | 支持            | 支持                |

> [!NOTE]  
> Intel Optane 支持*内存*（可变）模式和*应用直接*（持久）模式。
   
> [!NOTE]  
> 当你重新启动具有多个 Intel® Optane 的系统时™应用直接模式中划分为多个命名空间的 PMem 模块，你可能会失去对部分或全部相关逻辑存储磁盘的访问权限。 此问题发生在早于版本1903的 Windows Server 2019 版本上。
>   
> 由于 PMem 模块已训练或在系统启动时失败，导致此访问权限丢失。 在这种情况下，系统上任何 PMem 模块上的所有存储命名空间都将失败，包括不以物理方式映射到故障模块的命名空间。
>   
> 若要还原对所有命名空间的访问，请替换出现故障的模块。
>   
> 如果某个模块在 Windows Server 2019 版本1903或更高版本上失败，则你将失去实际映射到受影响的模块的命名空间的访问权限。 其他命名空间不受影响。

现在，让我们深入了解如何配置永久性内存。

## <a name="interleaved-sets"></a>交错集

### <a name="understanding-interleaved-sets"></a>了解交错集

请记住，NVDIMM 位于标准 DIMM （内存）槽，使数据更接近处理器。 此配置可减少延迟并提高提取性能。 若要进一步增加吞吐量，请使用两个或更多 NVDIMMs 创建一个用于条带读/写操作的 n 向交错集。 最常见的配置是双向或四向交叉。 交错集还会使多个永久性内存设备在 Windows Server 中显示为一个逻辑磁盘。 可以使用 Windows PowerShell **PmemDisk** cmdlet 查看此类逻辑磁盘的配置，如下所示：

```PowerShell
Get-PmemDisk

DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Healthy      None          True         {20, 120}         0
3          252 GB Healthy      None          True         {1020, 1120}      0
```

我们可以看到逻辑 PMem 磁盘 #2 使用物理设备 Id20 和 Id120，逻辑 PMem 磁盘 #3 使用物理设备 Id1020 和 Id1120。  

若要检索有关逻辑驱动器使用的交错集的详细信息，请运行**PmemPhysicalDevice** cmdlet：

```PowerShell
(Get-PmemDisk)[0] | Get-PmemPhysicalDevice

DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------------
20       Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_C1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
```

### <a name="configuring-interleaved-sets"></a>配置交错集

若要配置交错集，请首先查看未分配给系统中的逻辑 PMem 磁盘的所有永久性内存区域。 为此，请运行以下 PowerShell cmdlet：

```PowerShell
Get-PmemUnusedRegion

RegionId TotalSizeInBytes DeviceId
-------- ---------------- --------
       1     270582939648 {20, 120}
       3     270582939648 {1020, 1120}
```

若要查看系统中的所有 PMem 设备信息（包括设备类型、位置、运行状况和操作状态等），请在本地服务器上运行以下 cmdlet：

```PowerShell
Get-PmemPhysicalDevice

DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile
                                                                                                                      memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------
1020     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_C1     102005310        126 GB                 0 GB
1120     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_F1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
20       Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_C1     102005310        126 GB                 0 GB
```

由于我们有一个可用的未使用的 PMem 区域，因此，我们可以创建新的持久性内存磁盘。 可以通过运行以下 cmdlet，使用未使用的区域创建多个持久性内存磁盘：

```PowerShell
Get-PmemUnusedRegion | New-PmemDisk
Creating new persistent memory disk. This may take a few moments.
```

完成此操作后，可以通过运行以下内容来查看结果：

```PowerShell
Get-PmemDisk

DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Healthy      None          True         {20, 120}         0
3          252 GB Healthy      None          True         {1020, 1120}      0
```

值得注意的是，我们可以运行**PhysicalDisk |其中，媒体存储-Eq SCM** ，而不是**PmemDisk**以获得相同的结果。 新创建的 PMem 磁盘与 PowerShell 中和 Windows 管理中心的驱动器具有一对一的对应关系。

### <a name="using-persistent-memory-for-cache-or-capacity"></a>使用持久性内存作为缓存或容量

Windows Server 2019 上的存储空间直通支持使用持久性内存作为缓存或容量驱动器。 有关如何设置缓存和容量驱动器的详细信息，请参阅[了解存储空间直通中的缓存](understand-the-cache.md)。

## <a name="creating-a-dax-volume"></a>创建 DAX 卷

### <a name="understanding-dax"></a>了解 DAX

可以通过两种方法来访问永久性内存。 它们是：

1. **直接访问（DAX）** ，其操作类似于内存来获得最低延迟。 应用直接修改持久性内存，绕过堆栈。 请注意，只能将 DAX 与 NTFS 结合使用。
1. **阻止访问**，它的操作类似于应用程序兼容性的存储。 在此配置中，数据流经堆栈。 可以将此配置与 NTFS 和 ReFS 结合使用。

下图显示了 DAX 配置的示例：

![DAX 堆栈](media/deploy-pmem/dax.png)

### <a name="configuring-dax"></a>配置 DAX

必须使用 PowerShell cmdlet 在永久性内存磁盘上创建 DAX 卷。 通过使用 **-IsDax**开关，我们可以将卷格式化为启用 DAX。

```PowerShell
Format-Volume -IsDax:$true
```

以下代码片段可帮助你在永久性内存磁盘上创建 DAX 卷。

```PowerShell
# Here we use the first pmem disk to create the volume as an example
$disk = (Get-PmemDisk)[0] | Get-PhysicalDisk | Get-Disk
# Initialize the disk to GPT if it is not initialized
If ($disk.partitionstyle -eq "RAW") {$disk | Initialize-Disk -PartitionStyle GPT}
# Create a partition with drive letter 'S' (can use any available drive letter)
$disk | New-Partition -DriveLetter S -UseMaximumSize


   DiskPath: \\?\scmld#ven_8980&dev_097a&subsys_89804151&rev_0018#3&1b1819f6&0&03018089fb63494db728d8418b3cbbf549997891#{53f56307-b6
bf-11d0-94f2-00a0c91efb8b}

PartitionNumber  DriveLetter Offset                                               Size Type
---------------  ----------- ------                                               ---- ----
2                S           16777216                                        251.98 GB Basic

# Format the volume with drive letter 'S' to DAX Volume
Format-Volume -FileSystem NTFS -IsDax:$true -DriveLetter S

DriveLetter FriendlyName FileSystemType DriveType HealthStatus OperationalStatus SizeRemaining      Size
----------- ------------ -------------- --------- ------------ ----------------- -------------      ----
S                        NTFS           Fixed     Healthy      OK                    251.91 GB 251.98 GB

# Verify the volume is DAX enabled
Get-Partition -DriveLetter S | fl


UniqueId             : {00000000-0000-0000-0000-000100000000}SCMLD\VEN_8980&DEV_097A&SUBSYS_89804151&REV_0018\3&1B1819F6&0&03018089F
                       B63494DB728D8418B3CBBF549997891:WIN-8KGI228ULGA
AccessPaths          : {S:\, \\?\Volume{cf468ffa-ae17-4139-a575-717547d4df09}\}
DiskNumber           : 2
DiskPath             : \\?\scmld#ven_8980&dev_097a&subsys_89804151&rev_0018#3&1b1819f6&0&03018089fb63494db728d8418b3cbbf549997891#{5
                       3f56307-b6bf-11d0-94f2-00a0c91efb8b}
DriveLetter          : S
Guid                 : {cf468ffa-ae17-4139-a575-717547d4df09}
IsActive             : False
IsBoot               : False
IsHidden             : False
IsOffline            : False
IsReadOnly           : False
IsShadowCopy         : False
IsDAX                : True                   # <- True: DAX enabled
IsSystem             : False
NoDefaultDriveLetter : False
Offset               : 16777216
OperationalStatus    : Online
PartitionNumber      : 2
Size                 : 251.98 GB
Type                 : Basic
```

## <a name="monitoring-health"></a>监视运行状况

使用持久性内存时，监视体验有一些不同之处：

- 永久性内存不会创建物理磁盘性能计数器，因此不会在 Windows 管理中心的图表上看到它。
- 永久性内存不会创建 Storport 505 数据，因此不会获得主动离群检测。

除此之外，监视体验与其他任何物理磁盘相同。 可以通过运行以下 cmdlet 来查询永久性内存磁盘的运行状况：

```PowerShell
Get-PmemDisk

DiskNumber Size   HealthStatus AtomicityType CanBeRemoved PhysicalDeviceIds UnsafeShutdownCount
---------- ----   ------------ ------------- ------------ ----------------- -------------------
2          252 GB Unhealthy    None          True         {20, 120}         2
3          252 GB Healthy      None          True         {1020, 1120}      0

Get-PmemDisk | Get-PhysicalDisk | select SerialNumber, HealthStatus, OperationalStatus, OperationalDetails

SerialNumber               HealthStatus OperationalStatus  OperationalDetails
------------               ------------ ------------------ ------------------
802c-01-1602-117cb5fc      Healthy      OK
802c-01-1602-117cb64f      Warning      Predictive Failure {Threshold Exceeded,NVDIMM_N Error}
```

**HealthStatus**显示 PMem 磁盘是否正常。  

**UnsafeshutdownCount**值跟踪可能导致此逻辑磁盘上的数据丢失的关闭次数。 这是此磁盘上所有基础 PMem 设备的不安全关闭计数的总和。 有关运行状况状态的详细信息，请使用**PmemPhysicalDevice** cmdlet 查找信息，如**OperationalStatus**。

```PowerShell
Get-PmemPhysicalDevice

DeviceId DeviceType           HealthStatus OperationalStatus PhysicalLocation FirmwareRevision Persistent memory size Volatile memory size
-------- ----------           ------------ ----------------- ---------------- ---------------- ---------------------- --------------------
1020     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_C1     102005310        126 GB                 0 GB
1120     Intel INVDIMM device Healthy      {Ok}              CPU2_DIMM_F1     102005310        126 GB                 0 GB
120      Intel INVDIMM device Healthy      {Ok}              CPU1_DIMM_F1     102005310        126 GB                 0 GB
20       Intel INVDIMM device Unhealthy    {HardwareError}   CPU1_DIMM_C1     102005310        126 GB                 0 GB
```

此 cmdlet 显示哪些永久性内存设备处于不正常状态。 不正常的设备（**DeviceId** 20）与上一示例中的大小写匹配。 BIOS 中的**PhysicalLocation**可帮助确定哪些永久性内存设备处于错误状态。

## <a name="replacing-persistent-memory"></a>替换持久性内存

本文介绍如何查看持久内存的运行状况状态。 如果必须替换出现故障的模块，则必须重新设置 PMem 磁盘（请参阅前面介绍的步骤）。

进行故障排除时，可能需要使用**PmemDisk**。 此 cmdlet 将删除特定的持久性内存磁盘。 可以通过运行以下 cmdlet 来删除所有当前 PMem 磁盘：

```PowerShell
Get-PmemDisk | Remove-PmemDisk

cmdlet Remove-PmemDisk at command pipeline position 1
Supply values for the following parameters:
DiskNumber: 2

This will remove the persistent memory disk(s) from the system and will result in data loss.
Remove the persistent memory disk(s)?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
Removing the persistent memory disk. This may take a few moments.
```

> [!IMPORTANT]  
> 删除持久性内存磁盘会导致该磁盘上的数据丢失。

可能需要的另一个 cmdlet 为**PmemPhysicalDevice**。 此 cmdlet 将初始化物理持久性内存设备上的标签存储区域，并可以清除 PMem 设备上已损坏的标签存储信息。

```PowerShell
Get-PmemPhysicalDevice | Initialize-PmemPhysicalDevice

This will initialize the label storage area on the physical persistent memory device(s) and will result in data loss.
Initializes the physical persistent memory device(s)?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
Initializing the physical persistent memory device. This may take a few moments.
Initializing the physical persistent memory device. This may take a few moments.
Initializing the physical persistent memory device. This may take a few moments.
Initializing the physical persistent memory device. This may take a few moments.
```

> [!IMPORTANT]  
> **PmemPhysicalDevice**在永久性内存中导致数据丢失。 使用它作为解决持久内存相关问题的最后手段。

## <a name="see-also"></a>另请参阅

- [存储空间直通概述](storage-spaces-direct-overview.md)
- [Windows 中的存储类内存（NVDIMM-N）运行状况管理](storage-class-memory-health.md)
- [了解缓存](understand-the-cache.md)
