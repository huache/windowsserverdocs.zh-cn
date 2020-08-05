---
title: Windows Server 软件定义数据中心
Description: Windows Server SDDC 概述
ms.prod: windows-server
ms.technology: SDDC
ms.topic: get-started article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 06/04/2019
ms.localizationpriority: medium
ms.openlocfilehash: ceab6f99617bcb2e5581f6ea975ea8a71a2ea4b3
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409958"
---
# <a name="windows-server-software-defined-datacenter"></a>Windows Server 软件定义数据中心

>适用于：Windows Server 2019、Windows Server 2016

![标题图像](media/sddc/heading.png)

## <a name="what-is-windows-server-software-defined-datacenter"></a>什么是 Windows Server 软件定义数据中心？

软件定义数据中心 (SDDC) 是一个常用的行业术语，通常是指虚拟化整个基础结构所在的数据中心。 虚拟化是关键，它只意味着数据中心内硬件和软件的扩展超出了传统的一对一比例。 利用模拟硬件的软件虚拟机监控程序，操作系统和应用程序可以抽象自物理硬件并进行倍增，以形成处理器、内存、I/O 和网络的弹性资源池。

Microsoft 的 SDDC 实现包含本文重点介绍的 Windows Server 技术。 它从提供虚拟化平台来构建网络和存储的 Hyper-V 虚拟机监控程序开始。 针对虚拟化基础结构的独特挑战而开发的安全技术可减轻内部和外部威胁。 通过使用内置于 Windows Server 的 PowerShell 并添加 [System Center](https://docs.microsoft.com/system-center/) 和/或 [Operations Management Suite](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)，可进行编程并自动执行预配、部署、配置和管理。

内置于 Windows Server 和 System Center 的技术是 Windows Server SDDC 体验的主要构建基块。 但是，即使是虚拟化的平台，也仍然需要合适的基础硬件。 参与“Windows Server 软件定义 (WSSD) 解决方案”和“Azure Stack HCI 解决方案”计划的 Microsoft 合作伙伴可以帮助企业获取合适的硬件，并在第零天启动并运行硬件   。

![视频图标](media/sddc/video.png)**[观看视频以了解有关 Microsoft SDDC 的详细信息](https://mva.microsoft.com/training-courses/whats-new-in-windows-server-2016-16457?l=YcsJR6sXC_1006218965)**

![海报图标](media/sddc/poster-ico.png)**[下载此页面的海报大小的 .pdf 文件](https://github.com/MicrosoftDocs/windowsserverdocs/blob/master/WindowsServerDocs/media/sddc/sddc_poster_0801417_ANSI-E.pdf)**

## <a name="azure-stack-hci-solutions"></a>Azure Stack HCI 解决方案

在合适的硬件基础结构上构建 Windows Server 软件定义数据中心是获得成功至关重要的第一步。 这就是我们与 15 个合作伙伴合作来创建 Microsoft 验证的 SDDC 设计和部署的最佳实践的原因。

Microsoft 合作伙伴提供了一系列解决方案，这些解决方案可使用通过 Azure Stack HCI 计划使用 Window Server 2019 和通过 Windows Server 软件定义 (WSSD) 程序使用 Windows Server 2016，以提供高性能、超聚合的存储和网络基础结构。 超聚合解决方案在行业标准服务器和组件上将计算、存储和网络功能汇集在一起，以改善数据中心智能和控制。

![Learn 图标](media/sddc/learn.png)**[了解有关 Azure Stack HCI 解决方案的详细信息](https://azure.microsoft.com/overview/azure-stack/hci)**

![Learn 图标](media/sddc/learn.png)**[了解有关 WSSD 解决方案的详细信息](https://www.microsoft.com/cloud-platform/software-defined-datacenter)**

## <a name="windows-server-virtualized-technologies"></a>Windows Server 虚拟化技术 ##

本主题的其余部分列出了 Windows Server SDDC 技术，并提供指向每种技术的文档的链接。 下表列出了这些技术：

![可用的 Windows Server SDDC 技术](media/sddc/table.png)

![虚拟化任何内容标题栏](media/sddc/virtualize.png)

### <a name="windows-server-hyper-converged"></a>Windows Server、超聚合

Windows Server 虚拟化技术包括对 Hyper-V、Hyper-V 虚拟交换机以及受保护的构造和受防护的虚拟机 (VM) 进行更新，能够提升安全性、可扩展性和可靠性。 与 Hyper-V 配合使用时，对故障转移群集、网络和存储的更新会使这些技术的部署和管理更加轻松。

![仅限间距用途的图像](media/sddc/spacer1.png)![Windows Server，超融合基础设施示意图](media/sddc/hyper-converged.png)

![Learn 图标](media/sddc/learn.png)**[了解有关 Windows Server、超融合的详细信息](https://docs.microsoft.com/windows-server/get-started/what-s-new-in-windows-server-2016#computevirtualizationvirtualizationmd)**

### <a name="hyper-v-hypervisor"></a>Hyper-V 虚拟机监控程序

Hyper-V 是基于虚拟机监控程序的虚拟化技术，适用于 Windows。 虚拟机监控程序是虚拟化的核心。 它是特定于处理器的虚拟化平台，允许多个独立的操作系统共享单个硬件平台。

![Hyper-V 虚拟机监控程序示意图](media/sddc/spacer1.png)![Hyper](media/sddc/hypervisor.png)

![Learn 图标](media/sddc/learn.png)**[了解有关 Hyper-V 虚拟机监控程序的详细信息](https://www.microsoft.com/cloud-platform/server-virtualization)**

### <a name="guest-clustering-with-shared-vhdx"></a>具有共享 VHDX 的来宾群集

![间距用途的线图像](media/sddc/virtualize-line.png)

共享 VHDX 既灵活又安全并且未绑定到基础存储拓扑，而且不需要向来宾 OS 提供物理基础存储。 新的共享 VHDX 支持在线调整大小。

![仅限间距用途的图像](media/sddc/spacer1.png)![来宾群集和共享 VHDX 关系图](media/sddc/cluster.png)

- 共享 VHDX 可位于块存储或基于文件的 SMB 存储中的群集共享卷 (CSV) 上。
- 受保护：共享 VHDX 支持 Hyper-V 副本和主机级别的备份。

![Learn 图标](media/sddc/learn.png)**[了解有关具有共享 VHDX 的来宾群集的详细信息](https://technet.microsoft.com/library/dn281956(v=ws.11).aspx)**

### <a name="hyper-v-replica"></a>Hyper-V 副本

![间距用途的线图像](media/sddc/virtualize-line.png)

已将基于软件的跨网络 VM 复制与证书集成。 未绑定到任一站点上的服务器、网络或存储硬件。

![仅限间距用途的图像](media/sddc/spacer1.png)![Hyper-V 副本示意图](media/sddc/replica.png)

无需其他虚拟机复制技术，因此降低了成本。
- 自动处理实时迁移。
- 配置和管理十分简单 - 通过 Hyper-V 管理器、PowerShell 或使用 Azure 站点恢复。

![Learn 图标](media/sddc/learn.png)**[了解有关 Hyper-V 副本的详细信息](https://docs.microsoft.com/windows-server/virtualization/hyper-v/manage/set-up-hyper-v-replica)**

![连接任何内容横幅](media/sddc/networking.png)

### <a name="network-controller"></a>网络控制器

![间距用途的线图像](media/sddc/networking-line.png)

可用于在数据中心中以编程方式集中地自动管理、配置、监视虚拟和物理网络基础结构并对之进行故障排除。

![仅限间距用途的图像](media/sddc/spacer1.png)![网络控制器示意图](media/sddc/netcontroller.png)

管理员使用一种直接与网络控制器交互的管理工具。 网络控制器为此管理工具提供有关网络基础结构（包括虚拟和物理基础结构）的信息。

![Learn 图标](media/sddc/learn.png)**[了解有关网络控制器的详细信息](https://docs.microsoft.com/windows-server/networking/sdn/technologies/network-controller/network-controller)**

### <a name="datacenter-firewall"></a>数据中心防火墙

![间距用途的线图像](media/sddc/networking-line.png)

以服务形式部署和提供时，租户管理员可以安装和配置防火墙策略，以帮助保护虚拟网络免受 Internet 和 Intranet 网络垃圾流量的危害。

![仅限间距用途的图像](media/sddc/spacer1.png)![数据中心防火墙示意图](media/sddc/firewall.png)

服务提供商管理员或租户管理员可以通过网络控制器来管理数据中心防火墙策略。

![Learn 图标](media/sddc/learn.png)**[了解有关数据中心防火墙的详细信息](https://docs.microsoft.com/windows-server/networking/sdn/technologies/network-function-virtualization/datacenter-firewall-overview)**

### <a name="switch-embedded-teaming"></a>交换机嵌入式组合

![间距用途的线图像](media/sddc/networking-line.png)

SET 是一种替代 NIC 组合解决方案，可用于包含 Hyper-V 和[软件定义网络 (SDN)](https://docs.microsoft.com/windows-server/networking/sdn/software-defined-networking) 堆栈的环境。

![仅限间距用途的图像](media/sddc/spacer1.png)![交换机嵌入式组合示意图](media/sddc/teaming.png)

![Learn 图标](media/sddc/learn.png)**[了解有关交换机嵌入式组合的详细信息](https://docs.microsoft.com/windows-server/networking/sdn/technologies/set-for-sdn)**

### <a name="software-load-balancing"></a>软件负载均衡 (SLB)

![间距用途的线图像](media/sddc/networking-line.png)

SLB 允许多台服务器承载相同的工作负载，具有较高的可用性和可扩展性。 在用于其他 VM 工作负载的相同 Hyper-V 服务器上使用 SLB VM 横向扩展负载均衡功能。 SLB 支持快速创建和删除云服务提供商操作的负载均衡终结点。 SLB 支持每个群集拥有数十 GB 的容量，提供了一个简单的预配模型，并且易于横向和纵向扩展。

![仅限间距用途的图像](media/sddc/spacer1.png)![软件负载均衡示意图](media/sddc/balancer.png)

![Learn 图标](media/sddc/learn.png)**[了解有关软件负载均衡的详细信息](https://docs.microsoft.com/windows-server/networking/sdn/technologies/network-function-virtualization/software-load-balancing-for-sdn)**

![存储示意图](media/sddc/storage.png)

### <a name="storage-spaces-direct"></a>Storage Spaces Direct

![间距用途的线的存储图像](media/sddc/storage-line.png)

存储空间直通使用具有本地连接驱动器的行业标准服务器来提供高度可用、高度可扩展的软件定义存储，其成本仅占传统 SAN 或 NAS 阵列的一小部分。 其体系结构大大简化了采购和部署过程。

![仅限间距用途的图像](media/sddc/spacer1.png)![存储空间直通示意图](media/sddc/ssd.png)

存储空间直通引入了新的软件存储总线，并利用 Windows Server 中当前已知的许多功能，如故障转移群集、群集共享卷 (CSV)、服务器消息块 (SMB) 3 以及存储空间。

![Learn 图标](media/sddc/learn.png)**[了解有关存储空间直通的详细信息](storage/storage-spaces/storage-spaces-direct-overview.md)**
### <a name="storage-quality-of-service"></a>存储服务质量 ###

![间距用途的线](media/sddc/storage-line.png)

可以使用 Hyper-V 和横向扩展文件服务器角色集中监视和管理虚拟机的存储性能，并改善多个虚拟机之间的存储资源公平度。

![仅限间距用途的图像](media/sddc/spacer1.png)![服务存储质量示意图](media/sddc/qos.png)

存储 QoS 内置于横向扩展文件服务器和 Hyper-V 使用 SMB3 协议提供的 Microsoft 软件定义存储解决方案中。 新的策略管理器可集中监视存储性能。

![Learn 图标](media/sddc/learn.png)**[了解有关存储 QoS 的详细信息](https://docs.microsoft.com/windows-server/storage/storage-qos/storage-qos-overview)**

### <a name="storage-replica"></a>存储副本

![间距用途的线的存储图像](media/sddc/storage-line.png)

灾难恢复和准备可实现零数据丢失，能够同步保护不同机架、楼层、建筑物、园区、城市和国家/地区的数据，并且能更有效地利用多个数据中心。

![仅限间距用途的图像](media/sddc/spacer1.png)
![存储副本示意图](media/sddc/storage-replica.png)

同步复制

1. 应用程序写入数据
2. 写入日志数据，并将数据复制到远程站点
3. 在远程站点写入日志数据
4. 从远程站点确认
5. 确认应用程序写入

t & t1：数据刷新到该卷，始终写入日志

![Learn 图标](media/sddc/learn.png)**[了解有关存储副本的详细信息](https://docs.microsoft.com/windows-server/storage/storage-replica/storage-replica-overview)**

![安全示意图](media/sddc/security.png)

### <a name="guarded-fabric"></a>受保护的结构

![间距用途的线的安全图像](media/sddc/security-line.png)

作为云服务商或企业私有云管理员，你可以使用受保护的构造为 VM 提供更安全的环境。 受保护的结构包括一项主机保护者服务 (HGS)（通常是由三个节点组成的群集）、一个或多个受保护的主机以及一组受防护的虚拟机 (VM)。

![受保护的结构示意图](media/sddc/spacer1.png)![受保护的结构示意图](media/sddc/guarded-fabric.png)

![Learn 图标](media/sddc/learn.png)**[了解有关受保护的结构的详细信息](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms)**

### <a name="shielded-vms"></a>受防护的 VM

![间距用途的线的安全图像](media/sddc/security-line.png)

受防护的 VM 的数据和状态受到保护，以防止恶意软件和数据中心管理员进行检查、窃取和篡改。

![仅限间距用途的图像](media/sddc/spacer1.png)![受防护示意图](media/sddc/shielded.png)

- 受防护的 VM 将只在指定为 VM 所有者的结构中运行。
- 受防护的 VM 通过 BitLocker 或其他方式进行加密，以便只有指定的所有者才能运行它们。
- 运行中的 VM 可转换为受防护的 VM。

![Learn 图标](media/sddc/learn.png)**[了解有关受防护的 VM 的详细信息](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms)**

### <a name="host-guardian-service"></a>主机保护者服务

![间距用途的线的安全图像](media/sddc/security-line.png)

主机保护者服务会保存合法结构以及加密虚拟机的密钥。

![仅限间距用途的图像](media/sddc/spacer1.png)![保护者关系图](media/sddc/guardian.png)

![Learn 图标](media/sddc/learn.png)**[了解有关主机保护者服务的详细信息](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-manage-hgs)**

### <a name="device-health-attestation"></a>设备运行状况证明

![间距用途的线的安全图像](media/sddc/security-line.png)

证明使企业能够将组织的安全防护提升到受监视和已证明安全的硬件，对操作成本只有极小影响或无影响。

![仅限间距用途的图像](media/sddc/spacer1.png)![证明示意图](media/sddc/attestation.png)

如上所示的硬件信任模式可提供最高级别的安全保证以及 TPM v2.0 硬件根信任，并符合密钥发放的代码完整性策略。

![Learn 图标](media/sddc/learn.png)**[了解有关设备运行状况证明的详细信息](https://docs.microsoft.com/windows-server/security/device-health-attestation)**

![管理示意图](media/sddc/management.png)

### <a name="powershell-desired-state-configuration"></a>PowerShell Desired State Configuration

![间距用途的线的管理图像](media/sddc/management-line.png)

Windows PowerShell Desired State Configuration (DSC) 是基于开放标准且内置于 Windows 中的配置管理平台。 DSC 足够灵活以在部署生命周期的各个阶段（开发、测试、预生产、生产）及扩展期间可靠而一致地运转。

![仅限间距用途的图像](media/sddc/spacer1.png)![Desired State Configuration 示意图](media/sddc/dsc.png)

DSC 支持“连续部署”，因此，可以反复部署配置，而不会损坏任何内容。

-  DSC 配置只应用从原始配置更改的设置来实现更快的部署。
-  可以在本地、在公有或私有云环境中使用 DSC。
-  只要可以在目标系统上执行 PowerShell 脚本，就可以将 DSC 与任何 Microsoft 或非 Microsoft 解决方案集成。

![Learn 图标](media/sddc/learn.png)**[了解有关 PowerShell DSC 的详细信息](https://docs.microsoft.com/powershell/dsc/overview)**

### <a name="system-center-vmm"></a>System Center VMM

![间距用途的线的管理图像](media/sddc/management-line.png)

Virtual Machine Manager 是 System Center 套件的一部分，用于配置、管理和转换传统的数据中心，以在本地、服务商和 Azure 云中提供统一的管理体验。

![仅限间距用途的图像](media/sddc/spacer1.png)![Virtual Machine Manager 示意图](media/sddc/vmm.png)

- 数据中心：在 VMM 中将数据中心组件作为单一结构进行配置和管理。
- 虚拟化主机：VMM 可以添加、预配和管理 Hyper-V 和 VMware 虚拟化主机和群集。
- 网络：VMM 可提供网络虚拟化，包括对创建和管理虚拟网络和网关的支持。
- 存储：VMM 可以发现、分类、预配、分配和指定本地和远程存储。

![Learn 图标](media/sddc/learn.png)**[了解有关 System Center VMM 的详细信息](https://docs.microsoft.com/system-center/vmm/)**

### <a name="windows-admin-center"></a>Windows Admin Center

![间距用途的线的管理图像](media/sddc/management-line.png)

Windows Admin Center 是一个在本地部署的基于浏览器的管理工具集，能够实现在本地管理 Windows Server，而无需依赖 Azure 或云。 利用 Windows Admin Center，IT 管理员能够完全控制其服务器基础结构的各个方面，尤其适用于在未连接到 Internet 的专用网络上进行管理。

![仅限间距用途的图像](media/sddc/spacer1.png)![体系结构示意图](media/sddc/architecture.png)

通过将 Web 服务器发布到 DNS 并设置公司防火墙，你可以从公共 Internet 访问 Windows Admin Center，并且能够利用 Microsoft Edge 或 Google Chrome 从任何位置连接和管理服务器。

![Learn 图标](media/sddc/learn.png)**[了解有关 Windows Admin Center 的详细信息](manage/windows-admin-center/overview.md)**
