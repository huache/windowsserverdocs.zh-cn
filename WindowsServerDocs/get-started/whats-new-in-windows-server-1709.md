---
title: Windows Server 版本 1709 中的新增功能
description: 计算、标识、管理、自动化、网络、安全性、存储方面的新增功能。
ms.topic: article
ms.author: lizross
author: eross-msft
manager: mtillman
ms.localizationpriority: medium
ms.date: 06/03/2019
ms.openlocfilehash: 2202658da6d89d3a289e0fd1e6df07e9ba4e4544
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621989"
---
# <a name="whats-new-in-windows-server-version-1709"></a>Windows Server 版本 1709 中的新增功能

> 适用于：Windows Server（半年频道）

<img src=../media/landing-icons/new.png style='float:left; padding:.5em;' alt=Icon showing a newspaper>&nbsp;若要了解 Windows 中的最新功能，请参阅 [Windows Server 中的新增功能](whats-new-in-windows-server.md)。 本部分的内容介绍 Windows Server 版本 1709 中的新增功能和更改的功能。 此处列出的新功能和更改在你使用此版本时最可能具有最大影响力。 另请参阅 [Windows Server 版本 1709](https://cloudblogs.microsoft.com/windowsserver/2017/08/24/sneak-peek-1-windows-server-version-1709/)。

> [!IMPORTANT]
> 从 2019 年 4 月 9 日开始，Windows Server 版本 1709 不再接受支持。

## <a name="new-cadence-of-releases"></a>新的发布节奏

从此版本开始，可以采用以下两个选项来接收 Windows Server 功能更新：
- **长期服务频道 (LTSC)** ：这是像往常一样的业务，包含 5 年的主要支持和 5 年的外延支持。 可以选择以过去 20 年一直支持的相同方法每 2-3 年升级到下一个 LTSC 版本。
- **半年频道 (SAC)** ：这是一项软件保障权益，并且在生产中完全受支持。 区别在于其支持期为 18 个月，并且每六个月将推出一个新版本。

下表概述了版本频道。

| 说明 | 半年频道 | 长期服务频道 |
| ------------- |--| -- |
| 发布节奏 | 每年两次（春季和秋季） | 每 2 - 3 年 |
| 支持计划 | 18 个月主要生产支持 | 5 年主要支持 + 5 年外延支持 |
| 可用性 | 软件保障或 Azure（云托管） | 全部频道 |
| 命名约定 | Windows Server 版本 YYMM | Windows Server YYYY |

有关详细信息，请参阅[服务渠道的比较](../get-started-19/servicing-channels-19.md)。

## <a name="application-containers-and-micro-services"></a>应用程序容器和微服务

- Server Core 容器映像已针对可通过极少量更改将现有代码库或应用程序迁移到容器中的直接迁移方案进行了进一步优化，而且还缩小了 60%。
- Nano Server 容器映像几乎缩小了 80%。
    - 在 Windows Server 半年频道中，Nano Server 作为容器基本 OS 映像从 390 MB 降低到了 80 MB。
- 带 Hyper-V 隔离的 Linux 容器

有关详细信息，请参阅 [Windows Server 的下一个版本中对 Nano Server 进行的更改](./nano-in-semi-annual-channel.md)以及[适用于开发人员的 Windows Server 版本 1709](https://cloudblogs.microsoft.com/windowsserver/2017/09/13/sneak-peek-3-windows-server-version-1709-for-developers/)。

## <a name="modern-management"></a>现代管理

查看 [Project Honolulu](../manage/windows-admin-center/overview.md)，以了解简化、集成、安全的体验，从而帮助 IT 管理员管理核心疑难解答、配置和维护方案。  Project Honolulu 包括具有简化、集成、安全且可扩展的界面的下一代工具。
Project Honolulu 可提供直观的全新管理体验，用于管理电脑、Windows Server、故障转移群集以及基于存储空间直通的超融合基础设施，并降低运营成本。

## <a name="compute"></a>计算

**Nano 容器和 Server Core 容器**：首先且最重要的是，此版本与推动应用程序创新相关。 Nano Server 或 Nano 型主机已被弃用并且被 Nano 容器所取代，此容器是作为容器映像运行的 Nano。

有关容器的详细信息，请参阅[容器网络概述](../networking/sdn/technologies/containers/container-networking-overview.md)。

**用作容器的 Server Core**（和基础结构）主机可在现代化过程中为现有应用程序提供更好的灵活性、密度和性能，并且可以为已使用云模型开发的新应用打造品牌。

**VM 启动排序**也改进了 OS 和应用程序感知，提供增强的触发器，在一个 VM 已启动、下一个 VM 未启动时触发。

利用**对 VM 的存储类内存支持**，可以在非易失性 DIMM 上创建 NTFS 格式的直接访问卷，并且可以向 Hyper-V VM 公开这些卷。 这使 Hyper-V VM 能够利用存储类内存设备的低延迟性能优势。

**虚拟化永久内存 (vPMEM)** 的启用方式如下：在主机上的直接访问卷上创建一个 VHD 文件 (.vhdpmem)、向 VM 添加一个 vPMEM 控制器，并向 VM 添加创建的设备 (.vhdpmem)。 通过使用主机中直接访问卷上的 vhdpmem 文件来支持 vPMEM，可以灵活地进行分配，并且可以利用熟悉的管理模式向 VM 添加磁盘。

**容器存储 – 群集共享卷 (CSV) 上的永久数据卷**。 在 Windows Server 版本 1709 以及具有最新更新的 Windows Server 2016 中，我们为容器添加了支持，以便访问位于 CSV（包括存储空间直通上的 CSV）上的永久数据卷。 无论容器实例正在哪个群集节点上运行，这都会为应用程序容器提供对卷的永久访问权限。 有关详细信息，请参阅[群集共享卷 (CSV)、存储空间直通 (S2D)、SMB 全局映射的容器存储支持](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering)。

**容器存储 – 永久数据卷与 SMB 全局映射**。 在 Windows Server 版本 1709 中，我们添加了支持以支持将 SMB 文件共享映射到容器内的驱动器号 - 这种映射称为 SMB 全局映射。 此映射的驱动器以后可供本地服务器上的所有用户访问，以便数据卷上的容器 I/O 可以经安装的驱动器到达基础文件共享。 有关详细信息，请参阅[群集共享卷 (CSV)、存储空间直通 (S2D)、SMB 全局映射的容器存储支持](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering)。

**虚拟机配置文件格式（已更新）** 。 已经为配置版本为 8.2 和更高版本的虚拟机额外添加了一个文件 (.vmgs)。 VMGS 指 VM 来宾状态，是一个新的内部文件，其中包括以前属于 VM 运行时状态文件一部分的设备状态。

## <a name="security-and-assurance"></a>安全和保障

利用**网络加密**，你可以对软件定义网络基础结构上的网络段快速进行加密，以满足安全性和合规性需求。

**主机保护者服务 (HGS)** 作为受防护的 VM 处于启用状态。 在此版本之前，我们的建议是部署一个 3 节点物理群集。 虽然这可以确保管理员不会危害 HGS 环境，但通常成本高昂。

**Linux 作为受防护的 VM** 现在受支持。

有关详细信息，请参阅[受保护的结构和受防护的 VM 概述](../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms.md)。

**SMBLoris 漏洞**：一个被称为“SMBLoris”、可能导致拒绝服务的问题已得到解决。

## <a name="storage"></a>存储

**存储副本**：由 Windows Server 2016 中的存储副本添加的灾难恢复保护现在进行了扩展，其中包括：
- **测试故障转移**：现在可以通过测试故障转移功能来选择安装目标存储。 可以在目标节点上临时安装复制的存储的快照以便进行测试或备份。  有关详细信息，请参阅[有关存储副本的常见问题](https://aka.ms/srfaq)。
- **Project Honolulu 支持**：Project Honolulu 中现在提供对服务器到服务器复制图形管理的支持。 这不需要使用 PowerShell 来管理常见的灾难保护工作负荷。

**SMB**：
- **SMB1 和来宾身份验证删除**：默认情况下，Windows Server 版本 1709 不再安装 SMB1 客户端和服务器。 此外，SMB2 及更高版本中作为来宾进行身份验证的功能默认情况下处于关闭状态。 有关详细信息，请查看[默认情况下，Windows 10 版本 1709 和 Windows Server 版本 1709 中未安装 SMBv1](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows-10-rs3-and-windows-server)。

- **SMB2/SMB3 安全性和兼容性**：添加了安全性和应用程序兼容性的附加选项（包括针对旧版应用程序在 SMB2+ 中禁用 oplock 的功能），并且这些选项要求从客户端对每个连接都进行签名或加密。 有关详细信息，请查看 SMBShare PowerShell 模块帮助。

**重复数据删除**：
- **重复数据删除现在支持 ReFS**：不再需要在现代 ReFS 文件系统的优势与重复数据删除功能之间进行选择：现在，只要可以启用 ReFS，就可以启用重复数据删除。 使用 ReFS 将存储效率提高 95% 以上。
- **适用于删除了重复数据的卷优化入口/出口的 DataPort API**：开发人员现在可以利用重复数据删除功能所了解的高效数据存储方式，在卷、服务器和群集之间高效移动数据。

## <a name="remote-desktop-services-rds"></a>远程桌面服务 (RDS)

**RDS 已与 Azure AD 集成**，因此客户可以利用条件访问策略、多重身份验证、使用 Azure AD的其他 SaaS 应用的集成身份验证等等。 有关详细信息，请参阅[将 Azure AD 域服务与 RDS 部署集成](../remote/remote-desktop-services/rds-azure-adds.md)。

>[!TIP]
>若要抢先预览即将对 RDS 做出的其他令人兴奋的改进，请参阅[远程桌面服务：更新和即将推出的创新](https://techcommunity.microsoft.com/t5/microsoft-security-and/first-look-at-updates-coming-to-remote-desktop-services/ba-p/250320)

## <a name="networking"></a>网络

**Docker 的路由网**受支持。 入口路由网是[群模式](https://docs.docker.com/engine/swarm/)的一部分，群模式是 Docker 的内置容器编排解决方案。 有关详细信息，请参阅[适用于 Windows Server 版本 1709 的 Docker 路由网](https://techcommunity.microsoft.com/t5/virtualization/bg-p/Virtualization)。

**Docker 的新功能**可供使用。 有关详细信息，请参阅 [Windows Server 1709 的令人兴奋的 Docker 新功能](https://blog.docker.com/2017/09/docker-windows-server-1709/)。

**Windows 网络与适用于 Kubernetes 的 Linux 不相上下**：Windows 现在与 Linux 在网络方面不相上下。 在任何包括 Azure 的环境中、在本地以及在包含 Linux 所支持的相同网络基元和拓扑的第三方云堆栈上，客户可以部署混合 OS、Kubernetes 群集，而无需使用任何解决方法或交换机扩展。

**核心网络堆栈**：核心网络堆栈的一些功能有了改进。 有关这些功能的详细信息，请参阅 [Windows 10 创意者更新中的核心网络堆栈功能](https://techcommunity.microsoft.com/t5/networking-blog/bg-p/NetworkingBlog)。
- **TCP 快速打开 (TFO)** ：添加了对 TFO 的支持以优化 TCP 3 方握手过程。 TFO 使用标准 3 方握手在首次连接中建立安全的 TFO Cookie。  以后连接到同一服务器时，会使用 TFO Cookie 代替 3 方握手进行连接，因此行程往返时间为零。
- **CUBIC**：CUBIC 的实验性 Windows 本机实现（TCP 拥塞控制算法）可供使用。 以下命令可分别启用或禁用 CUBIC。

    ```
    netsh int tcp set supplemental template=internet congestionprovider=cubic
    netsh int tcp set supplemental template=internet congestionprovider=compound
    ```

- **接收窗口自动调整**：TCP 自动调整逻辑会计算 TCP 连接的“接收窗口”参数。  高速和/或长延迟连接需要使用该算法来实现良好的性能特征。  在此版本中，该算法经过了修改，以使用阶梯函数收敛给定连接的最大接收窗口值。
- **TCP 统计数据 API**：引入了一个名为 SIO_TCP_INFO 的新 API。  SIO_TCP_INFO 允许开发人员使用套接字选项查询有关各个 TCP 连接的大量信息。
- **IPv6**：在此版本中，IPv6 有多项改进。
  - **RFC 6106** 支持：RFC 6106 允许通过路由器播发 (RA) 来配置 DNS。 可以使用以下命令启用或禁用 RFC 6106 支持：

    ```
    netsh int ipv6 set interface <ifindex> rabaseddnsconfig=<enabled | disabled>
    ```

  - **流标签**：从创意者更新开始，已针对通过 IPv6 传输的出站 TCP 和 UDP 数据包将此字段设置为 5 元组哈希（源 IP、目标 IP、源端口、目标端口）。  这将使纯 IPv6 型数据中心能够更有效地进行负载平衡或流分类。 若要启用流标签，请执行以下命令：

    ```
    netsh int ipv6 set flowlabel=[disabled|enabled] (enabled by default)
    netsh int ipv6 set global flowlabel=<enabled | disabled>
    ```

  - **ISATAP 和 6to4**：作为未来弃用过程中的一个步骤，创意者更新默认情况下将禁用这些技术。
- **间隔网关检测 (DGD)** ：当前网关无法访问时，DGD 算法会将连接自动转换到另一个网关。 在此版本中，此算法经过了改进以定期重新探测网络环境。
- [Test-NetConnection](/powershell/module/nettcpip/test-netconnection?view=win10-ps) 是 Windows PowerShell 中的内置 cmdlet，可执行各种网络诊断。  在此版本中，我们增强了 cmdlet 以提供有关路由选择以及源地址选择的详细信息。

**软件定义的网络**

- **虚拟网络加密**是一项新功能，能够在标记为“启用加密”的子网内相互通信的虚拟机之间加密虚拟网络流量。 该功能利用虚拟子网上的数据报传输层安全 (DTLS) 功能来加密数据包。  DTLS 可以防止能够访问物理网络的任何人进行窃听、篡改和伪造。

**Windows 10 VPN**

- **预登录基础结构隧道**。 默认情况下，当用户未登录其计算机或设备时，Windows 10 VPN 不会自动创建基础结构隧道。 可将 Windows 10 VPN 配置为使用 VPN 配置文件中的设备隧道 (prelogon) 功能自动创建预登录基础结构隧道。
- **远程计算机和设备的管理**。  可以通过在 VPN 配置文件中配置设备隧道 (prelogon) 功能来管理 Windows 10 VPN 客户端。 此外，必须将 VPN 连接配置为动态注册通过内部 DNS 服务分配给 VPN 接口的 IP 地址。
- **指定预登录网关**。 可以在 VPN 配置文件中指定具有设备隧道 (prelogon) 功能的预登录网关，并结合流量筛选器，来控制可以通过设备隧道访问公司网络上的哪些管理系统。
