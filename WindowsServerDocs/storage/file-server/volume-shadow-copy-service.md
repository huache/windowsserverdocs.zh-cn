---
title: 卷影复制服务
ms.date: 01/30/2019
ms.prod: windows-server
ms.technology: storage
author: JasonGerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: f2e8d3bfb5ef907ffb522b5b7be31d1def3001c8
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75949681"
---
# <a name="volume-shadow-copy-service"></a>卷影复制服务

适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2008 R2、Windows Server 2008、Windows 10、Windows 8.1、Windows 8、Windows 7

由于以下问题，备份和还原关键业务数据可能非常复杂：

  - 当生成数据的应用程序仍在运行时，通常需要备份数据。 这意味着，某些数据文件可能处于打开状态，或者可能处于不一致的状态。  
      
  - 如果数据集很大，则很难一次备份所有数据集。  
      

正确执行备份和还原操作需要备份应用程序、要备份的业务线应用程序以及存储管理硬件和软件之间密切协调。 卷影复制服务 (VSS) 是在 Windows Server®2003 中引入的，它有助于这些组件之间的对话，以便更好地协同工作。 当所有组件都支持 VSS 时，你可以使用它们来备份应用程序数据，无需将应用程序脱机。

VSS 协调为要备份的数据创建一致的卷影副本（也称为快照或时间点副本）所需的操作。 卷影副本可以按原样使用，也可以在以下情况下使用：

  - 你需要备份应用程序数据和系统状态信息，包括将数据存档到其他硬盘驱动器、磁带或其他可移动媒体。  
      
  - 你正在执行数据挖掘。  
      
  - 你正在执行磁盘到磁盘备份。  
      
  - 你需要通过将数据恢复到原始 LUN 或全新的 LUN（替换出现故障的原始 LUN）来快速恢复数据丢失。  
      

