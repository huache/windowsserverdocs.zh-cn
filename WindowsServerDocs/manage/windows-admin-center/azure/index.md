---
title: 将 Windows Server 连接到 Azure 混合服务
description: 可以通过使用 Azure 混合服务将 Windows Server 的本地部署扩展到云。
ms.technology: manage
ms.topic: article
author: jasongerend
ms.author: jgerend
ms.localizationpriority: medium
ms.prod: windows-server
ms.date: 05/31/2019
ms.openlocfilehash: b82d2eaa9283d99993102f1656262e2eda86cfff
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950127"
---
# <a name="connecting-windows-server-to-azure-hybrid-services"></a>将 Windows Server 连接到 Azure 混合服务

可以通过使用 Azure 混合服务将 Windows Server 的本地部署扩展到云。 这些云服务提供了一系列有用的功能，可用于从本地扩展到 Azure，以及从 Azure 进行集中管理。

![包含箭头的图，一类箭头从本地指向云，表示从本地扩展到 Azure，另一类箭头从云指向本地，表示通过 Azure 进行集中管理](../media/azure-services/hybrid-framing.png)

在 Windows Admin Center 中使用 Azure 混合服务，可以：

- [保护虚拟机，并使用基于云的备份和灾难恢复 (HA/DR)](#back-up-and-protect-your-on-premises-servers-and-vms)。  
- [利用 Azure 中的存储和计算功能扩展本地容量，并简化到 Azure](#extend-on-premises-capacity-with-azure) 的网络连接。
- [利用云智能 Azure 管理服务，集中监视、管理、配置和保护应用程序、网络和基础结构](#centrally-manage-your-hybrid-environment-from-azure)。  

虽然可以通过下载应用和执行手动配置来设置大多数 Azure 混合服务，但许多 Azure 混合服务都直接集成到 Windows Admin Center 中，以便提供简化的安装体验和以服务器为中心的服务视图。 Windows Admin Center 还提供了指向 Azure 门户的方便的智能超链接，以便你查看连接的 Azure 资源以及混合环境的集中式视图。

## <a name="discover-integrated-services-in-the-azure-hybrid-services-tool"></a>在 Azure 混合服务工具中发现集成服务

[Windows Admin Center](../overview.md) 中的 Azure 混合服务工具将所有集成的 Azure 服务整合到一个集中式中心，你在其中可以轻松地发现可为本地或混合环境带来价值的所有可用 Azure 服务。  

![显示 Azure 混合服务工具的 Windows Admin Center 屏幕截图](../media/azure-services/ahs-discover.png)

如果在已启用 Azure 服务的情况下连接到服务器，Azure 混合服务工具可充当一片玻璃，供你查看该服务器上的所有已启用服务。 可以在 Windows Admin Center 中轻松访问相关工具，导航到 Azure 门户以便更深入地管理这些 Azure 服务，或者通过手头的文档了解详情。  

![显示服务器上已安装的 Azure 服务的 Windows Admin Center 屏幕截图](../media/azure-services/ahs-dayN.png)

从 Azure 混合服务工具中可以：

- 使用 [Azure 备份](azure-backup.md)从 Windows Admin Center 中备份 Windows Server
- 使用 [Azure Site Recovery](azure-site-recovery.md) 从 Windows Admin Center 中保护 Hyper-V 虚拟机
- 使用 [Azure 文件同步](azure-file-sync.md)将文件服务器与云同步
- 使用 [Azure 更新管理](azure-update-management.md)管理所有 Windows 服务器（在本地或在云中）的操作系统更新
- 使用 [Azure Monitor](azure-monitor.md) 监视服务器（在本地或在云中）并配置警报
- 使用[适用于服务器的 Azure Arc](https://docs.microsoft.com/azure/azure-arc/servers/overview) 通过 Azure Policy 将管控策略应用到本地服务器
- 通过 [Azure 安全中心来保护服务器并获得高级威胁防护](https://docs.microsoft.com/azure/security-center/windows-admin-center-integration)
- 使用 [Azure 网络适配器](https://aka.ms/WACNetworkAdapter)将本地服务器连接到 Azure 虚拟网络
- 通过 [Azure 扩展网络](https://go.microsoft.com/fwlink/?linkid=2109517&clcid=0x409)将 Azure VM 设置为类似于本地网络

## <a name="back-up-and-protect-your-on-premises-servers-and-vms"></a>备份和保护本地服务器和 VM

- **使用 [Azure 备份](https://docs.microsoft.com/azure/backup/backup-overview)来备份 Windows 服务器**  
可以将 Windows 服务器备份到 Azure，从而帮助防止意外或恶意删除、损坏和勒索软件侵害。  
有关详细信息，请参阅[使用 Azure 备份来备份服务器](azure-backup.md)。

- **使用 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) 保护 Hyper-V 虚拟机**  
可以复制在虚拟机上运行的工作负载，以便在出现灾难时能够让你的业务关键基础结构受到保护。 Windows Admin Center 简化了安装以及将虚拟机复制到 HYPER-V 服务器或群集的过程，让你可以更轻松地通过 Azure Site Recovery 的灾难恢复服务提升环境的复原能力。  
有关详细信息，请参阅[使用 Azure Site Recovery 和 Windows Admin Center 保护 VM](azure-site-recovery.md)。

- **使用[存储副本](https://docs.microsoft.com/windows-server/storage/storage-replica/storage-replica-overview)** 通过基于块的同步或异步复制到 Azure 中的 VM  
可以在服务器到服务器级别上使用存储副本将基于块或基于卷的复制配置为到辅助服务器或 VM。 借助 Windows Admin Center，可以针对复制目标创建 Azure VM，有助于你在新的 Azure VM 上调整大小并正确配置存储。  
有关详细信息，请参阅[通过存储副本进行服务器到服务器复制](https://docs.microsoft.com/windows-server/storage/storage-replica/storage-replica-ui)。  

## <a name="extend-on-premises-capacity-with-azure"></a>通过 Azure 扩展本地容量

### <a name="extend-storage-capacity"></a>扩展存储容量

- **使用 [Azure 文件同步](https://aka.ms/afs)将文件服务器与云同步**  
将此服务器上的文件与 Azure 文件共享同步。 将所有文件都保留在本地，或者使用云分层来释放空间，并且仅缓存服务器上最常用的文件，将冷数据分层到云中。 云中的数据可以备份，这样就无需担心本地服务器备份。 此外，多站点同步可让一组文件在多个服务器上保持同步。
有关详细信息，请参阅[使用 Azure 文件同步将文件服务器与云同步](azure-file-sync.md)。

- **使用[存储迁移服务](https://docs.microsoft.com/windows-server/storage/storage-migration-service/overview)将存储迁移到 Azure 中的 VM**  
使用分步工具清点 Windows 和 Linux 服务器上的数据，然后将数据传输到新的 Azure VM。 Windows Admin Center 可以为作业创建一个新的 Azure VM，该 VM 的大小进行了调整，并正确配置为接收来自源服务器的数据。  
有关详细信息，请参阅[使用存储迁移服务迁移服务器](https://docs.microsoft.com/windows-server/storage/storage-migration-service/migrate-data)。

### <a name="extend-compute-capacity"></a>扩展计算容量

- **创建新的 Azure 虚拟机，而无需离开 Windows Admin Center**  
在 Windows Admin Center 的“所有连接”页中，转到“添加”，然后选择“Azure VM”下的“新建”     。 甚至可以域加入 Azure VM，并在此分步创建工具中配置存储。

- **通过[云见证](https://docs.microsoft.com/windows-server/failover-clustering/deploy-cloud-witness)利用 Azure 在故障转移群集上实现仲裁**  
可以将 Azure 存储帐户用作 Azure Stack HCI 群集或其他故障转移群集的群集见证，而无需对其他硬件投资以实现 2 节点群集上的仲裁。  
有关详细信息，请参阅[为故障转移群集部署云见证](https://docs.microsoft.com/windows-server/failover-clustering/deploy-cloud-witness)。  

### <a name="simplify-network-connectivity-between-your-on-premises-and-azure-networks"></a>简化本地和 Azure 网络之间的网络连接

- **使用 [Azure 网络适配器](https://aka.ms/WACNetworkAdapter)将本地服务器连接到 Azure 虚拟网络**  
借助 Windows Admin Center，可以简化将点到站点 VPN 从本地服务器设置到 Azure 虚拟网络的操作。  

- **通过 [Azure 扩展网络](https://go.microsoft.com/fwlink/?linkid=2109517&clcid=0x409)将 Azure VM 设置为类似于本地网络**  
Windows Admin Center 可以设置站点到站点 VPN，并将本地 IP 地址扩展到 Azure vNet，让你能够更轻松地将工作负荷迁移到 Azure，而不会破坏 IP 地址的依赖项。

## <a name="centrally-manage-your-hybrid-environment-from-azure"></a>从 Azure 集中管理混合环境

- **使用[用于虚拟机的 Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview) 监视环境中的所有服务器并获取相关电子邮件警报**  
Azure Monitor（也称为虚拟机见解）可用于监视服务器运行状况和事件、创建电子邮件警报、获取整个环境中服务器性能的合并视图以及将连接到给定服务器的应用、系统和服务可视化。 Windows Admin Center 还可以为服务器运行状况性能和群集运行状况事件设置默认电子邮件警报。  
有关详细信息，请参阅[将服务器连接到 Azure Monitor 并配置电子邮件通知](azure-monitor.md)。

- **使用 [Azure 更新管理](https://docs.microsoft.com/azure/automation/automation-update-management)集中管理所有 Windows 服务器的操作系统更新**  
可以从单个位置（而不是在每个服务器上）管理多个服务器和 VM 的更新和修补程序。 借助 Azure 更新管理，可以快速评估可用更新的状态、计划所需更新的安装，以及查看部署结果来验证更新是否已成功应用。 无论服务器是 Azure VM、由其他云提供商托管或是本地服务器，均可如此。  
有关详细信息，请参阅[为 Azure 更新管理配置服务器](azure-update-management.md)。

- **通过 [Azure 安全中心](https://docs.microsoft.com/azure/security-center/security-center-intro)改善安全状况并获得高级威胁防护**  
Azure 安全中心是一种统一的基础结构安全管理系统，它可以增强数据中心的安全性，并跨云中（无论是否在 Azure 中）和本地的混合工作负荷提供高级威胁防护。 通过 Windows Admin Center，可以轻松地设置服务器并将其连接到 Azure 安全中心。  
有关详细信息，请参阅[将 Azure 安全中心与 Windows Admin Center（预览版）集成](https://docs.microsoft.com/azure/security-center/windows-admin-center-integration)。  

- **应用策略并通过[适用于服务器的 Azure Arc](https://docs.microsoft.com/azure/azure-arc/servers/overview) 和 [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview)** 确保混合环境中的符合性  
从 Azure 清点、组织和管理本地服务器。 可以使用 Azure Policy 管理服务器，使用 RBAC 控制访问权限，并从 Azure 启用其他管理服务。  

## <a name="clusters-versus-stand-alone-servers-and-vms"></a>群集与独立服务器和 VM

Azure 混合服务使用下列配置中的 Windows 服务器：

- 独立的物理服务器和虚拟机 (VM)
- 群集，包括通过了 [Azure Stack HCI](../../../azure-stack-hci/index.md) 认证的超融合群集，以及 [Windows Server 软件定义 (WSSD)](https://www.microsoft.com/cloud-platform/software-defined-datacenter) 程序

### <a name="services-for-stand-alone-servers-and-vms"></a>适用于独立服务器和 VM 的服务

这是为独立服务器和 VM 提供功能的 Azure 服务的完整列表：

- 使用 [Azure 备份](azure-backup.md)从 Windows Admin Center 中备份 Windows Server
- 使用 [Azure Site Recovery](azure-site-recovery.md) 从 Windows Admin Center 中保护 Hyper-V 虚拟机
- 使用 [Azure 文件同步](azure-file-sync.md)将文件服务器与云同步
- 使用 [Azure 更新管理](azure-update-management.md)管理所有 Windows 服务器（在本地或在云中）的操作系统更新
- 使用 [Azure Monitor](azure-monitor.md) 监视服务器（在本地或在云中）并配置警报
- 使用[适用于服务器的 Azure Arc](https://docs.microsoft.com/azure/azure-arc/servers/overview) 通过 Azure Policy 将管控策略应用到本地服务器
- 通过 [Azure 安全中心来保护服务器并获得高级威胁防护](https://docs.microsoft.com/azure/security-center/windows-admin-center-integration)
- 使用 [Azure 网络适配器](https://aka.ms/WACNetworkAdapter)将本地服务器连接到 Azure 虚拟网络
- 通过 [Azure 扩展网络](https://go.microsoft.com/fwlink/?linkid=2109517&clcid=0x409)将 Azure VM 设置为类似于本地网络

### <a name="services-for-clusters"></a>适用于群集的服务

这些是从整体上为群集提供功能的 Azure 服务：

- [使用 Azure Monitor 监视超融合群集](../../../storage/storage-spaces/configure-azure-monitor.md)
- [使用 Azure Site Recovery 保护 VM](azure-site-recovery.md)
- [部署群集云见证](../../../failover-clustering/deploy-cloud-witness.md)  

## <a name="other-azure-integrated-abilities-of-windows-admin-center"></a>Windows Admin Center 的其他 Azure 集成功能

- **[在 Windows Admin Center 中添加 Azure VM 连接](manage-azure-vms.md)**  
可以使用 Windows Admin Center 来管理 Azure VM 以及本地计算机。 通过将 Windows Admin Center 网关配置为连接到 Azure VNet，可以使用 Windows Admin Center 提供的一致、简化的工具在 Azure 中管理虚拟机。  
有关详细信息，请参阅[配置 Windows Admin Center 以便在 Azure 中管理 VM](manage-azure-vms.md)。

- **通过添加 [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) 身份验证向 Windows Admin Center 添加安全层**  
可以通过要求用户使用 Azure Active Directory (Azure AD) 标识访问网关进行身份验证，向 Windows Admin Center 添加额外的安全层。 使用 Azure AD 身份验证，还可以充分利用 Azure AD 的安全功能，如条件访问和多重身份验证。  
有关详细信息，请参阅[为 Windows Admin Center 配置 Azure AD 身份验证](../configure/user-access-control.md#azure-active-directory)。  

- **直接通过 Windows Admin Center 中嵌入的 [Azure Cloud Shell](https://docs.microsoft.com/azure/cloud-shell/overview) 管理 Azure 资源**  
利用 Azure Cloud Shell 在 Windows Admin Center 内获取 Bash 或 PowerShell 体验，以便轻松访问 Azure 管理任务。  
有关详细信息，请参阅 [Azure Cloud Shell 概述](https://docs.microsoft.com/azure/cloud-shell/overview)。


## <a name="see-also"></a>另请参阅

- [将 Windows Admin Center 连接到 Azure](azure-integration.md)
- [在 Azure 中部署 Windows Admin Center](deploy-wac-in-azure.md)
