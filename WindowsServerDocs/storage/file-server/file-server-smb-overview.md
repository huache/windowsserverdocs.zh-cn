---
title: 使用 Windows Server 中的 SMB 3 协议的文件共享概述
description: 使用 Windows Server 中的 SMB 3 协议进行文件共享和文件服务的概述。
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.date: 01/10/2020
ms.localizationpriority: medium
ms.openlocfilehash: 1b9ff2ccd63adc7edd7503d3eff695d09b806f7a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954734"
---
# <a name="overview-of-file-sharing-using-the-smb-3-protocol-in-windows-server"></a>使用 Windows Server 中的 SMB 3 协议的文件共享概述

>适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本主题介绍 Windows Server 2019、Windows Server 2016、Windows Server 2012 R2 和 Windows Server 2012 中的 SMB 3 功能，包括功能的实际应用、相对于以前版本此版本的最重要新功能或更新功能以及硬件要求。 SMB 也是由[软件定义数据中心 (SDDC)](../../sddc.md) 解决方案（如存储空间直通、存储副本和其他）使用的结构协议。 SMB 版本 3.0 已引入到 Windows Server 2012 中，并在后续版本中不断得到改进。

## <a name="feature-description"></a>功能描述

服务器消息块 (SMB) 协议是网络文件共享协议，让计算机上的应用程序可读取和写入文件以及从计算机网络中的服务器程序请求服务。 SMB 协议可在其 TCP/IP 协议或其他网络协议上使用。 使用 SMB 协议时，应用程序（或应用程序用户）可访问远程服务器上的文件或其他资源。 这让应用程序可以读取、创建和更新远程服务器上的文件。 SMB 还可以与任何设置为接收 SMB 客户端请求的服务器程序通信。 SMB 是由软件定义数据中心 (SDDC) 计算技术（如存储空间直通、存储副本）使用的结构协议。 有关详细信息，请参阅 [Windows Server 软件定义数据中心](../../sddc.md)。

## <a name="practical-applications"></a>实际的应用程序

本节讨论一些使用新 SMB 3.0 协议的全新实用方法。

* **用于虚拟化的文件存储 (Hyper-V(TM) over SMB)** 。 Hyper-V 可以通过 SMB 3.0 协议在文件共享中存储虚拟机文件，如配置、虚拟硬盘 (VHD) 文件和快照。 这既可用于独立文件服务器，又可用于将 Hyper-V 与群集的共享文件存储配合使用的群集文件服务器。
* **Microsoft SQL Server over SMB**。 SQL Server 可以将用户数据库文件存储在 SMB 文件共享中。 目前，SQL Server 2008 R2 的独立 SQL 服务器支持此功能。 即将推出的 SQL Server 版本将增加群集 SQL 服务器和系统数据库的支持。
* **用于最终用户数据的传统存储**。 SMB 3.0 协议提供 信息工作者 （或客户端）工作负载的增强功能。 这些增强功能包括减少分支机构用户在通过广域网 (WAN) 访问数据时遇到的应用程序延迟，以及防止数据遭受窃听攻击。

## <a name="new-and-changed-functionality"></a>新功能和更改的功能

以下各部分介绍 SMB 3 中添加的功能以及后续更新。