使用 VSS 的 Windows 功能和应用程序包括：

  - [Windows Server 备份](https://go.microsoft.com/fwlink/?linkid=180891) (https://go.microsoft.com/fwlink/?LinkId=180891)  
      
  - [共享文件夹的卷影副本](https://go.microsoft.com/fwlink/?linkid=142874) (https://go.microsoft.com/fwlink/?LinkId=142874)  
      
  - [System Center Data Protection Manager](https://go.microsoft.com/fwlink/?linkid=180892) (https://go.microsoft.com/fwlink/?LinkId=180892)  
      
  - [系统还原](https://go.microsoft.com/fwlink/?linkid=180893) (https://go.microsoft.com/fwlink/?LinkId=180893)  
      

## <a name="how-volume-shadow-copy-service-works"></a>卷影复制服务的工作原理

完整的 VSS 解决方案需要以下所有基本部分：

VSS 服务   Windows 操作系统的一部分，可确保其他组件能够正确地相互通信并协同工作  。

VSS 请求程序   请求实际创建卷影副本（或导入或删除卷影副本等其他高级操作）的软件  。 通常，这是备份应用程序。 Windows Server 备份实用程序和 System Center Data Protection Manager 应用程序是 VSS 请求程序。 非 Microsoft® VSS 请求程序几乎包括所有在 Windows 上运行的备份软件。

VSS 编写程序   保证我们要备份的数据集保持一致的组件  。 这通常作为业务线应用程序（如 SQL Server® 或 Exchange Server）的一部分提供。 各种 Windows 组件（如注册表）的 VSS 编写程序都包含在 Windows 操作系统中。 许多 Windows 应用程序中都包含非 Microsoft VSS 编写程序，这些编写程序在备份过程中需要确保数据的一致性。

VSS 提供程序   创建和维护卷影副本的组件  。 这可能会在软件或硬件中发生。 Windows 操作系统包括使用写入时复制的 VSS 提供程序。 如果使用存储区域网络 (SAN)，则必须为 SAN 安装 VSS 硬件提供程序（如果已提供）。 硬件提供程序从主机操作系统中卸载创建和维护卷影副本的任务。

下图说明了 VSS 服务如何与请求程序、编写程序和提供程序协调以创建卷的卷影副本。

![](media/volume-shadow-copy-service/Ee923636.94dfb91e-8fc9-47c6-abc6-b96077196741(WS.10).jpg)

图 1   卷影复制服务的架构示意图 

### <a name="how-a-shadow-copy-is-created"></a>如何创建卷影副本

本部分通过列出创建卷影副本所需采取的步骤，将请求程序、编写程序和提供程序的各种角色置于上下文中。 下图显示卷影复制服务如何控制请求程序、编写程序和提供程序的总体协调。

![](media/volume-shadow-copy-service/Ee923636.1c481a14-d6bc-4796-a3ff-8c6e2174749b(WS.10).jpg)

图 2 卷影副本创建过程 

若要创建卷影副本，请求程序、编写程序和提供程序将执行以下操作：

1.  请求程序要求卷影复制服务枚举编写程序，收集编写程序元数据，并准备创建卷影副本。  
      
2.  每个编写程序都会为需要备份的组件和数据存储创建 XML 描述，并将其提供给卷影复制服务。 编写器还定义了用于所有组件的还原方法。 卷影复制服务向请求程序提供编写程序的描述，而请求程序则选择要备份的组件。  
      
3.  卷影复制服务通知所有编写程序准备数据以进行卷影复制。  
      
4.  每个编写程序都会根据需要准备数据，例如完成所有未结束事务、滚动事务日志和刷新缓存。 当数据准备好进行卷影复制时，编写程序将通知卷影复制服务。  
      
5.  卷影复制服务通知编写程序将应用程序写入 I/O 请求暂时冻结几秒钟（仍然可以执行读取 I/O 请求），创建卷的卷影副本需要这几秒的时间。 应用程序冻结的时间不允许超过 60 秒。 卷影复制服务刷新文件系统缓冲区，然后冻结文件系统，从而确保正确记录文件系统元数据，并以一致的顺序写入要进行卷影复制的数据。  
      
6.  卷影复制服务通知提供程序创建卷影副本。 卷影副本创建周期不超过 10 秒，在此期间，对文件系统的所有写入 I/O 请求都将保持冻结状态。  
      
7.  卷影复制服务释放文件系统写入 I/O 请求。  
      
8.  VSS 通知编写程序解除冻结应用程序写入 I/O 请求。 此时，应用程序可以继续将数据写入正在进行卷影复制的磁盘。  
      

> [!NOTE]
> 如果编写程序保持冻结状态的时间超过 60 秒，或者提供程序提交卷影副本的时间超过 10 秒，则会中止创建卷影副本。 
<br>

9. 请求程序可以重试该过程（返回步骤 1）或通知管理员稍后重试。  
      
10. 如果已成功创建卷影副本，则卷影复制服务会将卷影副本的位置信息返回给请求程序。 在某些情况下，卷影副本可以临时作为读写卷使用，以便 VSS 和一个或多个应用程序可以在卷影副本完成之前，更改卷影副本的内容。 VSS 和应用程序进行更改后，卷影副本将变为只读。 此阶段称为自动恢复，用于撤消卷影副本卷上在创建卷影副本之前未完成的任何文件系统或应用程序事务。  
      

### <a name="how-the-provider-creates-a-shadow-copy"></a>提供程序创建卷影副本的方式

硬件或软件卷影复制提供程序使用以下方法之一创建卷影副本：

完整复制   此方法在给定时间点对原始卷进行完整复制（称为“完整复制”或“克隆”）  。 此副本为只读副本。

写入时复制   此方法不复制原始卷  。 相反，它通过复制在给定时间点之后对卷所做的所有更改（已完成的写入 I/O 请求）来进行差异复制。

写入时重定向   此方法不会复制原始卷，也不会在给定时间点后对原始卷进行任何更改  。 相反，它会通过将所有更改重定向到其他卷来进行差异复制。

## <a name="complete-copy"></a>完整复制

通常通过制造“拆分镜像”创建完整的副本，如下所示：

1.  原始卷和卷影副本卷是镜像卷集。  
      
2.  卷影副本卷与原始卷分离。 这会中断镜像连接。  
      

镜像连接断开后，原始卷和卷影副本卷彼此独立。 原始卷继续接受所有更改（写入 I/O 请求），而卷影副本卷在中断时仍是原始数据的准确只读副本。

### <a name="copy-on-write-method"></a>写入时复制方法

在写入时复制方法中，当原始卷发生更改时（但在写入 I/O 请求完成之前），将读取要修改的每个块，然后将其写入该卷的卷影副本存储区域（也称为“差异区域”）。 卷影副本存储区域可以位于同一卷或不同卷上。 这将在更改覆盖原始卷之前保留该卷上数据块的副本。


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>时间</th>
<th>源数据（状态和数据）</th>
<th>卷影副本（状态和数据）</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>T0</p></td>
<td><p>原始数据：1 2 3 4 5</p></td>
<td><p>无副本：-</p></td>
</tr>
<tr class="even">
<td><p>T1</p></td>
<td><p>缓存中的数据已更改：3 到 3'</p></td>
<td><p>已创建的卷影副本（仅限差异）：3</p></td>
</tr>
<tr class="odd">
<td><p>T2</p></td>
<td><p>已覆盖的原始数据：1 2 3' 4 5</p></td>
<td><p>卷影副本上存储的差异和索引：3</p></td>
</tr>
</tbody>
</table>

表 1   创建卷影副本的写入时复制方法 

写入时复制方法是创建卷影副本的快速方法，因为它只复制对数据所做的更改。 可将差异区域中复制的块与原始卷上更改的数据相结合，将卷还原到进行任何更改之前的状态。 如果有很多更改，则写入时复制方法会变得昂贵。

### <a name="redirect-on-write-method"></a>写入时重定向方法

在写入时重定向方法中，每当原始卷收到更改（写入 I/O 请求）时，该更改不会应用于原始卷。 相反，更改将写入另一个卷的卷影副本存储区域。


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>时间</th>
<th>源数据（状态和数据）</th>
<th>卷影副本（状态和数据）</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>T0</p></td>
<td><p>原始数据：1 2 3 4 5</p></td>
<td><p>无副本：-</p></td>
</tr>
<tr class="even">
<td><p>T1</p></td>
<td><p>缓存中的数据已更改：3 到 3'</p></td>
<td><p>已创建的卷影副本（仅限差异）：3'</p></td>
</tr>
<tr class="odd">
<td><p>T2</p></td>
<td><p>原始数据保持不变：1 2 3 4 5</p></td>
<td><p>卷影副本上存储的差异和索引：3'</p></td>
</tr>
</tbody>
</table>

表 2   创建卷影副本的写入时重定向方法 

与写入时复制方法一样，写入时重定向方法是创建卷影副本的快速方法，因为它只复制对数据所做的更改。 差异区域中复制的块可以与原始卷上未更改的数据相结合，以创建完整、最新的数据副本。 如果有很多读取 I/O 请求，则写入时重定向方法可能会变得昂贵。

## <a name="shadow-copy-providers"></a>卷影复制提供程序

卷影复制提供程序有两种类型：基于硬件的提供程序和基于软件的提供程序。 还有一个系统提供程序，它是内置在 Windows 操作系统中的软件提供程序。

### <a name="hardware-based-providers"></a>基于硬件的提供程序

基于硬件的卷影复制提供程序通过与硬件存储适配器或控制器协同工作，充当卷影复制服务和硬件级别之间的接口。 创建和维护卷影副本的工作由存储阵列执行。

硬件提供程序始终采用整个 LUN 的卷影副本，但卷影复制服务只公开所请求的卷的卷影副本。

基于硬件的卷影复制提供程序利用卷影复制服务功能定义时间点、允许数据同步、管理卷影副本，并提供备份应用程序的通用接口。 但卷影复制服务不指定基于硬件的提供程序生成和维护卷影复本的基础机制。

### <a name="software-based-providers"></a>基于软件的提供程序

基于软件的卷影复制提供程序通常拦截并处理文件系统和卷管理器软件之间软件层中的读写 I/O 请求。

这些提供程序作为用户模式 DLL 组件和至少一个内核模式设备驱动程序（通常是存储筛选器驱动程序）实现。 与基于硬件的提供程序不同，基于软件的提供程序在软件级别（而不是硬件级别）创建卷影副本。

基于软件的卷影复制提供程序必须通过访问在卷影副本创建时间之前可用于重新创建卷状态的数据集来维护卷的“时间点”视图。 示例是系统提供程序的写入时复制技术。 但卷影复制服务对基于软件的提供程序用于创建和维护卷影副本的技术没有任何限制。

与基于硬件的提供程序相比，软件提供程序适用于范围更广的存储平台，并且它应同样适用于基本磁盘或逻辑卷。 （逻辑卷是通过合并两个或多个磁盘的空闲空间而创建的卷。）与硬件卷影副本不同，软件提供程序使用操作系统资源来维护卷影副本。

有关基本磁盘的详细信息，请参阅 TechNet 上的[什么是基本磁盘和卷？](https://go.microsoft.com/fwlink/?linkid=180894) (https://go.microsoft.com/fwlink/?LinkId=180894) 。

### <a name="system-provider"></a>系统提供程序

Windows 操作系统中提供了一个卷影复制提供程序，即系统提供程序。 尽管 Windows 中提供了默认的提供程序，但其他供应商可以随意提供针对其存储硬件和软件应用程序优化的实现。

为了维护卷影副本中包含的卷的“时间点”视图，系统提供程序使用了写入时复制技术。 自开始创建卷影副本以来，卷上已修改的块的副本存储在卷影副本存储区域中。

系统提供程序可以公开可正常写入和读取的生产卷。 当需要卷影副本时，它会按照逻辑将差异应用于生产卷上的数据，以公开完整的卷影副本。

对于系统提供程序，卷影副本存储区域必须位于 NTFS 卷上。 要进行卷影复制的卷不需要是 NTFS 卷，但系统上必须至少装载一个 NTFS 卷。

组成系统提供程序的组件文件是 swprv.dll 和 volsnap.sys。

### <a name="in-box-vss-writers"></a>内置 VSS 编写程序

Windows 操作系统包含一组 VSS 编写程序，这些编写程序负责枚举各种 Windows 功能所需的数据。

有关这些编写程序的详细信息，请参阅以下 Microsoft 网站：

  - [内置 VSS 编写程序](https://go.microsoft.com/fwlink/?linkid=180895) (https://go.microsoft.com/fwlink/?LinkId=180895)  
      
  - [Windows Server 2008 和 Windows Vista SP1 的内置 VSS 编写程序](https://go.microsoft.com/fwlink/?linkid=180896) (https://go.microsoft.com/fwlink/?LinkId=180896)  
      
  - [Windows Server 2008 R2 和 Windows 7 的内置 VSS 编写程序](https://go.microsoft.com/fwlink/?linkid=180897) (https://go.microsoft.com/fwlink/?LinkId=180897)  
      

## <a name="how-shadow-copies-are-used"></a>如何使用卷影副本

除了备份应用程序数据和系统状态信息外，还可以使用卷影副本实现多种目的，包括：

  - 还原 LUN（LUN 重新同步和 LUN 交换）  
      
  - 还原单个文件（共享文件夹的卷影副本）  
      
  - 使用可传输卷影副本进行数据挖掘  
      

### <a name="restoring-luns-lun-resynchronization-and-lun-swapping"></a>还原 LUN（LUN 重新同步和 LUN 交换）

在 Windows Server 2008 R2 和 Windows 7 中，VSS 请求程序可以使用名为 LUN 重新同步（或“LUN 重新同步”）的硬件卷影复制提供程序功能。 这是一种快速恢复方案，应用程序管理员利用该方案能够将数据从卷影副本还原到原始 LUN 或新 LUN。

卷影副本可以是完整克隆或差异卷影副本。 在这两种情况下，在重新同步操作结束时，目标 LUN 将具有与卷影副本 LUN 相同的内容。 在重新同步操作期间，阵列执行从卷影副本到目标 LUN 的块级复制。


> [!NOTE]
> 卷影副本必须是可传输的硬件卷影副本。 
<br>


大多数阵列允许在重新同步操作开始后不久继续生产 I/O 操作。 重新同步操作正在进行时，读取请求将重定向到卷影副本 LUN，写入请求将重定向到目标 LUN。 这允许阵列恢复非常大的数据集，并在几秒钟内继续进行正常操作。

LUN 重新同步不同于 LUN 交换。 LUN 交换是自 Windows Server 2003 SP1 以来 VSS 支持的一种快速恢复方案。 在 LUN 交换中，会导入卷影副本，然后将其转换为读写卷。 转换是一种不可逆的操作，此后无法使用 VSS API 控制卷和基础 LUN。 以下列表描述了如何将 LUN 重新同步与 LUN 交换进行比较：

  - 在 LUN 重新同步中，卷影副本不会被更改，因此可以多次使用。 在 LUN 交换中，卷影副本只能用于一次恢复。 对于安全意识很高的管理员来说，这一点很重要。 使用 LUN 重新同步时，如果首次出现问题，请求程序可以重试整个还原操作。  
      
  - 在 LUN 交换结束时，卷影复本 LUN 用于生产 I/O 请求。 因此，卷影复本 LUN 必须使用与原始生产 LUN 相同的存储质量，以确保恢复操作后性能不会受到影响。 如果改为使用 LUN 重新同步，则硬件提供程序可以在成本低于生产质量存储的存储上维护卷影副本。  
      
  - 如果目标 LUN 不可用并且需要重新创建，则 LUN 交换可能更经济，因为它不需要目标 LUN。  
      


> [!WARNING]
> 列出的所有操作都是 LUN 级别的操作。 如果尝试使用 LUN 重新同步来恢复特定卷，则会无意中还原共享该 LUN 的所有其他卷。 
<br>


### <a name="restoring-individual-files-shadow-copies-for-shared-folders"></a>还原单个文件（共享文件夹的卷影副本）

共享文件夹的卷影副本使用卷影复制服务提供位于共享网络资源（如文件服务器）上的文件的时间点副本。 使用共享文件夹的卷影副本，用户可以快速恢复存储在网络上的已删除或更改的文件。 因为无需管理员帮助也可以执行此操作，共享文件夹的卷影副本可以提高生产效率并降低管理成本。

有关共享文件夹的卷影副本的详细信息，请参阅 TechNet 上的[共享文件夹的卷影副本](https://go.microsoft.com/fwlink/?linkid=180898) (https://go.microsoft.com/fwlink/?LinkId=180898) 。

### <a name="data-mining-by-using-transportable-shadow-copies"></a>使用可传输卷影副本进行数据挖掘

使用可与卷影复制服务配合使用的硬件提供程序，可以创建可传输的卷影副本，以便将其导入到同一子系统（例如 SAN）中的服务器上。 这些卷影副本可用于为具有只读数据的生产或测试安装设定种子以进行数据挖掘。

使用卷影复制服务和具有硬件提供程序（设计用于卷影复制服务）的存储阵列，可以在一台服务器上创建源数据卷的卷影副本，然后将卷影副本导入到另一台服务器（或返回到同一台服务器）。 此过程在数分钟内完成，而不考虑数据的大小。 传输过程通过一系列步骤实现的，这些步骤使用支持可传输卷影副本的卷影副本请求程序（存储管理应用程序）。

## <a name="to-transport-a-shadow-copy"></a>传输卷影副本

1.  在服务器上创建源数据的可传输卷影副本。

2.  将卷影副本导入连接到 SAN 的服务器（可以导入到其他服务器或同一服务器）。

3.  数据现已准备就绪，可供使用。

![](media/volume-shadow-copy-service/Ee923636.633752e0-92f6-49a7-9348-f451b1dc0ed7(WS.10).jpg)

图 3   在两个服务器之间创建和传输卷影副本 


> [!NOTE]
> 在 Windows Server 2003 上创建的可传输卷影副本无法导入运行 Windows Server 2008 或 Windows Server 2008 R2 的服务器。 在 Windows Server 2008 或 Windows Server 2008 R2 上创建的可传输卷影副本无法导入运行 Windows Server 2003 的服务器。 但是，在 Windows Server 2008 上创建的卷影副本可以导入到运行 Windows Server 2008 R2 的服务器上，反之亦然。 
<br>


卷影副本是只读的。 如果要将卷影副本转换为读/写 LUN，除了卷影副本服务之外，还可以使用基于虚拟磁盘服务的存储管理应用程序（包括一些请求程序）。 通过使用此应用程序，可以从卷影复制服务管理中删除卷影副本并将其转换为读/写 LUN。

卷影复制服务传输是在运行 Windows Server 2003 企业版、Windows Server 2003 数据中心版、Windows Server 2008 或 Windows Server 2008 R2 的计算机上的高级解决方案。 仅当存储阵列上存在硬件提供程序时，它才有效。 卷影复制传输可用于多种目的，包括磁带备份、数据挖掘和测试。

## <a name="frequently-asked-questions"></a>常见问题

此常见问题解答回答了有关系统管理员的卷影复制服务 (VSS) 的问题。 有关 VSS 应用程序编程接口的信息，请参阅 Windows 开发中心库中的[卷影复制服务](https://go.microsoft.com/fwlink/?linkid=180899) (https://go.microsoft.com/fwlink/?LinkId=180899) 。

### <a name="when-was-volume-shadow-copy-service-introduced-on-which-windows-operating-system-versions-is-it-available"></a>卷影复制服务是何时引入的？ 它在哪些 Windows 操作系统版本上可用？

VSS 在 Windows XP 中引入。 它在 Windows XP、Windows Server 2003、Windows Vista®、Windows Server 2008、Windows 7 和 Windows Server 2008 R2 上可用。

### <a name="what-is-the-difference-between-a-shadow-copy-and-a-backup"></a>卷影副本和备份之间有何区别？

对于硬盘驱动器备份，创建的卷影副本也是备份。 可以从卷影副本复制数据以进行还原，也可以将卷影副本用于快速还原方案，例如，LUN 重新同步或 LUN 交换。

当数据从卷影副本复制到磁带或其他可移动媒体时，存储在该媒体上的内容构成备份。 从卷影副本复制数据后，可以删除卷影副本本身。

### <a name="what-is-the-largest-size-volume-that-volume-shadow-copy-service-supports"></a>卷影复制服务支持的最大容量是多少？

卷影复制服务支持的卷大小高达 64 TB。

### <a name="i-made-a-backup-on-windows-server2008-can-i-restore-it-on-windows-server2008r2"></a>我在 Windows Server 2008 上进行了备份。 能否在 Windows Server 2008 R2 上进行还原？

这取决于所使用的备份软件。 大多数备份程序支持将此方案用于数据备份，但不支持用于系统状态备份。

在这两种版本 Windows 中的一种上创建的卷影副本可用于另一版本的 Windows。

### <a name="i-made-a-backup-on-windows-server2003-can-i-restore-it-on-windows-server2008"></a>我在 Windows Server 2003 上进行了备份。 能否在 Windows Server 2008 上进行还原？

这取决于所使用的备份软件。 如果在 Windows Server 2003 上创建卷影副本，则无法在 Windows Server 2008 上使用。 此外，如果在 Windows Server 2008 上创建卷影副本，则无法在 Windows Server 2003 上将其还原。

### <a name="how-can-i-disable-vss"></a>如何禁用 VSS？

可以使用 Microsoft 管理控制台禁用卷影复制服务。 但是，你不应执行此操作。 禁用 VSS 会对所用的依赖它的任何软件（如系统还原和 Windows Sever 备份）产生不利影响。

有关详细信息，请参阅以下 Microsoft TechNet 网站：

  - [系统还原](https://go.microsoft.com/fwlink/?linkid=157113) (https://go.microsoft.com/fwlink/?LinkID=157113)  
      
  - [Windows Server 备份](https://go.microsoft.com/fwlink/?linkid=180891) (https://go.microsoft.com/fwlink/?LinkID=180891)  
      

### <a name="can-i-exclude-files-from-a-shadow-copy-to-save-space"></a>是否可以从卷影副本中排除文件以节省空间？

VSS 可用于创建整个卷的卷影副本。 临时文件（如页面文件）会自动从卷影副本中忽略以节省空间。

若要从卷影副本中排除特定文件，请使用以下注册表项：**FilesNotToSnapshot**。


> [!NOTE]
> <STRONG>FilesNotToSnapshot</STRONG> 注册表项只供应用程序使用。 尝试使用它的用户将遇到如下所示的限制：
> <br>
> <UL>
> <LI>它无法删除在 Windows Server 上使用以前版本功能创建的卷影副本中的文件。<BR><BR>
> <LI>它无法删除共享文件夹的卷影副本中的文件。<BR><BR>
> <LI>它可以删除使用 <a href="https://docs.microsoft.com/windows-server/administration/windows-commands/diskshadow" data-raw-source="[Diskshadow](https://docs.microsoft.com/windows-server/administration/windows-commands/diskshadow)">Diskshadow</a> 实用程序创建的卷影副本中的文件，但不能删除使用 <a href="https://docs.microsoft.com/windows-server/administration/windows-commands/vssadmin" data-raw-source="[Vssadmin](https://docs.microsoft.com/windows-server/administration/windows-commands/vssadmin)">Vssadmin</a> 实用程序创建的卷影副本中的文件。<BR><BR>
> <LI>系统会尽力从卷影副本中删除文件。 这意味着不能保证它们被删除。<BR><BR></LI></UL>


有关详细信息，请参阅 MSDN 上的[从卷影副本中排除文件](https://go.microsoft.com/fwlink/?linkid=180904) (https://go.microsoft.com/fwlink/?LinkId=180904) 。

### <a name="my-non-microsoft-backup-program-failed-with-a-vss-error-what-can-i-do"></a>我的非 Microsoft 备份程序因 VSS 错误而失败。 我该怎么办？

查看创建备份程序的公司网站的产品支持部分。 可能会有一个产品更新，你可以下载并安装以解决问题。 如果没有，请与公司的产品支持部门联系。

系统管理员可以使用以下 Microsoft TechNet Library 网站上的 VSS 故障排除信息来收集 VSS 相关问题的诊断信息。

有详细信息，请参阅 TechNet 上的 [Volume Shadow Copy Service](https://go.microsoft.com/fwlink/?linkid=180905)（卷影复制服务）(https://go.microsoft.com/fwlink/?LinkId=180905) 。

### <a name="what-is-the-diff-area"></a>什么是“差异区域”？

卷影副本存储区域（或“差异区域”）是存储系统软件提供程序创建的卷影副本数据的位置。

### <a name="where-is-the-diff-area-located"></a>差异区域位于何处？

差异区域可以位于任何本地卷上。 但是，它必须位于有足够空间存储它的 NTFS 卷上。

### <a name="how-is-the-diff-area-location-determined"></a>如何确定差异区域的位置？

按此顺序评估以下条件以确定差异区域位置：

  - 如果卷中已存在卷影副本，则使用该位置。  
      
  - 如果原始卷和卷影复本卷位置之间存在预先配置的手动关联，则使用该位置。  
      
  - 如果前两个条件未提供位置，卷影复制服务将根据可用空闲空间选择位置。 如果正在对多个卷进行卷影复制，卷影复制服务将根据空闲空间的大小按降序创建可能的快照位置列表。 提供的位置数等于要进行卷影复制的卷数。  
      
  - 如果要进行卷影复制的卷是可能的位置之一，则会创建本地关联。 否则将创建与具有最大可用空间的卷的关联。  
      

### <a name="can-vss-create-shadow-copies-of-non-ntfs-volumes"></a>VSS 是否可以创建非 NTFS 卷的卷影副本？

是的。 但是，只能对 NTFS 卷进行永久性卷影复制。 此外，系统上必须至少安装一个 NTFS 卷。

### <a name="whats-the-maximum-number-of-shadow-copies-i-can-create-at-one-time"></a>我可以一次创建的卷影副本的最大数目是多少？

单个卷影副本集中卷影复制的卷的最大数目为 64。 请注意，这与卷影副本的数量不同。

### <a name="whats-the-maximum-number-of-software-shadow-copies-created-by-the-system-provider-that-i-can-maintain-for-a-volume"></a>对于一个卷，我可以维护的系统提供程序创建的软件卷影副本的最大数量是多少？

每个卷的软件卷影副本的最大数量为 512。 但是，默认情况下，你只能维护共享文件夹的卷影副本功能使用的 64 个卷影副本。 若要更改共享文件夹卷影副本功能的限制，请使用以下注册表项：MaxShadowCopies  。

### <a name="how-can-i-control-the-space-that-is-used-for-shadow-copy-storage-space"></a>如何控制用于卷影副本存储空间的空间？

键入 vssadmin resize shadowstorage 命令  。

有关详细信息，请参阅 TechNet 上的 [Vssadmin resize shadowstorage](https://go.microsoft.com/fwlink/?linkid=180906) (https://go.microsoft.com/fwlink/?LinkId=180906) 。

### <a name="what-happens-when-i-run-out-of-space"></a>当空间不足时，会发生什么情况？

将删除卷的卷影副本，从最旧的卷影副本开始。

## <a name="volume-shadow-copy-service-tools"></a>卷影复制服务工具

Windows 操作系统提供了以下用于处理 VSS 的工具：

  - [DiskShadow](https://go.microsoft.com/fwlink/?linkid=180907) (https://go.microsoft.com/fwlink/?LinkId=180907)  
      
  - [VssAdmin](https://go.microsoft.com/fwlink/?linkid=84008) (https://go.microsoft.com/fwlink/?LinkId=84008)  
      

### <a name="diskshadow"></a>DiskShadow

DiskShadow 是一个 VSS 请求程序，可用来管理系统上的所有硬件和软件快照。 DiskShadow 包含如下所示的命令：

  - list  ：列出 VSS 编写程序、VSS 提供程序和卷影副本  
      
  - create  ：创建新的卷影副本  
      
  - import  ：导入可传输的卷影副本  
      
  - expose  ：公开永久性卷影副本（例如驱动器号）  
      
  - revert  ：将卷还原到指定的卷影副本  
      

此工具适用于 IT 专业人员，但开发人员会发现在测试 VSS 编写程序或 VSS 提供程序时它也很有用。

DiskShadow 仅在 Windows Server 操作系统上可用。 它在 Windows 客户端操作系统上不可用。

### <a name="vssadmin"></a>VssAdmin

VssAdmin 用于创建、删除和列出有关卷影副本的信息。 它还可用于调整卷影副本存储区域（“差异区域”）的大小。

VssAdmin 包含如下所示的命令：

  - create shadow  ：创建新的卷影副本  
      
  - delete shadows  ：删除卷影副本  
      
  - list providers  ：列出所有已注册的 VSS 提供程序  
      
  - list writers  ：列出所有订阅的 VSS 编写程序  
      
  - resize shadowstorage  ：更改卷影副本存储区域的大小上限  
      

VssAdmin 只能用于管理由系统软件提供程序创建的卷影副本。

VssAdmin 适用于 Windows 客户端和 Windows Server 操作系统版本。

## <a name="volume-shadow-copy-service-registry-keys"></a>卷影复制服务注册表项

以下注册表项可用于 VSS：

  - VssAccessControl   
      
  - MaxShadowCopies   
      
  - MinDiffAreaFileSize   
      

### <a name="vssaccesscontrol"></a>VssAccessControl

此项用于指定哪些用户有权访问卷影副本。

有关详细信息，请参阅 MSDN 网站上的以下条目：

  - [编写程序的安全注意事项](https://go.microsoft.com/fwlink/?linkid=157739) (https://go.microsoft.com/fwlink/?LinkId=157739)  
      
  - [请求程序的安全注意事项](https://go.microsoft.com/fwlink/?linkid=180908) (https://go.microsoft.com/fwlink/?LinkId=180908)  
      

### <a name="maxshadowcopies"></a>MaxShadowCopies

此项指定可以存储在计算机的每个卷上的客户端可访问的卷影副本的最大数量。 共享文件夹的卷影副本使用客户端可访问的卷影副本。

有关详细信息，请参阅 MSDN 网站上的以下条目：

[用于备份和还原的注册表项](https://go.microsoft.com/fwlink/?linkid=180909) (https://go.microsoft.com/fwlink/?LinkId=180909) 下的“MaxShadowCopies” 

### <a name="mindiffareafilesize"></a>MinDiffAreaFileSize

此项指定卷影副本存储区域的最小初始大小 (MB)。

有关详细信息，请参阅 MSDN 网站上的以下条目：

[用于备份和还原的注册表项](https://go.microsoft.com/fwlink/?linkid=180910) (https://go.microsoft.com/fwlink/?LinkId=180910) 下的“MinDiffAreaFileSize” 

`##`#` 支持的操作系统版本

下表列出了 VSS 功能支持的最低操作系统版本。


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>VSS 功能</th>
<th>最低受支持的客户端</th>
<th>最低受支持的服务器</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LUN 重新同步</p></td>
<td><p>无受支持的版本</p></td>
<td><p>Windows Server 2008 R2</p></td>
</tr>
<tr class="even">
<td><p><strong>FilesNotToSnapshot</strong> 注册表项</p></td>
<td><p>Windows Vista</p></td>
<td><p>Windows Server 2008</p></td>
</tr>
<tr class="odd">
<td><p>可传输的卷影副本</p></td>
<td><p>无受支持的版本</p></td>
<td><p>Windows Server 2003 SP1</p></td>
</tr>
<tr class="even">
<td><p>硬件卷影副本</p></td>
<td><p>无受支持的版本</p></td>
<td><p>Windows Server 2003</p></td>
</tr>
<tr class="odd">
<td><p>以前版本的 Windows Server</p></td>
<td><p>Windows Vista</p></td>
<td><p>Windows Server 2003</p></td>
</tr>
<tr class="even">
<td><p>使用 LUN swap 快速恢复</p></td>
<td><p>无受支持的版本</p></td>
<td><p>Windows Server 2003 SP1</p></td>
</tr>
<tr class="odd">
<td><p>多次导入硬件卷影副本</p>
<div class="alert">
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="media/volume-shadow-copy-service/Dd560667.note(WS.10).gif" />注意</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>这样可以多次导入卷影副本。 一次只能执行一个导入操作。
<p></p></td>
</tr>
</tbody>
</table>
<p></p>
</div></td>
<td><p>无受支持的版本</p></td>
<td><p>Windows Server 2008</p></td>
</tr>
<tr class="even">
<td><p>共享文件夹的卷影副本</p></td>
<td><p>无受支持的版本</p></td>
<td><p>Windows Server 2003</p></td>
</tr>
<tr class="odd">
<td><p>可传输的自动恢复卷影副本</p></td>
<td><p>无受支持的版本</p></td>
<td><p>Windows Server 2008</p></td>
</tr>
<tr class="even">
<td><p>并发备份会话（最多 64 个）</p></td>
<td><p>Windows XP</p></td>
<td><p>Windows Server 2003</p></td>
</tr>
<tr class="odd">
<td><p>与备份并发的单个还原会话</p></td>
<td><p>Windows Vista</p></td>
<td><p>带 SP2 的 Windows Server 2003</p></td>
</tr>
<tr class="even">
<td><p>与备份并发的最多 8 个还原会话</p></td>
<td><p>Windows 7</p></td>
<td><p>Windows Server 2003 R2</p></td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅

[Windows 开发人员中心中的卷影复制服务](https://docs.microsoft.com/windows/desktop/vss/volume-shadow-copy-service-overview)