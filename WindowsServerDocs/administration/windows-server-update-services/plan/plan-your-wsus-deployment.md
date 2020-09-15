---
title: 规划 WSUS 部署
description: Windows Server Update Service (WSUS) 主题 - 概述了部署规划流程，并提供了相关主题的链接
ms.topic: article
ms.assetid: 35865398-b011-447a-b781-1c52bc0c9e3a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 05/24/2018
ms.openlocfilehash: 45d2dbc330c4277de961943cdd7a97fb50215de1
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628541"
---
# <a name="plan-your-wsus-deployment"></a>规划 WSUS 部署

>适用于：Windows Server 2019、Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

部署 Windows Server Update Services (WSUS) 的第一步是做出重要决定，例如确定 WSUS 部署方案、选择网络拓扑和了解系统要求。 以下清单汇总了为部署做准备时执行的步骤。

|任务|说明|
|----|--------|
|[1.1.查看注意事项和系统要求](#11-review-considerations-and-system-requirements)|查看注意事项列表和系统要求，以确保你拥有部署 WSUS 所需的所有硬件和软件。|
|[1.2.选择 WSUS 部署方案](#12-choose-a-wsus-deployment-scenario)|确定将使用哪种 WSUS 部署方案。|
|[1.3.选择 WSUS 存储策略](#13-choose-a-wsus-storage-strategy)|确定哪种 WSUS 存储策略最适合你的部署。|
|[1.4.选择 WSUS 更新语言](#14-choose-wsus-update-languages)|确定将安装哪种 WSUS 更新语言。|
|[1.5.计划 WSUS 计算机组](#15-plan-wsus-computer-groups)|计划你进行部署时所用的 WSUS 计算机组方法。|
|[1.6.计划 WSUS 性能注意事项：后台智能传送服务](#16-plan-wsus-performance-considerations)|计划优化性能的 WSUS 设计。|
|[1.7.计划自动更新设置](#17-plan-automatic-updates-settings)|计划如何为你的方案配置自动更新设置。|

## <a name="11-review-considerations-and-system-requirements"></a>1.1. 查看注意事项和系统要求

### <a name="system-requirements"></a>系统要求

硬件和数据库软件要求取决于组织中要更新的客户端计算机的数量。  启用 WSUS 服务器角色之前，按照以下指南确认服务器满足系统要求，以及你拥有完成安装所需的权限：

-   启用 WSUS 角色的服务器硬件要求与硬件要求相关。 WSUS 的最低硬件需求是：

    -   **处理器：** 1.4 千兆赫 (GHz) x64 处理器（推荐使用 2Ghz 或以上）

    -   **内存：** 除了服务器和所有其他服务或软件需要的内存量之外，WSUS 还需要额外的 2 GB RAM。

    -   **可用磁盘空间：** 建议使用 40 GB 或更多

    -   **网络适配器：** 每秒 100 兆位 (Mbps) 或以上（建议使用 1GB）

> [!NOTE]
> 这些指导原则假设 WSUS 客户端每 8 小时与服务器同步一次（客户端总共为 30000 个）。 如果同步频率更高，则服务器负载会相应地增加。

-   软件要求：

    -   为查看报告，WSUS 需要 [Microsoft Report Viewer Redistributable 2008](https://www.microsoft.com/download/details.aspx?id=6576)。 在 Windows Server 2016 上，WSUS 需要 [Microsoft Report Viewer 运行时 2012](https://www.microsoft.com/download/details.aspx?id=35747)

-   如果你安装的角色或软件更新要求你在安装完成时重新启动服务器，则在你启用 WSUS 服务器角色之前，先重新启动服务器。

-   必须在将安装 WSUS 服务器角色的服务器上安装 Microsoft .NET Framework 4.0。

-   NT Authority\Network Service 帐户必须拥有以下文件夹的完全控制权限，以便 WSUS 管理管理单元正确显示：

    -   %windir%\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET Files

        > [!NOTE]
        > 在安装含有 Internet Information Service (IIS) 的 Web 服务器角色之前，该路径可能不存在。

    -   %windir%\Temp

-   确认你打算用来安装 WSUS 的帐户是本地 Administrators 组成员。

### <a name="installation-considerations"></a>安装注意事项

在安装过程中，WSUS 将默认安装以下各项：

-   .NET API 和 Windows PowerShell cmdlet

-   供 WSUS 使用的的 Windows 内部数据库 (WID)

-   供 WSUS 使用的服务如下：

    -   更新服务

    -   报告 Web 服务

    -   客户端 Web 服务

    -   简单 Web 身份验证 Web 服务

    -   服务器同步服务

    -   DSS 身份验证 Web 服务

### <a name="features-on-demand-considerations"></a>按需功能注意事项

请注意，将客户端计算机（包括服务器）配置为使用 WSUS 进行更新会形成以下限制：

1. 使用按需功能移除了其有效负载的服务器角色无法从 Microsoft 更新进行按需安装。 必须在尝试安装这类服务器角色时提供安装源，或在组策略中为按需功能配置源。

2. Windows 客户端版本无法从 Web 按需安装 .NET 3.5。 与服务器角色相同的注意事项也适用于 .NET 3.5。

   > [!NOTE]
   > 配置按需功能安装源不涉及 WSUS。 有关如何配置这些功能的信息，请参阅 [在 Windows Server 中配置按需功能](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127275(v=ws.11))。

3. 运行 Windows 10 版本 1709 或版本 1803 的企业设备无法直接从 WSUS 安装任何按需功能。 若要安装按需功能，请[创建功能文件（并排存储）](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127275%28v=ws.11%29#create-a-feature-file-or-side-by-side-store)或从以下源之一获取按需功能包：
   - [批量许可服务中心](https://www.microsoft.com/licensing/servicecenter) (VLSC) - 需要批量许可访问权限
   - OEM 门户 - 需要 OEM 访问权限
   - MSDN 下载 - 需要 MSDN 订阅

     可以使用 [DISM 命令行选项](/windows-hardware/manufacture/desktop/dism-operating-system-package-servicing-command-line-options)安装单独获取的按需功能包。

### <a name="wsus-database-requirements"></a>WSUS 数据库要求
WSUS 要求以下数据库之一：

-   Windows 内部数据库 (WID)

-   任何受支持的 Microsoft SQL Server 版本。 有关详细信息，请参阅 [Microsoft 生命周期策略](https://aka.ms/sqllifecycle)。

WSUS 支持以下版本的 SQL Server：

-   Standard

-   企业

-   速成

> [!NOTE]
> SQL Server Express 2008 R2 具有 10 GB 的数据库大小限制。 此数据库大小可能足以用于 WSUS，尽管使用此数据库而不是 WID 没有明显好处。 WID 数据库具有最小 2 GB 的 RAM 内存要求，这超过了标准 Windows Server 系统要求。

你可以在与数据库服务器计算机独立开来的计算机上安装 WSUS 角色。 在这种情况下，以下其他标准适用于：

1.  数据库服务器不能作为域控制器进行配置。

2.  WSUS 服务器不能运行远程桌面服务。

3.  数据库服务器必须与 WSUS 服务器位于相同的 Active Directory 域中，或它必须与 WSUS 服务器的 Active Directory 域建立信任关系。

4.  WSUS 服务器和数据库服务器必须处于相同的时区中，或同步到相同的协调世界时（格林威治标准时间）源。

## <a name="12-choose-a-wsus-deployment-scenario"></a>1.2. 选择 WSUS 部署方案
本部分介绍了所有 WSUS 部署的基本特征。 使用本部分，熟悉单一 WSUS 服务器的简单部署，并且了解更加复杂的方案，例如在独立网段上的 WSUS 服务器层次结构或 WSUS 服务器。

### <a name="simple-wsus-deployment"></a>简单 WSUS 部署
最基本的 WSUS 部署由在私有内部网上为客户端计算机提供服务的企业防火墙内部的服务器组成。 将 WSUS 服务器连接到 Microsoft 更新，以下载更新。 这称为 *同步*。 在同步期间，WSUS 确定自上次同步起是否有任何新更新可供使用。 如果你是第一次同步 WSUS，所有更新均可供下载。

> [!NOTE]
> 初步同步将花费一个小时。 所有后续同步所花费的时间将大大减少。

默认情况下，WSUS 服务器将端口 80 用于 HTTP 协议，将端口 443 用于 HTTPS 协议，以从 Microsoft 获取更新。 如果你的网络和 Internet 之间存有企业防火墙，则必须在直接与 Microsoft 更新通信的服务器上打开这些端口。 如果你打算使用自定义端口进行此类通信，则必须打开那些端口。 你可以将多台 WSUS 服务器配置为与父 WSUS 服务器同步。 默认情况下，WSUS 服务器将端口 8530 用于 HTTP 协议，将端口 8531 用于 HTTPS 协议，以向客户端工作站提供更新。

### <a name="multiple-wsus-servers"></a>多台 WSUS 服务器
管理员可部署多台运行 WSUS 的服务器，从而同步其组织内部网中的所有内容。 你可以仅向 Internet 公开一台服务器，它将成为从 Microsoft 更新下载更新的唯一服务器。 将该服务器设置为上游服务器 - 与下游服务器同步的源。 在适当情况下，服务器可遍布于在地理上分散的网络中，以向所有客户端计算机提供最佳连接。

### <a name="disconnected-wsus-server"></a>断开的 WSUS 服务器
如果公司策略或其他条件限制计算机访问 Internet，管理员可设置内部服务器以运行 WSUS。 此示例说明了服务器连接到内部网却与 Internet 独立开来的情况。 在该服务器上下载、测试和批准更新之后，管理员会将更新元数据和内容导出到 DVD。 将更新元数据和内容从 DVD 中导入到在内部网运行 WSUS 的服务器。

### <a name="wsus-server-hierarchies"></a>WSUS 服务器层次结构
你可以创建 WSUS 服务器的复杂层次结构。 因为你可将一台 WSUS 服务器与另一台 WSUS 服务器（而非 Microsoft 更新）同步，所以你必须拥有唯一一台与 Microsoft 更新连接的 WSUS 服务器。 当你将 WSUS 服务器连接在一起时，则存在上游 WSUS 服务器和下游 WSUS 服务器。 WSUS 服务器层次结构部署具有以下几个优点：

-   你可以一次从 Internet 下载更新，然后使用下游服务器将更新分配给客户端计算机。 该方法将节约企业 Internet 连接上的带宽。

-   你可将更新下载到接近实际的客户端计算机（例如在分支机构）的 WSUS 服务器。

-   你可设置独立的 WSUS 服务器以服务使用 Microsoft 产品不同语言的客户端计算机。

-   对于客户端计算机数量超出一台 WSUS 服务器有效管理范围的大型组织而言，你可以扩展 WSUS。

> [!NOTE]
> 我们建议你不要创建三个级别以上的 WSUS 服务器层次结构。 每个级别将增加向整个连接的服务器传播更新的时间。 虽然在理论上层次结构没有受到限制，但 Microsoft 只对具有五个级别的层次结构部署进行了测试。
>
> 另外，下游服务器必须采用与上游服务器同步源相同的 WSUS 版本或更早的版本。

你可在“自治”模式（旨在实现分布式管理）或“副本”模式（旨在实现集中管理）下连接 WSUS 服务器。 你无需部署只使用一个模式的服务器层次结构：你可部署使用自治和副本 WSUS 服务器的 WSUS 解决方案。

#### <a name="autonomous-mode"></a>“自治”模式
“自治”模式（也称为分布式管理）是 WSUS 的默认安装选项。 在“自治”模式中，上游 WSUS 服务器与下游服务器在同步期间分享更新。 独立管理下游 WSUS 服务器，它们不接收来自上游服务器的更新批准状态或计算机组信息。 使用分布式管理模式，每个 WSUS 服务器管理员选择更新语言、创建计算机组、将计算机分配给各组、测试和批准更新，并确保将正确的更新安装到适当的计算机组。 以下图像显示你可能在分支机构环境中部署自治 WSUS 服务器的方式：

#### <a name="replica-mode"></a>副本模式
拥有与下游服务器分享更新、批准状态和计算机组的上游 WSUS 服务器，即可使用“副本”模式（也称为集中管理）。 副本服务器将继承更新批准，并且不能脱离其上游 WSUS 服务器进行管理。 以下图像显示你可能在分支机构环境中部署副本 WSUS 服务器的方式：

> [!NOTE]
> 如果你设置几台副本服务器以连接到单台上游 WSUS 服务器，请勿计划在每台副本服务器上同时运行同步。 该操作将避免带宽使用突然加剧的现象。

### <a name="branch-offices"></a>分支机构
你可利用 Windows 中的“分支机构”功能优化 WSUS 部署。 此类部署提供以下优势：

1.  有利于降低 WAN 链路利用率，并改进应用程序响应性。 若要启用由 Web 服务器提供的内容的 BranchCache 加速，则在服务器和客户端上安装 BranchCache 功能，并确保已启动 BranchCache 服务。 不需要其他步骤。

2.  在低带宽连接到中央办公室而高带宽连接到 Internet 的分支机构中，同样可使用“分支机构”功能。 在这种情况下，你可能希望配置下游 WSUS 服务器，以获取有关安装哪些来自中央 WSUS 服务器的更新的信息，并且从 Microsoft 更新下载更新。

### <a name="network-load-balancing"></a>Network Load Balancing
网络负载平衡 (NLB) 提高 WSUS 网络的可靠性和性能。 你可以设置多台 WSUS 服务器，使其共享运行 SQL Server（例如 SQL Server 2008 R2 SP1）的单一故障转移群集。 在该配置中，你必须使用完整的 SQL Server 安装程序（而非 WSUS 提供的 Windows 内部数据库安装程序），并且数据库角色必须安装在所有 WSUS 前端服务器上。 你还可让所有 WSUS 服务器都使用分布式文件系统 (DFS) 来存储其内容。

**用于 NLB 的 WSUS 设置**：与用于 NLB 的 WSUS 3.2 设置相比，配置用于 NLB 的 WSUS 不再需要特殊的设置调用和参数。 你只需要设置每台 WSUS 服务器，请记住以下注意事项。

-   WSUS 必须使用 SQL 数据库选项而不是 WID 进行设置。

-   如果在本地存储更新，则必须在共享相同 SQL 数据库的 WSUS 服务器之间共享相同的内容文件夹。

-   WSUS 设置必须串行进行。 在共享相同 SQL 数据库时，安装后任务不能同时在多台服务器上运行。

### <a name="wsus-deployment-with-roaming-client-computers"></a>带有漫游客户端计算机的 WSUS 部署
如果网络包含从不同位置登录到网络的移动用户，则可配置 WSUS，以便漫游用户从在地理上最接近它们的 WSUS 服务器更新其客户端计算机。 例如，你可以在每个区域部署一台 WSUS 服务器，并为每个区域使用不同的 DNS 子网。 所有客户端计算机都可以定向到同一 WSUS 服务器，从而确定在每个子网中距离最近的实际 WSUS 服务器。

## <a name="13-choose-a-wsus-storage-strategy"></a>1.3. 选择 WSUS 存储策略
Windows Server Update Services (WSUS) 使用两种存储系统：一个是存储 WSUS 配置和更新元数据的数据库，另一个是存储更新文件的可选本地文件系统。 在安装 WSUS 之前，应确定你希望实施存储的方式。

更新由两部分组成：描述更新的元数据，以及安装更新所需的文件。 更新元数据的规模通常比实际的更新要小很多，并且它存储在 WSUS 数据库中。 更新文件存储在本地 WSUS 服务器上或 Microsoft 更新 Web 服务器上。

### <a name="wsus-database"></a>WSUS 数据库
WSUS 需要适用于每台 WSUS 服务器的数据库。 WSUS 支持使用位于与 WSUS 服务器有所不同的计算机上的数据库，但受到一些限制。 有关受支持的数据库列表和远程数据库限制的详细信息，请参阅本指南中的“1.1 查看初始注意事项和系统要求”部分。

WSUS 数据库存储以下信息：

-   WSUS 服务器配置信息

-   描述各个更新的元数据

-   有关客户端计算机、更新和交互的信息

如果你安装多台 WSUS 服务器，你必须为每台 WSUS 服务器维护独立的数据库，不管它是自治服务器还是副本服务器。 你不能将多个 WSUS 数据库存储在 SQL Server 的单一实例中，除使用 SQL Server 故障转移的网络负载平衡 (NLB) 群集外。

SQL Server、SQL Server Express 和 Windows 内部数据库为单服务器配置提供相同的性能特征，其数据库和 WSUS 服务都位于相同的计算机上。 单服务器配置可支持数千台 WSUS 客户端计算机。

> [!NOTE]
> 请勿尝试通过直接访问数据库来管理 WSUS。 直接操控数据库会导致数据库损坏。 损坏可能不会即时显现，但它会阻止升级到产品的下一版本。 可以通过使用 WSUS 控制台或 WSUS 应用程序编程接口 (API) 来管理 WSUS。

#### <a name="wsus-with-windows-internal-database"></a>带 Windows 内部数据库的 WSUS
默认情况下，安装向导创建和使用命名为 SUSDB.mdf 的 Windows 内部数据库。 该数据库位于 %windir%\wid\data\ folder 中，其中 %windir% 是安装 WSUS 服务器软件的本地驱动器。

> [!NOTE]
> Windows 内部数据库 (WID) 是在 Windows Server 2008 中引入的。

WSUS 支持仅用于数据库的 Windows 身份验证。 你不能同时使用 SQL Server 身份验证和 WSUS。 如果你针对 WSUS 数据库使用 Windows 内部数据库，WSUS 安装可创建命名为 server\Microsoft##WID 的 SQL Server 实例，其中的服务器采用计算机的名称。 使用任一数据库选项，WSUS 安装创建命名为 SUSDB 的数据库。 该数据库的名称是不可配置的。

我们建议你在以下情况下使用 Windows 内部数据库：

-   组织尚未购买且无需适用于任何其他应用程序的 SQL Server 产品。

-   组织无需 NLB WSUS 解决方案。

-   你打算部署多台 WSUS 服务器（例如在分支机构中）。 在这种情况下，你应考虑在辅助服务器上使用 Windows 内部数据库，即使你将使用适用于根 WSUS 服务器的 SQL Server。 由于每台 WSUS 服务器都需要独立的 SQL Server 实例，因此，如果只有一个 SQL Server 实例处理多台 WSUS 服务器，你将很快经历数据库性能问题。

Windows 内部数据库不提供用户界面或任何数据库管理工具。 如果为 WSUS 选择该数据库，则必须使用外部工具来管理数据库。 有关更多信息，请参阅：

-   [备份和还原 WSUS 数据以及备份你的服务器](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd939904(v=ws.10))

-   [为 WSUS 数据库重建索引](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd939795(v=ws.10))

#### <a name="wsus-with-sql-server"></a>带 SQL Server 的 WSUS
我们建议你在以下情况下使用 SQL Server 和 WSUS：

1.  你需要 NLB WSUS 解决方案。

2.  你已经至少安装了一个 SQL Server 实例。

3.  你不能在本地非系统账户下运行 SQL Server 服务，或使用 SQL Server 身份验证。 WSUS 仅支持 Windows 身份验证。

### <a name="wsus-update-storage"></a>WSUS 更新存储
将更新同步到 WSUS 服务器时，元数据和更新文件存储在两个不同的位置。 元数据存储在 WSUS 数据库中。 更新文件可以存储在 WSUS 服务器上或 Microsoft 更新服务器上（具体取决于同步选项的配置方式）。 如果选择将更新文件存储在 WSUS 服务器上，则客户端计算机会从本地 WSUS 服务器下载批准的更新。 如果不选择这样做，客户端计算机将直接从 Microsoft 更新下载批准的更新。 最适合你组织的选项将取决于 Internet 的网络带宽、内部网上的网络带宽以及本地存储可用性。

你可为每个部署的 WSUS 服务器选择不同的更新存储解决方案。

#### <a name="local-wsus-server-storage"></a>本地 WSUS 服务器存储
当你安装和配置 WSUS 时，更新文件的本地存储是默认选项。 此选项可将企业连接上的带宽保存到 Internet，因为客户端计算机直接从本地 WSUS 服务器下载更新。

此选项要求服务器拥有充分的磁盘空间来存储所有需要的更新。 WSUS 至少需要 20 GB 才能将更新存储在本地；但是我们建议根据测试的变量使用 30 GB。

#### <a name="remote-storage-on-microsoft-update-servers"></a>在 Microsoft 更新服务器上的远程存储
你可以将更新远程存储在 Microsoft 更新服务器上。 如果大多数客户端计算机通过慢速 WAN 连接来连接 WSUS 服务器，但它们却通过高带宽连接来连接 Internet，则此选项是非常有帮助的。

在这种情况下，根 WSUS 服务器与 Microsoft 更新同步，并接收更新元数据。 你批准更新后，客户端计算机从 Microsoft 更新服务器下载批准的更新。

## <a name="14-choose-wsus-update-languages"></a>1.4. 选择 WSUS 更新语言
当你部署 WSUS 服务器层次结构时，你应确定整个组织需要哪种语言更新。 你应配置根 WSUS 服务器以下载整个组织使用的所有语言的更新。

例如，总部可能需要英语和法语更新，但某个分支机构需要英语、法语和德语更新，其他分支机构则需要英语和西班牙语更新。 在这种情况下，你将配置根 WSUS 服务器，以下载英语、法语、德语和西班牙语更新。 随后为第一个分支机构配置 WSUS 服务器以便仅下载英语、法语和德语，为第二个分支机构配置 WSUS 服务器以便仅下载英语和西班牙语更新。

WSUS 配置向导的 **“选择语言”** 页可让你获得所有语言或语言子集的更新。 选择语言子集将节省磁盘空间，但选择 WSUS 服务器的所有下游服务器和客户端计算机需要的语言至关重要。

以下是一些有关你在配置此选项之前应记住的更新语言的重要事项：

-   除整个组织需要的任何其他语言外，始终包含英语。 所有更新都是以英语软件包为基础的。

-   如果你尚未选择上游服务器需要的所有语言，则下游服务器和客户端计算机将接收不到所有必需的更新。 确保你选择了与所有下游服务器有关的所有客户端计算机需要的全部语言。

-   一般情况下，你应在与 Microsoft 更新同步的根 WSUS 服务器上下载所有语言的更新。 此选择确保所有下游服务器和客户端计算机将接收需要的语言更新。

如果你在本地存储更新，并且你安装了 WSUS 服务器以便下载有限范围内的语言更新，则可能会注意到除你指定的语言更新外，还有其他语言更新。 所有更新文件都包含几种语言，其中至少包含一种在服务器上指定的语言。

**上游服务器**

> [!NOTE]
> 将上游服务器配置为同步下游副本服务器所需的所有语言中的更新。 不会向你通知非同步语言中的所需更新。

更新会在需要相关语言的客户端计算机上显示为“不适用”  。 若要避免此问题，请确保所有操作系统语言都包含在 WSUS 服务器同步选项中。 可以通过转到 WSUS 管理控制台的“计算机”  视图并按操作系统语言对计算机进行排序，来查看所有操作系统语言。 但是，如果存在多种语言的 Microsoft 应用程序（例如，如果在使用英语版 Windows 8 的某些计算机上安装法语版的 Microsoft Word），则你可能要包含多种语言。

为上游服务器选择语言与为下游服务器选择语言不同。 以下过程说明了差异。

#### <a name="to-choose-update-languages-for-a-server-synchronizing-from-microsoft-update"></a>为从 Microsoft 更新进行同步的服务器选择更新语言

1.  在 WSUS 配置向导中：

    -   若要获取所有语言的更新，请单击“下载包括新语言在内的所有语言的更新”  。

    -   若要仅获取特定语言的更新，请单击“仅下载以下语言的更新”  ，然后选择你希望获得更新的语言。

#### <a name="to-choose-update-languages-for-a-downstream-server"></a>为下游服务器选择更新语言

1.  如果上游服务器配置为下载一部分语言的更新文件：在 WSUS 配置向导中，单击“仅下载以下语言的更新”  （上游服务器仅支持标有星号的语言），然后选择你希望获得更新的语言。

> [!NOTE]
> 即使你希望下游服务器下载与上游服务器相同的语言，也应执行此操作。

2. 如果上游服务器配置为下载所有语言的更新文件：在 WSUS 配置向导中，单击“下载上游服务器支持的所有语言的更新”  。

> [!NOTE]
> 即使你希望下游服务器下载与上游服务器相同的语言，也应执行此操作。 此设置使上游服务器下载所有语言的更新，包括最初没有为上游服务器配置的语言。 如果向上游服务器添加语言，则应将新的更新复制到其副本服务器。
>
> 在上游服务器上单独更改语言选项可能会导致中心服务器上批准的更新数与副本服务器上批准的更新数不匹配。

## <a name="15-plan-wsus-computer-groups"></a>1.5. 计划 WSUS 计算机组
WSUS 可让你将各组客户端计算机作为更新目标，从而确保特定计算机总是在最方便的时候获得适当的更新。 例如，如果同一部门（例如会计组）中的所有计算机具有特定配置，你可为该组建立一个计算机组，并确定它们的计算机需要哪些更新以及何时安装这些更新，然后使用 WSUS 报告评估团队更新。

> [!NOTE]
> 如果 WSUS 服务器在副本模式下运行，则不能在该服务器上创建计算机组。 必须在属于 WSUS 服务器层次结构的 WSUS 服务器上，创建副本服务器的客户端计算机需要的所有计算机组。 有关副本模式的详细信息，请参阅《WSUS 3.0 SP2 操作指南》中的“管理 WSUS 副本服务器”[管理 WSUS 副本服务器](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd939893(v=ws.10))。

计算机始终分配给“所有计算机”  组，并且它们保持分配给“未分配的计算机”  组，直到你将它们分配给其他组。 计算机可以属于多个组。

可以按层次结构建立计算机组（例如，在 Accounting 组下的 Payroll 组和 Accounts Payable 组）。 除位置较高组外，为位置较高的组批准的更新将自动部署到位置较低的组。 在本示例中，如果你为 Accounting 组批准 Update1，更新将被部署到 Accounting 组中的所有计算机、Payroll 组中的所有计算机以及 Accounts Payable 组中的所有计算机。

因为可将计算机分配给多个组，所以可为同一台计算机多次批准单一更新。 但是，更新仅被部署一次，且 WSUS 服务器将解决任何冲突。 在上一示例中，如果计算机 A 被分配给 Payroll 组和 Accounts Payable 组，且为这两个组批准 Update1，则它将仅部署一次。

可以使用“指向服务器端”或“指向客户端”这两种方法之一将计算机分配到计算机组。 以下是每种方法的定义：

-   **指向服务器端**：你手动将一台或多台客户端计算机同时分配给多个计算机组。

-   **指向客户端**：在客户端计算机上使用组策略或编辑注册表设置，使那些计算机可以自动将其添加到之前创建的计算机组中。

### <a name="conflict-resolution"></a>冲突解决
服务器应用以下规则以解决冲突和确定客户端上的结果操作：

1.  优先级

2.  安装/卸载

3.  最后期限

#### <a name="priority"></a>优先级
与最高优先级组有关的操作会覆盖其他组的操作。 小组在组层次结构中出现的结构越深，优先级越高。 仅基于深度分配优先级；所有分支都有相同的优先级。 例如，桌面分支之下二级的组的优先级高于服务器分支之下一级的组。

在更新服务控制台层次结构窗格的以下文本示例中，对于名为 WSUS-01 的 WSUS 服务器，名为“台式计算机”和“服务器”的计算机组已添加到默认的“所有计算机”组。  桌面计算机和服务器组都处于相同的层次结构级别。

-   **更新服务**

    -   **WSUS-01**

        -   **更新**

        -   **计算机**

            -   **所有计算机**

                -   **未分配的计算机**

                -   **台式计算机**

                    -   **Desktops-L1**

                        -   **Desktops-L2**

                -   **服务器**

                    -   **Servers-L1**

        -   **下游服务器**

        -   **同步**

        -   **报表**

        -   **选项**

在此示例中，桌面计算机分支之下二级 (Desktops L2) 的组的优先级高于服务器分支之下一级 (Servers L1) 的组。 因此，对于具有 Desktops-L2 和 Servers-L1 组成员资格的计算机，Desktops-L2 组的所有操作优先于为 Servers-L1 组指定的操作。

#### <a name="priority-of-install-and-uninstall"></a>安装和卸载的优先级
安装操作会覆盖卸载操作。 必需安装会覆盖可选安装（可选安装仅通过 API 可用且为使用 WSUS 管理控制台的更新更改批准将清除所有可选批准）。

#### <a name="priority-of-deadlines"></a>最后期限的优先级
具有最后期限的操作会覆盖没有最后期限的操作。  最后期限较早的操作会覆盖最后期限较晚的操作。

## <a name="16-plan-wsus-performance-considerations"></a>1.6. 计划 WSUS 性能注意事项
在部署 WSUS 之前，你应小心计划一些区域，以便你可以优化性能。 关键区域包括：

-   网络设置

-   延迟的下载

-   筛选器

-   安装

-   大规模更新部署

-   后台智能传送服务 (BITS)

### <a name="network-setup"></a>网络设置
若要优化 WSUS 网络中的性能，请考虑以下建议：

1.  在集散拓扑（而非层次结构拓扑）中设置 WSUS 网络。

2.  为漫游客户端计算机使用 DNS 网络掩码排序，并配置漫游客户端计算机以获得本地 WSUS 服务器的更新。

### <a name="deferred-download"></a>延迟的下载
你可在下载更新文件之前，批准更新和下载更新元数据，这种方法被称为 *延迟的下载*。 当你延迟下载时，仅在获批准之后才能下载更新。 我们建议你延迟下载，原因是它优化了网络带宽和磁盘空间。

在 WSUS 服务器的层次结构中，WSUS 将自动设置所有下游服务器，以使用根 WSUS 服务器的延迟下载设置。 你可以更改此默认设置。 例如，你可配置上游服务器以执行完全、即时同步，然后配置下游服务器以延迟下载。

如果你部署连接的 WSUS 服务器的层次结构，我们建议你不要深入嵌套服务器。 如果你启用延迟的下载，且下游服务器请求未在上游服务器上获批准的更新，则下游服务器的请求将强制在上游服务器上执行下载。 然后下游服务器在后续同步上下载更新。 在 WSUS 服务器的深层次结构中，请求和下载更新并将更新传递到服务器层次结构时会出现延误。 默认情况下，当你在本地存储更新时，启用延迟的下载。 你可以手动更改此选项。

### <a name="filters"></a>筛选器
WSUS 可让你按语言、产品和类别来过滤更新同步。 在 WSUS 服务器的层次结构中，WSUS 将自动设置所有下游服务器，以使用在根 WSUS 服务器上选择的更新过滤选项。 你可以配置下游服务器，以仅接收语言子集。

默认情况下，要更新的产品是 Windows 和 Office，默认类别是 Critical 更新、Security 更新和 Definition 更新。 若要保存带宽和磁盘空间，我们建议你将语言限制为你实际使用那些语言。

### <a name="installation"></a>安装
更新通常由新版本且早已存在于准备更新的计算机中的文件组成。 在二进制级，这些现有的文件可能与更新的版本有很大不同。 快速安装文件功能识别不同版本之间的精确字节，并创建和分配仅限于那些差异的更新，然后将现有文件与更新的字节合并在一起。

有时候该功能被称为增量交付，因为它仅下载文件的两个版本之间的增量（差异）。 快速安装文件比分配给客户端计算机的更新要大，因为快速安装文件含有每份要更新的文件的所有潜在版本。

可以使用快速安装文件限制在本地网络上消耗的带宽，因为 WSUS 仅传输适用于特定版本的更新组件的增量。 但是，这会在你的 WSUS 服务器、任何上游 WSUS 服务器与 Microsoft 更新之间形成额外带宽成本，并且需要更多的本地磁盘空间。 默认情况下，WSUS 并不使用快速安装文件。

并非所有更新都适合使用快速安装文件来分配。 如果你选择此选项，你将为所有更新获得快速安装文件。 如果不在本地存储更新，则 Windows 更新代理会决定是下载快速安装文件还是完整文件更新分发。

### <a name="large-update-deployment"></a>大规模更新部署
当你部署大规模更新（例如 service pack）时，你可以使用以下操作来避免占满网络：

1.  使用后台智能传送服务 (BITS) 限制 可使用当天的时间来控制 BITS 带宽，但它们适用于使用 BITS 的所有应用程序。 若要了解如何控制 BITS 限制，请参阅[组策略](/windows/win32/bits/group-policies)。

2.  使用 Internet 信息服务 (IIS) 限制来控制对一个或多个 Web 服务的限制。

3.  使用计算机组来控制推出。 当客户端计算机向 WSUS 服务器发送信息时，它将自己识别为特定计算机组的成员。 WSUS 服务器使用此信息确定应向此计算机部署哪些更新。 你可以设置多个计算机组，并随后为这些组的子集批准大规模 service pack 下载。

### <a name="background-intelligent-transfer-service"></a>后台智能传送服务
WSUS 为所有其文件传送任务使用后台智能传送服务 (BITS) 协议。 这包括到客户端计算机和服务器同步的下载。 BITS 使用空闲带宽启用程序来下载文件。 BITS 保持通过断开网络和重新启动计算机来传送文件的方式。 有关更多信息，请参阅：[后台智能传送服务](/windows/win32/bits/background-intelligent-transfer-service-portal)

## <a name="17-plan-automatic-updates-settings"></a>1.7. 计划自动更新设置
你可以指定批准 WSUS 服务器上的更新的截止时间。 截止时间促使客户端计算机在特定时间安装更新，但存在的情况有许多种，取决于截止时间是否过期、计算机中是否有其他更新排队等候安装以及更新（或队列中的其他更新）是否需要重新启动。

默认情况下，自动更新每隔 22 小时（减去随机偏移量）就向 WSUS 服务器询问批准的更新。 如果需要安装新更新，则已下载它们。 每个检测周期之间的时间可限制为 1 到 22 小时。

你可以按如下方式操控通知选项：

1.  如果配置自动更新以通知用户更新已准备好安装，则将通知发送到系统日志以及客户端计算机的通知区域。

2.  当带有适当凭据的用户单击通知区域图标，自动更新将显示要安装的可用更新。 用户必须单击 **“安装”** 以启动安装。 如果更新需要重新启动计算机以完成更新，则一条信息会出现。 如果需要重新启动，自动更新将无法检测额外更新，直到计算机已重新启动。

如果配置自动更新以按计划安装更新，则下载适用的更新，并将它标记为“准备好安装”。 自动更新使用通知区域图标通知拥有适当凭据的用户，并将事件记录在系统日志中。

在计划的当天和时间，自动更新安装更新并重新启动计算机（必要时），即使无本地管理员登陆。 如果本地管理员登陆和计算机需要重新启动，自动更新将显示一条警告信息和重新启动的倒计时间。 否则，安装将在后台发生。

如果必须重新启动计算机，且有任何用户登陆，则会显示类似的倒计时对话框，该对话框将警告用户即将重新启动。 你可以使用组策略操控计算机重新启动。

下载新更新后，自动更新向 WSUS 服务器询问批准的程序包列表，以确认它下载的程序包依然有效且获批准。 这意味着，如果在自动更新下载更新时，WSUS 管理员从批准的更新列表中删除更新，则实际上安装的只是依然获批准的更新。