---
title: Microsoft Hyper-V Server 2016
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f815ada0-4c63-4e73-9c24-dc5eb21526c7
author: KBDAzure
ms.author: kathydav
ms.date: 07/26/2017
ms.openlocfilehash: c9e1b5e2d30276bf89bc2d56482ec76d1c2241a2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365585"
---
# <a name="microsoft-hyper-v-server-2016"></a>Microsoft Hyper-V Server 2016

Microsoft Hyper-V Server 2016 是一种独立的\-产品，仅包含 Windows 虚拟机监控程序、Windows Server 驱动程序模型和虚拟化组件。 它提供简单可靠的虚拟化解决方案，以帮助提高服务器利用率并降低成本。

Microsoft Hyper-V Server 2016 中的 Windows 虚拟机监控程序技术与 Windows Server 2016 上的 "Hyper-v\-V" 角色中的内容相同。 那么，在 Windows Server 2016 上，适用于超级\-V 角色的很多内容也适用于 Microsoft Hyper-V 服务器2016。

## <a name="hyper-v-server-resources-for-it-pros"></a>适用于 IT 专业人员的 hyper-v\-Server 资源

|任务|资源|
|-|-|
|![满足要求符号](media/All_Symbols_MeetsRequirements.png)|**评估 Hyper-v**<br /><br />-   [Hyper-v 技术概述](hyper-v-technology-overview.md)<br />- [Windows Server 2016 上的 hyper-v 中的新增功能](what-s-new-in-hyper-v-on-windows.md)<br />[Windows Server 2016 上的 hyper-v 的 -   系统要求](system-requirements-for-hyper-v-on-windows.md)<br />[适用于 hyper-v 的 -   支持的 Windows 来宾操作系统](supported-windows-guest-operating-systems-for-hyper-v-on-windows.md)<br />-   [支持的 Linux 和 FreeBSD 虚拟机](supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows.md)<br />[通过代和来宾 -   功能兼容性](hyper-v-feature-compatibility-by-generation-and-guest.md)<br /><br />**规划 Hyper-v**<br /><br />-决定哪种[虚拟机生成](plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v.md)满足你的需求。 <br/>-如果你要移动或导入虚拟机，请决定[升级版本的](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md)时间。 <br />- [可伸缩性](plan/plan-hyper-v-scalability-in-windows-server.md) <br />- [网络](plan/plan-hyper-v-networking-in-windows-server.md) <br />- [安全性](plan/plan-hyper-v-security-in-windows-server.md)|
|![入门符号](media/All_Symbols_GetStarted.png)|**Hyper-v 服务器入门**<br /><br />[下载并安装 Microsoft hyper-v\-Server 2016](https://www.microsoft.com/evalcenter/evaluate-hyper-v-server-2016)。 这将安装 Windows 虚拟机监控程序、Windows Server 驱动程序模型和虚拟化组件。 它类似于运行 Windows Server 2016 的服务器核心安装选项和超级\-V 角色。|
|![管理符号](media/All_Symbols_Administrator.png)|**配置和管理 Hyper-v 服务器**<br /><br />Hyper-v\-Server \(GUI\)没有图形用户界面。 你可以使用以下工具来配置和管理 Hyper-v\-V Server。<br /><br />-   [使用 Sconfig.cmd 配置 Windows server 2016 的服务器核心安装](../../get-started/sconfig-on-ws2016.md)，以更新域或工作组设置，更改 Windows 更新设置、启用远程管理等。<br />-对 Sconfig.cmd 中不可用的命令使用普通[命令提示符](../../administration/windows-commands/windows-commands.md)。<br />-使用[超级\-v 管理器](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/remote_host_management)或[Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm)远程管理\-hyper-v 服务器。 若要使用超级\-V 管理器，请在 Windows 10 或[Windows Server 2016](get-started/install-the-hyper-v-role-on-windows-server.md)[上安装超级\-V 角色](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)。<br />-有关不特定于超级\-V 的基本服务器功能，请参阅[安装服务器核心](../../get-started/getting-started-with-server-core.md)以获取其他管理选项。 其中所述的大部分管理方法也适用于超级\-Server。<br /><br />**配置和管理超级\-V 虚拟机**<br /><br />-   [为 hyper-v 虚拟机创建虚拟交换机](get-started/create-a-virtual-switch-for-hyper-v-virtual-machines.md)<br />-   [在 hyper-v 中创建虚拟机](get-started/create-a-virtual-machine-in-hyper-v.md)<br />-   [在标准或生产检查点之间进行选择](manage/choose-between-standard-or-production-checkpoints-in-hyper-v.md)<br />-   [启用或禁用检查点](manage/enable-or-disable-checkpoints-in-hyper-v.md)<br />-   [通过 PowerShell Direct 管理 Windows 虚拟机](manage/manage-windows-virtual-machines-with-powershell-direct.md) <br /><br />**部署**<br /><br />-   在[没有故障转移群集的情况下为实时迁移设置主机](deploy/set-up-hosts-for-live-migration-without-failover-clustering.md)<br />- [升级 Windows Server 群集节点](../../failover-clustering/cluster-operating-system-rolling-upgrade.md)<br />- [升级虚拟机版本](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md)<br />|
