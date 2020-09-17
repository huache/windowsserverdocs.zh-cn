---
title: Windows Server 上的 Hyper-V
description: 提供指向有关如何试用、规划、部署和管理 Hyper-v 的关键文章的链接
ms.topic: article
ms.assetid: 0baef6b8-598c-4fe0-9f31-5869fc4e0f69
ms.author: benarm
author: BenjaminArmstrong
ms.date: 10/07/2016
ms.openlocfilehash: 9d0e8ea97d229f82b07268bb143cf6ea0969c251
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90744152"
---
# <a name="hyper-v-on-windows-server"></a>Windows Server 上的 Hyper-V

>适用于：Windows Server 2016、Windows Server 2019

Windows Server 中的 Hyper-v 角色使你能够创建虚拟化的计算环境，你可以在其中创建和管理虚拟机。 你可以在一台物理计算机上运行多个操作系统，并将操作系统彼此隔离。 利用此技术，可以提高计算资源的效率并释放硬件资源。

请参阅下表中的主题，了解有关 Windows Server 上的 Hyper-v 的详细信息。

## <a name="hyper-v-resources-for-it-pros"></a>适用于 IT 专业人员的 hyper-v 资源

|任务 |资源|
|---|---|
|![已满足显示要求的复选标记和文档图标](media/All_Symbols_MeetsRequirements.png)|**评估 Hyper-V**<p>- [Hyper-v 技术概述](Hyper-V-Technology-Overview.md)<br />- [Windows Server 上的 Hyper-v 中的新增功能](What-s-new-in-Hyper-V-on-Windows.md)<br />- [Windows Server 上的 Hyper-v 的系统要求](System-requirements-for-Hyper-V-on-Windows.md)<br />- [支持 Hyper-v 的 Windows 来宾操作系统](Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md) <br />- [支持的 Linux 和 FreeBSD 虚拟机](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)<br />- [功能与生成和来宾的兼容性](Hyper-V-feature-compatibility-by-generation-and-guest.md) <p>**规划 Hyper-v**<p>- [是否应在 Hyper-v 中创建第1代或第2代虚拟机？](plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md) <br />- [规划 Windows Server 中的 Hyper-v 可伸缩性](plan/plan-hyper-v-scalability-in-windows-server.md) <br />- [规划 Windows Server 中的 Hyper-v 网络](plan/plan-hyper-v-networking-in-windows-server.md) <br />- [规划 Windows Server 中的 Hyper-v 安全](plan/plan-hyper-v-security-in-windows-server.md)|
|![光标和旭日图标](media/All_Symbols_GetStarted.png)|**Hyper-V 入门**<p>- [下载并安装 Windows Server 2019](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019)<p>**Windows Server 2019 作为虚拟主机的服务器核心或 GUI 安装选项**<p>- [在 Windows Server 上安装 Hyper-v 角色](get-started/Install-the-Hyper-V-role-on-Windows-Server.md)<br />- [为 Hyper-v 虚拟机创建虚拟交换机](get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)<br />- [在 Hyper-v 中创建虚拟机](get-started/Create-a-virtual-machine-in-Hyper-V.md)|
|![人员和工具图标](media/All_Symbols_Administrator.png)|**升级 Hyper-v 主机和虚拟机**<p>- [升级 Windows Server 群集节点](../../failover-clustering/Cluster-Operating-System-Rolling-Upgrade.md)<br />- [升级虚拟机版本](deploy/Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md)<p>**配置和管理 Hyper-v**<p>- [为无故障转移群集的实时迁移设置主机](deploy/Set-up-hosts-for-live-migration-without-Failover-Clustering.md)<br />- [远程管理 Nano Server](../../get-started/manage-nano-server.md)<br />- [在标准或生产检查点之间进行选择](manage/Choose-between-standard-or-production-checkpoints-in-Hyper-V.md)<br />- [启用或禁用检查点](manage/Enable-or-disable-checkpoints-in-Hyper-V.md)<br />- [通过 PowerShell Direct 管理 Windows 虚拟机](manage/Manage-Windows-virtual-machines-with-PowerShell-Direct.md)<br />- [设置 Hyper-v 副本](manage/Set-up-Hyper-V-Replica.md)|
|![对话气泡图标](media/All_Symbols_Chat.png)|**博客**<p>查看 Microsoft 虚拟化和 Hyper-v 团队中的项目经理、产品经理、开发人员和测试人员的最新帖子。<p>- [虚拟化博客](https://blogs.technet.com/b/virtualization/)<br />- [Windows Server 博客](https://blogs.technet.com/b/windowsserver/)<br />- [Ben Armstrong 的虚拟化博客](/archive/blogs/virtual_pc_guy/) (存档) |
|![用户组图标](media/All_Symbols_Users_Group.png)|**论坛和新闻组**<p>遇到问题？ 与你的同事、Mvp 和 Hyper-v 产品团队交流。<p>- [Windows Server 社区](https://techcommunity.microsoft.com/t5/Windows-Server/ct-p/Windows-Server)<br />- [Windows Server Hyper-v TechNet 论坛](/answers/topics/windows-server-hyper-v.html)|

## <a name="related-technologies"></a>相关技术

下表列出了你可能想要在虚拟化计算环境中使用的技术。

|技术|描述|
|--------------|---------------|
|[客户端 Hyper-V](/virtualization/hyper-v-on-windows/index)|Windows 8、Windows 8.1 和 Windows 10 附带的虚拟化技术，可通过**控制面板**中的 "**程序和功能**" 安装。|
|[故障转移群集](../../failover-clustering/whats-new-in-failover-clustering.md)|为 Hyper-v 主机和虚拟机提供高可用性的 Windows Server 功能。|
|[Virtual Machine Manager](/system-center/vmm/overview)|为虚拟化数据中心提供管理解决方案的 System Center 组件。 你可以配置和管理虚拟化主机、网络和存储资源，以便创建虚拟机和服务并将其部署到你创建的私有云。|
|[Windows 容器](/virtualization/windowscontainers/)|使用 Windows Server 和 Hyper-v 容器为开发、测试和生产团队提供标准化环境。|