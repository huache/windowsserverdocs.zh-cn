---
title: 使用 Windows Server 中的 SMB 3 协议的文件共享概述
description: 有关将 SMB 3 协议用于文件共享和使用 Windows Server 的文件服务的概述。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 01/10/2020
ms.localizationpriority: medium
ms.openlocfilehash: 416145a8c4ec20eaf46cf4b5ac88a0cdf38bdf33
ms.sourcegitcommit: 76469d1b7465800315eaca3e0c7f0438fc3939ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919884"
---
# <a name="overview-of-file-sharing-using-the-smb-3-protocol-in-windows-server"></a>使用 Windows Server 中的 SMB 3 协议的文件共享概述

>适用于： Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

本主题介绍 Windows Server 2019、Windows Server 2016、Windows Server 2012 R2 和 Windows Server 2012 中的 SMB 3 功能，适用于该功能的实际用途，与以前的版本相比，此版本中最重要的新功能或更新功能，以及硬件要求。 SMB 也是[软件定义数据中心（SDDC）](../../sddc.md)解决方案（例如存储空间直通、存储副本等）使用的构造协议。 SMB 版本3.0 随 Windows Server 2012 引入，并在后续版本中进行了增量改进。

## <a name="feature-description"></a>功能说明

服务器消息块 (SMB) 协议是网络文件共享协议，让计算机上的应用程序可读取和写入文件以及从计算机网络中的服务器程序请求服务。 SMB 协议可在其 TCP/IP 协议或其他网络协议上使用。 使用 SMB 协议时，应用程序（或应用程序用户）可访问远程服务器上的文件或其他资源。 这让应用程序可以读取、创建和更新远程服务器上的文件。 SMB 还可以与任何设置为接收 SMB 客户端请求的服务器程序通信。 SMB 是软件定义数据中心（SDDC）计算技术使用的构造协议，如存储空间直通、存储副本。 有关详细信息，请参阅[Windows Server 软件定义的数据中心](../../sddc.md)。

## <a name="practical-applications"></a>实际应用程序

本节讨论一些使用新 SMB 3.0 协议的全新实用方法。

* **用于虚拟化的文件存储 (Hyper-V(TM) over SMB)** 。 Hyper-V 可以通过 SMB 3.0 协议在文件共享中存储虚拟机文件，如配置、虚拟硬盘 (VHD) 文件和快照。 这既可用于独立文件服务器，又可用于将 Hyper-V 与群集的共享文件存储配合使用的群集文件服务器。
* **Microsoft SQL Server over SMB**。 SQL Server 可以将用户数据库文件存储在 SMB 文件共享中。 目前，SQL Server 2008 R2 的独立 SQL 服务器支持此功能。 即将推出的 SQL Server 版本将增加群集 SQL 服务器和系统数据库的支持。
* **用于最终用户数据的传统存储**。 SMB 3.0 协议提供 信息工作者 （或客户端）工作负载的增强功能。 这些增强功能包括减少分支机构用户在通过广域网 (WAN) 访问数据时遇到的应用程序延迟，以及防止数据遭受窃听攻击。

## <a name="new-and-changed-functionality"></a>新功能和更改的功能

以下各节介绍 SMB 3 中添加的功能以及后续更新。

