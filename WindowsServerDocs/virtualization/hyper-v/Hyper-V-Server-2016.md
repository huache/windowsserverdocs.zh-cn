---
title: Microsoft Hyper-V Server 2016
ms.topic: get-started-article
ms.assetid: f815ada0-4c63-4e73-9c24-dc5eb21526c7
author: kbdazure
ms.author: kathydav
ms.date: 07/26/2017
ms.openlocfilehash: e99750caea4948f51f5f660f3b6f4b42766e833d
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87997071"
---
# <a name="microsoft-hyper-v-server-2016"></a>Microsoft Hyper-V Server 2016

Microsoft Hyper-V Server 2016 是独立的 \- 产品，仅包含 windows 虚拟机监控程序、Windows Server 驱动程序模型和虚拟化组件。 它提供简单可靠的虚拟化解决方案，以帮助提高服务器利用率并降低成本。

Microsoft Hyper-V Server 2016 中的 Windows 虚拟机监控程序技术与 \- Windows Server 2016 上的 "hyper-v" 角色中的内容相同。 因此，Windows Server 2016 上的 Hyper-v 角色可用的很多内容 \- 也适用于 Microsoft Hyper-V Server 2016。

## <a name="hyper-v-server-resources-for-it-pros"></a>\-适用于 IT 专业人员的 Hyper-v 服务器资源

|任务|资源|
|-|-|
|![满足要求符号](media/All_Symbols_MeetsRequirements.png)|**评估 Hyper-V**<p>-   [Hyper-v 技术概述](hyper-v-technology-overview.md)<br />- [Windows Server 2016 上的 Hyper-v 中的新增功能](what-s-new-in-hyper-v-on-windows.md)<br />-   [Windows Server 2016 上的 Hyper-v 的系统要求](system-requirements-for-hyper-v-on-windows.md)<br />-   [支持 Hyper-v 的 Windows 来宾操作系统](supported-windows-guest-operating-systems-for-hyper-v-on-windows.md)<br />-   [支持的 Linux 和 FreeBSD 虚拟机](supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows.md)<br />-   [功能与生成和来宾的兼容性](hyper-v-feature-compatibility-by-generation-and-guest.md)<p>**规划 Hyper-v**<p>-决定哪种[虚拟机生成](plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v.md)满足你的需求。 <br/>-如果你要移动或导入虚拟机，请决定[升级版本的](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md)时间。 <br />- [能力](plan/plan-hyper-v-scalability-in-windows-server.md) <br />- [上网](plan/plan-hyper-v-networking-in-windows-server.md) <br />- [安全](plan/plan-hyper-v-security-in-windows-server.md)|
|![入门符号](media/All_Symbols_GetStarted.png)|**Hyper-v 服务器入门**<p>[下载并安装 Microsoft 超 \-V Server 2016](https://www.microsoft.com/evalcenter/evaluate-hyper-v-server-2016)。 这将安装 Windows 虚拟机监控程序、Windows Server 驱动程序模型和虚拟化组件。 它类似于运行 Windows Server 2016 和 Hyper-v 角色的服务器核心安装选项 \- 。|
|![管理符号](media/All_Symbols_Administrator.png)|**配置和管理 Hyper-v 服务器**<p>Hyper-v \- 服务器没有图形用户界面 \( GUI \) 。 你可以使用以下工具来配置和管理 Hyper-v \- Server。<p>-   [使用 Sconfig.cmd 配置 Windows server 2016 的服务器核心安装](../../get-started/sconfig-on-ws2016.md)，以更新域或工作组设置，更改 Windows 更新设置、启用远程管理等。<br />-对 Sconfig.cmd 中不可用的命令使用普通[命令提示符](../../administration/windows-commands/windows-commands.md)。<br />-使用[Hyper-v \- 管理器](./manage/remotely-manage-hyper-v-hosts.md)或[Virtual Machine Manager](/system-center/vmm)来远程管理 hyper-v \- 服务器。 若要使用 Hyper-v \- 管理器，请[ \- 在 Windows 10](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)或[Windows Server 2016](get-started/install-the-hyper-v-role-on-windows-server.md)上安装 hyper-v 角色。<br />-有关不特定于 Hyper-v 的基本服务器功能，请参阅[安装服务器核心](../../get-started/getting-started-with-server-core.md)以获取其他管理选项 \- 。 其中所述的大部分管理方法也适用于 Hyper-v \- 服务器。<p>**配置和管理 Hyper-v \- 虚拟机**<p>-   [为 Hyper-v 虚拟机创建虚拟交换机](get-started/create-a-virtual-switch-for-hyper-v-virtual-machines.md)<br />-   [在 Hyper-v 中创建虚拟机](get-started/create-a-virtual-machine-in-hyper-v.md)<br />-   [在标准或生产检查点之间进行选择](manage/choose-between-standard-or-production-checkpoints-in-hyper-v.md)<br />-   [启用或禁用检查点](manage/enable-or-disable-checkpoints-in-hyper-v.md)<br />-   [通过 PowerShell Direct 管理 Windows 虚拟机](manage/manage-windows-virtual-machines-with-powershell-direct.md) <p>**部署**<p>-   [为无故障转移群集的实时迁移设置主机](deploy/set-up-hosts-for-live-migration-without-failover-clustering.md)<br />- [升级 Windows Server 群集节点](../../failover-clustering/cluster-operating-system-rolling-upgrade.md)<br />- [升级虚拟机版本](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md)<br />|