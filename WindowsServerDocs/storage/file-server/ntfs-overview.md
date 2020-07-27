---
title: NTFS 概述
description: 解释 NTFS 是什么。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 06/17/2019
ms.localizationpriority: medium
ms.openlocfilehash: a390521cbd4d5dd676662d3dc41062792f1fa945
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965139"
---
# <a name="ntfs-overview"></a>NTFS 概述

>适用于：Windows 10、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

NTFS 是最新版 Windows 和 Windows Server 的主文件系统，提供一整套功能（包括安全描述符、加密、磁盘配额以及丰富的元数据），它可以配合群集共享卷 (CSV) 使用，用于提供持续可用的卷，这种卷可以从故障转移群集的多个节点同时访问。

若要详细了解 Windows Server 2012 R2 中 NTFS 的新增功能和更改的功能，请参阅 [NTFS 中的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn466520(v%3dws.11))。 有关其他功能信息，请参阅本主题的[附加信息](#additional-information)部分。 若要了解有关较新的复原文件系统 (ReFS) 的详细信息，请参阅[复原文件系统 (ReFS) 概述](../refs/refs-overview.md)。

## <a name="practical-applications"></a>实际的应用程序

### <a name="increased-reliability"></a>更高的可靠性

计算机在发生系统故障后重启时，NTFS 将使用其日志文件和检查点信息来还原文件系统的一致性。 出现坏扇区错误后，NTFS 会动态重新映射包含坏扇区的群集，为数据分配一个新的群集，将原始群集标记为“坏”，并不再使用旧的群集。 例如，在服务器出现故障后，NTFS 可以通过重播其日志文件来恢复数据。

NTFS 在后台持续监视和纠正暂时性损坏问题，而不会使卷脱机（此功能称为[具有自修复功能的 NTFS](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771388(v=ws.10))，在 Windows Server 2008 中引入）。 对于更大的损坏问题，在 Windows Server 2012 及更高版本中，Chkdsk 实用程序会在卷处于联机状态时扫描并分析驱动器，将脱机时间限制为还原卷上数据一致性所需的时间。 将 NTFS 与群集共享卷配合使用时，无需停机。 有关详细信息，请参阅 [NTFS 运行状况和 Chkdsk](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831536(v%3dws.11))。

### <a name="increased-security"></a>增加的安全性

- **文件和文件夹的基于访问控制列表 (ACL) 的安全性** - 借助 NTFS，可以对文件或文件夹设置权限，指定要限制或允许其访问权限的组和用户，以及选择“访问类型”。

- **支持 BitLocker 驱动器加密** - BitLocker 驱动器加密为存储在 NTFS 卷上的重要系统信息和其他数据提供额外的安全性。 从 Windows Server 2012 R2 和 Windows 8.1 开始，BitLocker 通过受信任的平台模块 (TPM)（支持连接待机，以前仅在 Windows RT 设备上可用）为基于 x86 和 x64 计算机上的设备加密提供支持。 设备加密有助于保护 Windows 计算机上的数据，它可以帮助阻止恶意用户访问它们用于发现用户密码的系统文件，或阻止它们通过物理方式从电脑中移除驱动器并将它安装在另一台电脑中来访问驱动器。 有关详细信息，请参阅 [BitLocker 中的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn306081(v%3dws.11))。

- **支持大容量** - NTFS 支持容量高达 256 TB 的卷。 支持的卷大小受群集大小和群集数量的影响。 在具有（2<sup>32</sup> - 1）个群集（NTFS 支持的最大群集数量）的情况下，支持以下卷和文件大小。

  |群集大小|最大卷|最大文件|
  |---|---|---|
  |4 KB（默认大小）|16 TB|16 TB|
  |8 KB|32 TB|32 TB|
  |16 KB|64 TB|64 TB|
  |32 KB|128 TB|128 TB|
  |64 KB（最大大小）|256 TB|256 TB|

>[!IMPORTANT]
>服务和应用可能会对文件和卷大小施加额外限制。 例如，如果你使用的是以前版本的功能或利用卷影复制服务 (VSS) 快照（而不是使用 SAN 或 RAID 存储模块）的备份应用，则卷大小限制为 64 TB。 但是，你可能需要使用较小的卷大小，具体取决于你的工作负载和存储性能。

### <a name="formatting-requirements-for-large-files"></a>大型文件的格式要求

若要允许对大型 .vhdx 文件进行适当的扩展，有新的建议用于格式化卷。 若要格式化用于重复数据删除或承载大型文件（如大于 1 TB的 .vhdx 文件）的卷，请通过以下参数使用 Windows PowerShell 中的 Format-Volume cmdlet  。

|参数|说明|
|---|---|
|-AllocationUnitSize 64KB|设置 64 KB NTFS 分配单元大小。|
|-UseLargeFRS|启用对大型文件记录段 (FRS) 的支持。 增加卷上每个文件允许的区数需要此参数。 对于大型 FRS 记录，限制会从约 150 万个区增加到约 600 万个区。|

例如，以下 cmdlet 将驱动器 D 格式化为 NTFS 卷，同时启用了 FRS 并将分配单元大小设置为 64 KB。

```PowerShell
Format-Volume -DriveLetter D -FileSystem NTFS -AllocationUnitSize 64KB -UseLargeFRS
```

你还可以使用 format 命令  。 在系统命令提示符处，输入以下命令，其中 /L 格式化大型 FRS 卷，/A:64k 设置 64 KB 分配单元大小   ：

```PowerShell
format /L /A:64k
```

### <a name="maximum-file-name-and-path"></a>最大文件名称和路径

NTFS 支持长文件名和扩展长度路径，并且具有以下最大值：

- **支持长文件名，具有后向兼容性** - 借助 NTFS，可使用较长的文件名，在磁盘上存储 8.3 别名（采用 Unicode 编码），以提供与文件系统的兼容性。该文件系统可对文件名称和扩展施加 8.3 限制。 如果需要（出于性能方面的原因），可以在 Windows Server 2008 R2、Windows 8 和更新版本的 Windows 操作系统中有选择地禁用各个 NTFS 卷上的 8.3 别名。
  在 Windows Server 2008 R2 及更高版本系统中，如果使用操作系统格式化卷，则默认禁用短名称。 为了实现应用程序兼容性，系统卷上仍启用了短名称。

- **支持扩展长度路径** - 许多 Windows API 函数的 Unicode 版本允许长度约为 32,767 个字符的扩展长度路径，该长度超过 MAX\_PATH 设置定义的 260 个字符的路径限制。 有关详细的文件名和路径格式要求，以及实现扩展长度路径的指南，请参阅[命名文件、路径和命名空间](/windows/win32/fileio/naming-a-file)。

- **群集存储** - 在故障转移群集中使用时，NTFS 支持连续可用的卷。当与集群共享卷(CSV)文件系统结合使用时，多个群集节点可以同时访问这些卷。 有关详细信息，请参阅[在故障转移群集中使用群集共享卷](../../failover-clustering/failover-cluster-csvs.md)。

### <a name="flexible-allocation-of-capacity"></a>灵活分配容量

如果卷上的空间有限，NTFS 提供以下方法来处理服务器的存储容量：

- 使用磁盘配额跟踪和控制各个用户的 NTFS 卷上的磁盘空间使用情况。
- 使用文件系统压缩来最大程度地提高可存储的数据量。
- 通过从同一磁盘或其他磁盘添加未分配的空间来增加 NTFS 卷的大小。
- 如果用完了驱动器号，或者需要创建可从现有文件夹访问的额外空间，请在本地 NTFS 卷上的任何空文件夹中装载卷。

## <a name="additional-information"></a>附加信息

- [ReFS 和 NTFS 的群集大小建议](https://techcommunity.microsoft.com/t5/Storage-at-Microsoft/Cluster-size-recommendations-for-ReFS-and-NTFS/ba-p/425960)
- [复原文件系统 (ReFS) 概述](../refs/refs-overview.md)
- [NTFS 中的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn466520(v%3dws.11)) (Windows Server 2012 R2)
- [NTFS 中的新增功能](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff383236(v=ws.10))（Windows Server 2008 R2、Windows 7）
- [NTFS 运行状况和 Chkdsk](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831536(v%3dws.11))
- [具有自修复功能的 NTFS](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771388(v=ws.10))（在 Windows Server 2008 中引入）
- [事务性 NTFS](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc730726(v%3dws.10))（在 Windows Server 2008 中引入）
- [Windows Server 中的存储](../storage.yml)