## <a name="features-added-in-windows-server-2019-and-windows-10-version-1809"></a>Windows Server 2019 和 Windows 10 版本1809中新增的功能

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| 能够要求对不连续可用的文件共享上的磁盘进行写入 | “新建” | 若要提供写入文件共享的一些额外保证，请在写入操作返回为 "已完成" 之前，通过软件和硬件堆栈一直到物理磁盘，可以使用 `NET USE /WRITETHROUGH` 命令或 `New-SMBMapping -UseWriteThrough` PowerShell cmdlet 在文件共享上启用写操作。 使用 write 有一定程度的性能下降;有关进一步的讨论，请参阅博客文章[在 SMB 中控制写入行为](https://techcommunity.microsoft.com/t5/storage-at-microsoft/controlling-write-through-behaviors-in-smb/bc-p/1083417#M677)。 |

## <a name="features-added-in-windows-server-version-1709-and-windows-10-version-1709"></a>Windows Server 版本1709和 Windows 10 版本1709中添加的功能

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| 禁止对文件共享进行来宾访问 | “新建” | SMB 客户端不再允许执行以下操作：来宾帐户对远程服务器的访问权限;提供了无效凭据后回退到来宾帐户。 有关详细信息，请参阅[Windows 中默认禁用的 SMB2 中的来宾访问权限](https://support.microsoft.com/help/4046019/guest-access-in-smb2-disabled-by-default-in-windows-10-and-windows-ser)。 | 
| SMB 全局映射 | “新建” | 将远程 SMB 共享映射到本地主机上的所有用户都可以访问的驱动器号，包括容器。 这对于在数据卷上启用容器 i/o 以遍历远程装入点是必需的。 请注意，在使用容器的 SMB 全局映射时，容器主机上的所有用户都可以访问远程共享。 容器主机上运行的任何应用程序还可以访问映射的远程共享。 有关详细信息，请参阅[具有群集共享卷（CSV）的容器存储支持、存储空间直通、SMB 全局映射](https://techcommunity.microsoft.com/t5/failover-clustering/container-storage-support-with-cluster-shared-volumes-csv/ba-p/372140)。 |
| SMB 方言控制 | “新建” | 你现在可以设置注册表值以控制所使用的最低 SMB 版本（方言）和最大 SMB 版本。 有关详细信息，请参阅[控制 SMB 方言](https://techcommunity.microsoft.com/t5/storage-at-microsoft/controlling-smb-dialects/ba-p/860024)。 |

## <a name="features-added-in-smb-311-with-windows-server-2016-and-windows-10-version-1607"></a>在 SMB 3.11 中添加的功能与 Windows Server 2016 和 Windows 10 版本1607

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| SMB 加密     |   已更新      | 使用 3.1.1/Galois/Counter 模式（AES-GCM）的 SMB 高级加密标准加密比 SMB 签名或使用 AES-CCM 之前的 SMB 加密更快。   |
| 目录缓存 | “新建” | SMB 3.1.1 包括目录缓存的增强功能。 Windows 客户端现在可以缓存更大的目录，这是大约50万个的条目。 Windows 客户端将尝试具有 1 MB 缓冲区的目录查询，以减少往返和提高性能。 |
| 预身份验证完整性 | “新建” |  在 SMB 3.1.1 中，预先身份验证的完整性可让中间人攻击者篡改 SMB 的连接建立和身份验证消息。 有关详细信息，请参阅[Windows 10 中的 SMB 3.1.1 预身份验证完整性](https://docs.microsoft.com/archive/blogs/openspecification/smb-3-1-1-pre-authentication-integrity-in-windows-10)。 |
| SMB 加密改进 | “新建” | SMB 3.1.1 提供一种机制，用于协商每个连接的加密算法，以及 AES-128-CCM 和 AES-128-GCM 的选项。 AES-128-GCM 是新的 Windows 版本的默认值，较旧的版本将继续使用 AES-128-CCM。 |
| 支持滚动群集升级 | “新建” | 允许 SMB 在升级过程中显示为支持群集的不同最大版本，从而支持[滚动群集升级](../../failover-clustering/cluster-operating-system-rolling-upgrade.md)。 有关如何使用协议的不同版本（方言）来通信的详细信息，请参阅博客文章[控制 SMB 方言](https://techcommunity.microsoft.com/t5/storage-at-microsoft/controlling-smb-dialects/ba-p/860024)。 |
| Windows 10 中的 SMB 直接客户端支持 | “新建” | Windows 10 企业版、Windows 10 教育版和 Windows 10 专业版工作站现在包含 SMB 直接客户端支持。 |
| 对 FileNormalizedNameInformation API 调用的本机支持 | “新建” | 添加了对查询文件的规范化名称的本机支持。 有关详细信息，请参阅[FileNormalizedNameInformation](https://docs.microsoft.com/openspecs/windows_protocols/ms-fscc/20bcadba-808c-4880-b757-4af93e41edf6)。 |

有关更多详细信息，请参阅博客文章[Windows Server 2016 Technical Preview 2 中的 SMB 3.1.1 的新增功能](https://docs.microsoft.com/archive/blogs/josebda/whats-new-in-smb-3-1-1-in-the-windows-server-2016-technical-preview-2)。

## <a name="features-added-in-smb-302-with-windows-server-2012-r2-and-windows-81"></a>在 SMB 3.02 中添加的功能与 Windows Server 2012 R2 和 Windows 8。1

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| 自动重新平衡横向扩展文件服务器客户端     |   “新建”      | 提高横向扩展文件服务器的可伸缩性和可管理性。 将按照每个文件共享（而不是每个服务器）跟踪 SMB 客户端连接，然后将客户端重定向到群集节点，并让用户最方便地访问文件共享使用的卷。 这样便会减少文件服务器节点之间的重定向流量，从而提高效率。 在建立初始连接后以及在重新配置群集存储时，将重定向客户端。    |
| 广域网性能   | 已更新  | 当你使用文件资源管理器从远程计算机上的一个位置复制到同一服务器上的另一个副本时，Windows 8.1 和 Windows 10 提供了针对 SMB 支持的改进 CopyFile SRV_COPYCHUNK。 只需在网络上复制少量元数据（传输文件数据的每个16MiB 的2KiB）。 这会显著提高性能。 这是适用于 SMB 的 OS 级别和文件资源管理器级区别。 |
| SMB 直通     |   已更新      | 托管包含小规模 I/O 的工作负载（例如，虚拟机中的联机事务处理 (OLTP) 数据库）时，通过提高效率来优化小规模 I/O 工作负载的性能。 当使用更快的网络接口（例如 40 Gbps 以太网和 56 Gbps）时，这些改进非常明显。  |
| SMB 带宽限制 | “新建” | 你现在可以使用[SmbBandwidthLimit](https://docs.microsoft.com/powershell/module/smbshare/set-smbbandwidthlimit)来设置三个类别中的带宽限制： VirtualMachine （HYPER-V over smb 流量）、LiveMigration （hyper-v 实时迁移流量 over smb）或默认值（所有其他类型的 smb 通信）。

有关 Windows Server 2012 R2 中新的和更改的 SMB 功能的详细信息，请参阅[Windows server 中 smb 的新增](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831474(v%3dws.11)>)功能。

## <a name="features-added-in-smb-30-with-windows-server-2012-and-windows-8"></a>在 SMB 3.0 中添加的功能与 Windows Server 2012 和 Windows 8

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| SMB 透明故障转移     |   “新建”    | 让管理员可执行群集文件服务器中节点的硬件或软件维护，且不会中断将数据存储在这些文件共享上的服务器应用程序。 此外，如果群集节点出现硬件或软件故障，SMB 客户端将以透明方式重新连接到其他群集节点，且不会中断将数据存储在这些文件共享上的服务器应用程序。        |
| SMB 横向扩展     |   “新建”      | 支持横向扩展文件服务器上的多个 SMB 实例。 使用群集共享卷 (CSV) 版本 2 时，管理员可以通过文件服务器群集中的所有节点，创建可供同时访问含直接 I/O 的数据文件的文件共享。 这可更好地利用文件服务器客户端的网络带宽和负载平衡，以及优化服务器应用程序的性能。  |
| SMB 多通道     |   “新建”      |  如果 SMB 客户端和服务器之间有多个路径，则启用网络带宽和网络容错的聚合。 这让服务器应用程序可以充分利用可用网络带宽并在发生网络故障时恢复。<br><br>与以前的 SMB 版本相比，SMB 3 中的 SMB 多通道可大大提高性能。 |
| SMB 直通     |   “新建”      | 支持使用具有 RDMA 功能且可全速运行的网络适配器，其中延迟非常低且 CPU 非常少。 对于 Hyper-V 或 Microsoft SQL Server 等工作负载，这让远程文件服务器如同本地存储一样。<br><br>与以前的 SMB 版本相比，SMB 3 中的 SMB Direct 可大大提高性能。  |
| 用于服务器应用程序的性能计数器     |   “新建”      |  新的 SMB 性能计数器提供有关吞吐量、延迟和每秒 i/o 数（IOPS）的详细、每次共享的信息，允许管理员分析存储数据的 SMB 文件共享的性能。 这些计数器专为将文件存储在远程文件共享上的服务器应用程序而设计，如 Hyper-V 和 SQL Server。      |
| 性能优化    |  已更新   | SMB 客户端和服务器都已针对小型随机读/写 i/o 进行了优化，这在服务器应用程序（如 SQL Server OLTP）中很常见。 此外，默认情况下打开大型最大传输单元 (MTU)，这将大幅提高大型连续传输性能，如 SQL Server 数据仓库、数据库备份或还原、部署或复制虚拟硬盘。 |
| SMB-专用 Windows PowerShell cmdlet     |   “新建”      |  借助用于 SMB 的 Windows PowerShell cmdlet，管理员可以从命令行以端对端方式管理文件服务器上的文件共享。   |
| SMB 加密     |   “新建”      | 提供 SMB 数据的端对端加密并防止数据在未受信任网络中遭受窃听。 无需新部署成本，且无需 Internet 协议安全性 (IPsec)、专用硬件或 WAN 加速器。 它可按共享配置，也可针对整个文件服务器配置，并且可针对数据遍历未受信任网络的各种方案启用。 |
| SMB 目录租用     |  “新建” | 缩短分支机构的应用程序响应时间。 使用目录租用后，缩短了从客户端到服务器的往返时间，因为是从保留时间较长的目录缓存中检索元数据。 缓存一致性得到保持，因为在服务器上的目录信息更改时将通知客户端。 目录租约适用于主文件夹（读/写，无共享）和发布（具有共享的只读）的方案。    |
| 广域网性能   | “新建”   | SMB 3.0 中引入了目录机会锁（oplock）和 oplock 租约。 对于典型的办公/客户端工作负荷，会显示 oplock/租约，以将网络往返次数减少大约15%。<br><br>在 SMB 3 中，SMB 的 Windows 实现已经过优化，可改善客户端上的缓存行为，并能够推送更高的吞吐量。<br><br>SMB 3 提供了对 CopyFile （） API 以及相关工具（如 Robocopy）的改进，以便在网络上推送更多的数据。 |
| 安全方言协商 | “新建” | 可帮助防止中间人尝试降级方言协商。 其思路是防止窃听者在客户端和服务器之间降级最初协商的方言和功能。 有关详细信息，请参阅[SMB3 安全方言方言协商](https://docs.microsoft.com/archive/blogs/openspecification/smb3-secure-dialect-negotiation)。 请注意，此功能已被 SMB 3.1.1 中[Windows 10 功能的 smb 3.1.1 预身份验证完整性](https://docs.microsoft.com/archive/blogs/openspecification/smb-3-1-1-pre-authentication-integrity-in-windows-10)取代。 |


## <a name="hardware-requirements"></a>硬件要求

SMB 透明故障转移具有以下要求：

* 运行 Windows Server 2012 或 Windows Server 2016 且至少配置了两个节点的故障转移群集。 群集必须通过验证向导中包括的群集验证测试。
* 必须使用连续可用性 (CA) 属性（默认值）创建文件共享。
* 必须在 CSV 卷路径上创建文件共享，才能获得 SMB 横向扩展。
* 客户端计算机必须运行 Windows®8或 Windows Server 2012，两者均包括支持连续可用性的更新 SMB 客户端。

> [!NOTE]
> 下级客户端可以连接到具有 CA 属性的文件共享，但这些客户端不支持透明故障转移。

SMB 多通道具有以下要求：

* 至少需要两台运行 Windows Server 2012 的计算机。 无需安装额外功能 - 该技术默认情况下处于打开状态。
* 有关建议的网络配置的信息，请参阅本概述主题末尾的“另请参阅”部分。

SMB 直接具有以下要求：

* 至少需要两台运行 Windows Server 2012 的计算机。 无需安装额外功能 - 该技术默认情况下处于打开状态。
* 需要含 RDMA 功能的网络适配器。 目前，这些适配器有三种类型：iWARP、Infiniband 或 RoCE (RDMA over Converged Ethernet)。

## <a name="more-information"></a>详细信息

以下列表提供了有关 Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2016 中的 SMB 和相关技术的其他资源。

* [Windows Server 中的存储](../storage.md)
* [应用程序数据的横向扩展文件服务器](../../failover-clustering/sofs-overview.md)
* [使用 SMB 直通提高文件服务器的性能](smb-direct.md)
* [部署基于 SMB 的 Hyper-v](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134187(v%3dws.11)>)
* [部署 SMB 多通道](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn610980(v%3dws.11)>)
* [为服务器应用程序部署快速且高效的文件服务器](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831723(v%3dws.11)>)
* [SMB：故障排除指南](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn659439(v%3dws.11)>)