## <a name="features-added-in-windows-server-2019-and-windows-10-version-1809"></a>Windows Server 2019 和 Windows 10 版本 1809 中添加的功能

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| 要求对无法连续使用的文件共享上的磁盘进行连续写入的功能 | “新建” | 若要提供一些写入文件共享的补充保证，使其在写入操作返回完成之前通过软件和硬件堆栈进入物理磁盘，可使用 `NET USE /WRITETHROUGH` 命令或 `New-SMBMapping -UseWriteThrough` PowerShell cmdlet 对文件共享启用连续写入操作。 使用连续写入会造成一些性能影响；有关进一步讨论，请参阅博客文章[控制 SMB 中的连续写入行为](https://techcommunity.microsoft.com/t5/storage-at-microsoft/controlling-write-through-behaviors-in-smb/bc-p/1083417#M677)。 |

## <a name="features-added-in-windows-server-version-1709-and-windows-10-version-1709"></a>Windows Server 版本 1709 和 Windows 10 版本 1709 中添加的功能

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| 禁止对文件共享的来宾访问权限 | “新建” | SMB 客户端不再允许执行以下操作：对远程服务器的来宾帐户访问权限；提供无效凭据后回退到来宾帐户。 有关详细信息，请参阅 [Windows 中默认禁用 SMB2 中的来宾访问权限](https://support.microsoft.com/help/4046019/guest-access-in-smb2-disabled-by-default-in-windows-10-and-windows-ser)。 |
| SMB 全局映射 | “新建” | 将远程 SMB 共享映射到本地主机上的所有用户（包括容器）可访问的驱动器号。 这是使数据卷上的容器 I/O 能够遍历远程装入点的必要操作。 请注意，对容器使用 SMB 全局映射时，容器主机上的所有用户都可以访问远程共享。 在容器主机上运行的任何应用程序也有权访问映射的远程共享。 有关详细信息，请参阅[群集共享卷 (CSV)、存储空间直通、SMB 全局映射的容器存储支持](https://techcommunity.microsoft.com/t5/failover-clustering/container-storage-support-with-cluster-shared-volumes-csv/ba-p/372140)。 |
| SMB 方言控制 | “新建” | 现在可以设置注册表值以控制所使用的最低 SMB 版本（方言）和最高 SMB 版本。 有关详细信息，请参阅[控制 SMB 方言](https://techcommunity.microsoft.com/t5/storage-at-microsoft/controlling-smb-dialects/ba-p/860024)。 |

## <a name="features-added-in-smb-311-with-windows-server-2016-and-windows-10-version-1607"></a>Windows Server 2016 和 Windows 10 版本 1607 的 SMB 3.11 中添加的功能

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| SMB 加密     |   已更新      | 使用高级加密标准-Galois/计数器模式 (AES-GCM) 的 SMB 3.1.1 加密比使用 AES-CCM 的 SMB 签名或之前的 SMB 加密更快。   |
| 目录缓存 | “新建” | SMB 3.1.1 包括目录缓存的增强功能。 Windows 客户端现在可以缓存更大的目录，大约 50 万个条目。 Windows 客户端将尝试使用 1 MB 缓冲区进行目录查询，以减少往返并提高性能。 |
| 预身份验证完整性 | “新建” |  在 SMB 3.1.1 中，预身份验证完整性提供改进的防护，可防止中间人攻击者篡改 SMB 的连接建立和身份验证消息。 有关详细信息，请参阅 [Windows 10 中的 SMB 3.1.1 预身份验证完整性](/archive/blogs/openspecification/smb-3-1-1-pre-authentication-integrity-in-windows-10)。 |
| SMB 加密改进 | “新建” | SMB 3.1.1 提供一种用于协商每个连接的加密算法的机制，以及 AES-128-CCM 和 AES-128-GCM 选项。 AES-128-GCM 是新的 Windows 版本的默认选项，而较旧的版本将继续使用 AES-128-CCM。 |
| 滚动群集升级支持 | “新建” | 通过让 SMB 在升级过程中支持用于群集的 SMB 的不同最高版本，启用[滚动群集升级](../../failover-clustering/cluster-operating-system-rolling-upgrade.md)。 有关让 SMB 使用协议的不同版本（方言）进行通信的详细信息，请参阅博客文章[控制 SMB 方言](https://techcommunity.microsoft.com/t5/storage-at-microsoft/controlling-smb-dialects/ba-p/860024)。 |
| Windows 10 中的 SMB 直通客户端支持 | “新建” | Windows 10 企业版、Windows 10 教育版和 Windows 10 专业工作站版现已添加 SMB 直通客户端支持。 |
| 对 FileNormalizedNameInformation API 调用的本机支持 | “新建” | 添加了对查询文件的规范化名称的本机支持。 有关详细信息，请参阅 [FileNormalizedNameInformation](/openspecs/windows_protocols/ms-fscc/20bcadba-808c-4880-b757-4af93e41edf6)。 |

有关更多详细信息，请参阅博客文章 [Windows Server 2016 技术预览版 2 中 SMB 3.1.1 的新增功能](/archive/blogs/josebda/whats-new-in-smb-3-1-1-in-the-windows-server-2016-technical-preview-2)。

## <a name="features-added-in-smb-302-with-windows-server-2012-r2-and-windows-81"></a>Windows Server 2012 R2 和 Windows 8.1 的 SMB 3.02 中添加的功能

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| 自动重新平衡横向扩展文件服务器客户端     |   “新建”      | 改进了横向扩展文件服务器的可伸缩性和可管理性。 将按照每个文件共享（而不是每个服务器）跟踪 SMB 客户端连接，然后将客户端重定向到群集节点，并让用户最方便地访问文件共享使用的卷。 这样便会减少文件服务器节点之间的重定向流量，从而提高效率。 在建立初始连接后以及在重新配置群集存储时，将重定向客户端。    |
| WAN 的性能   | 已更新  | 当使用文件资源管理器将远程计算机上某个位置的远程副本复制到同一服务器上的另一副本时，Windows 8.1 和 Windows 10 通过 SMB 支持提供改进的 CopyFile SRV_COPYCHUNK。 将仅通过网络复制少量元数据（每 16MiB 传输 1/2KiB 的文件数据）。 这样可以显著提高性能。 这是 SMB 的 OS 级别和文件资源管理器级别的区别。 |
| SMB 直通     |   已更新      | 托管包含小规模 I/O 的工作负载（例如，虚拟机中的联机事务处理 (OLTP) 数据库）时，通过提高效率来优化小规模 I/O 工作负载的性能。 使用较高速度的网络接口（例如 40 Gbps 以太网和 56 Gbps InfiniBand）时，这些改进是很明显的。  |
| SMB 带宽限制 | “新建” | 现在可以使用 [Set-SmbBandwidthLimit](/powershell/module/smbshare/set-smbbandwidthlimit) 来设置三种类别的宽带限制：VirtualMachine（基于 SMB 的 Hyper-V 流量）、LiveMigration（基于 SMB 的 Hyper-V 实时迁移流量）或 Default（所有其他类型的 SMB 流量）。

有关 Windows Server 2012 R2 中新增和更改的 SMB 功能的详细信息，请参阅 [Windows Server 中 SMB 的新增功能](</previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831474(v%3dws.11)>)。

## <a name="features-added-in-smb-30-with-windows-server-2012-and-windows-8"></a>Windows Server 2012 和 Windows 8 的 SMB 3.0 中添加的功能

| 特性/功能  | 新功能或更新功能  | 摘要  |
| --------- | --------- | --------- |
| SMB 透明故障转移     |   “新建”    | 让管理员可执行群集文件服务器中节点的硬件或软件维护，且不会中断将数据存储在这些文件共享上的服务器应用程序。 此外，如果群集节点出现硬件或软件故障，SMB 客户端将以透明方式重新连接到其他群集节点，且不会中断将数据存储在这些文件共享上的服务器应用程序。        |
| SMB 横向扩展     |   “新建”      | 支持一个横向扩展文件服务器上的多个 SMB 实例。 使用群集共享卷 (CSV) 版本 2 时，管理员可以通过文件服务器群集中的所有节点，创建可供同时访问含直接 I/O 的数据文件的文件共享。 这可更好地利用文件服务器客户端的网络带宽和负载平衡，以及优化服务器应用程序的性能。  |
| SMB 多通道     |   “新建”      |  如果在 SMB 客户端和服务器之间有多个可用路径，则支持网络带宽和网络容错的聚合。 这让服务器应用程序可以充分利用可用网络带宽并在发生网络故障时恢复。<br><br>与以前版本的 SMB 相比，SMB 3 中的 SMB 多通道显著提高了性能。 |
| SMB 直通     |   “新建”      | 支持使用具有 RDMA 功能且可全速运行的网络适配器，其中延迟非常低且 CPU 非常少。 对于 Hyper-V 或 Microsoft SQL Server 等工作负载，这让远程文件服务器如同本地存储一样。<br><br>与以前版本的 SMB 相比，SMB 3 中的 SMB 直通显著提高了性能。  |
| 用于服务器应用程序的性能计数器     |   “新建”      |  新增的 SMB 性能计数器提供有关吞吐量、延迟和 I/O/秒 (IOPS) 的按共享列出的详细信息，从而让管理员可以分析用于存储数据的 SMB 文件共享的性能。 这些计数器专为将文件存储在远程文件共享上的服务器应用程序而设计，如 Hyper-V 和 SQL Server。      |
| 性能优化    |  已更新   | SMB 客户端和服务器均已针对小型随机读/写 I/O 进行了优化，此类 I/O 在 SQL Server OLTP 等服务器应用程序中很常见。 此外，默认情况下打开大型最大传输单元 (MTU)，这将大幅提高大型连续传输性能，如 SQL Server 数据仓库、数据库备份或还原、部署或复制虚拟硬盘。 |
| SMB-专用 Windows PowerShell cmdlet     |   “新建”      |  借助用于 SMB 的 Windows PowerShell cmdlet，管理员可以从命令行以端对端方式管理文件服务器上的文件共享。   |
| SMB 加密     |   “新建”      | 提供 SMB 数据的端对端加密并防止数据在未受信任网络中遭受窃听。 无需新部署成本，且无需 Internet 协议安全性 (IPsec)、专用硬件或 WAN 加速器。 它可按共享配置，也可针对整个文件服务器配置，并且可针对数据遍历未受信任网络的各种方案启用。 |
| SMB 目录租用     |  “新建” | 缩短分支机构的应用程序响应时间。 使用目录租用后，缩短了从客户端到服务器的往返时间，因为是从保留时间较长的目录缓存中检索元数据。 缓存一致性得到保持，因为在服务器上的目录信息更改时将通知客户端。 目录租用适用于主文件夹（读/写，无共享）和发布（只读，带共享）。    |
| WAN 的性能   | “新建”   | 目录操作锁定 (oplock) 和 oplock 租用已在 SMB 3.0 中引入。 对于典型办公/客户端工作负载，会显示 oplock/租用以减少约 15% 的网络往返。<br><br>在 SMB 3 中，SMB 的 Windows 实现已经过优化，以改善客户端的缓存性能以及提高吞吐量的能力。<br><br>SMB 3 改进了 CopyFile() API 和相关工具（例如 Robocopy），以显著增加通过网络推送的数据。 |
| 安全方言协商 | “新建” | 有助于防止中间人降级方言协商的企图。 目的是防止窃听者降级客户端和服务器之间的初始协商方言和功能。 有关详细信息，请参阅 [SMB3 安全方言协商](/archive/blogs/openspecification/smb3-secure-dialect-negotiation)。 请注意，此功能已由 SMB 3.1.1 中 [Windows 10 中的 SMB 3.1.1 预身份验证完整性](/archive/blogs/openspecification/smb-3-1-1-pre-authentication-integrity-in-windows-10)功能取代。 |


## <a name="hardware-requirements"></a>硬件要求

SMB 透明故障转移具有以下要求：

* 运行 Windows Server 2012 或 Windows Server 2016 且至少配置两个节点的故障转移群集。 群集必须通过验证向导中包括的群集验证测试。
* 必须使用连续可用性 (CA) 属性（默认值）创建文件共享。
* 必须在 CSV 卷路径上创建文件共享，才能获得 SMB 横向扩展。
* 客户端计算机必须运行 Windows® 8 或 Windows Server 2012，且两者均包括支持连续可用性的更新的 SMB 客户端。

> [!NOTE]
> 下级客户端可以连接到具有 CA 属性的文件共享，但这些客户端将不支持透明故障转移。

SMB 多通道具有以下要求：

* 至少需要两台运行 Windows Server 2012 的计算机。 无需安装额外功能 - 该技术默认情况下处于打开状态。
* 有关建议的网络配置的信息，请参阅本概述主题末尾的“另请参阅”部分。

SMB 直接具有以下要求：

* 至少需要两台运行 Windows Server 2012 的计算机。 无需安装额外功能 - 该技术默认情况下处于打开状态。
* 需要含 RDMA 功能的网络适配器。 目前，这些适配器有三种类型：iWARP、Infiniband 或 RoCE (RDMA over Converged Ethernet)。

## <a name="more-information"></a>详细信息

以下列表提供有关 Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2016 中的 SMB 和相关技术的 Web 附加资源。

* [Windows Server 中的存储](../storage.yml)
* [应用程序数据横向扩展文件服务器](../../failover-clustering/sofs-overview.md)
* [通过 SMB 直通优化文件服务器的性能](smb-direct.md)
* [部署基于 SMB 的 Hyper-V](</previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134187(v%3dws.11)>)
* [部署 SMB 多通道](</previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn610980(v%3dws.11)>)
* [针对服务器应用程序部署快速且高效的文件服务器](</previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831723(v%3dws.11)>)
* [SMB：故障排除指南](</previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn659439(v%3dws.11)>)
