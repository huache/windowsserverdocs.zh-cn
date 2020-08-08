---
title: 群集操作系统滚动升级
ms.topic: get-started-article
ms.assetid: 6e102c1f-df26-4eaa-bc7a-d0d55d3b82d5
author: jasongerend
ms.author: jgerend
manager: lizross
ms.date: 03/27/2018
ms.openlocfilehash: a1694bdb8af495073723a74f24b9d0e153d580b9
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87991091"
---
# <a name="cluster-operating-system-rolling-upgrade"></a>群集操作系统滚动升级

> 适用于：Windows Server 2019、Windows Server 2016

群集操作系统滚动升级允许管理员升级群集节点的操作系统，而无需停止 Hyper-v 或横向扩展文件服务器工作负荷。 使用此功能可以避免服务级别协议 (SLA) 的停机时间损失。

群集操作系统滚动升级具有以下优势：

- 运行 Hyper-v 虚拟机和横向扩展文件服务器 (SOFS 的故障转移群集) 工作负荷可以从 Windows Server 2012 R2 升级 (在群集的所有节点上运行 2016) 在群集的所有群集节点上运行 (不会造成停机。 其他群集工作负荷（例如 SQL Server）将在 (通常不到五分钟的时间内不可用) 会故障转移到 Windows Server 2016。
- 它不需要任何其他硬件。 尽管可以在群集操作系统滚动升级过程中将其他群集节点暂时添加到小型群集，以提高群集的可用性。
- 群集不需要停止或重新启动。
- 不需要新群集。 升级现有群集。 此外，将使用存储在 Active Directory 中的现有群集对象。
- 升级过程是可逆的，在客户选择 "无回车键"、所有群集节点都在运行 Windows Server 2016 时以及运行 Update-clusterfunctionallevel PowerShell cmdlet 时进行恢复。
- 群集在混合 OS 模式下运行时可以支持修补和维护操作。
- 它通过 PowerShell 和 WMI 支持自动化。
- 群集公共属性**update-clusterfunctionallevel**属性指明 Windows Server 2016 群集节点上的群集的状态。 可以使用 PowerShell cmdlet 从属于故障转移群集的 Windows Server 2016 群集节点查询此属性：
    ```PowerShell
    Get-Cluster | Select ClusterFunctionalLevel
    ```

    值**8**表示群集正在 Windows Server 2012 R2 功能级别运行。 值**9**表示群集正在 Windows Server 2016 功能级别运行。

本指南介绍群集操作系统滚动升级过程的各个阶段、安装步骤、功能限制和常见问题 (Faq) ，适用于 Windows Server 2016 中的以下群集操作系统滚动升级方案：
- Hyper-v 群集
- 横向扩展文件服务器群集

Windows Server 2016 不支持以下方案：
-  群集 OS 使用虚拟硬盘 ( vhdx 文件将来宾群集滚动升级为共享存储) 

System Center Virtual Machine Manager (SCVMM) 2016 完全支持群集操作系统滚动升级。 如果你使用的是 SCVMM 2016，请参阅[在 VMM 中执行 hyper-v 主机群集到 Windows Server 2016 的滚动升级](/system-center/vmm/hyper-v-rolling-upgrade?view=sc-vmm-1807)，以获取有关升级群集和自动执行本文档中所述步骤的指导。

## <a name="requirements"></a>要求
在开始群集 OS 滚动升级过程之前，请完成以下要求：

- 从运行 Windows Server (半年通道) 、Windows Server 2016 或 Windows Server 2012 R2 的故障转移群集开始。
- 不支持将存储空间直通群集升级到 Windows Server 1709 版。
- 如果群集工作负载为 Hyper-v Vm 或横向扩展文件服务器，则可以预见到零停机时间的升级。
- 使用以下方法之一，验证 Hyper-v 节点具有支持第二级寻址表 (SLAT) 的 Cpu;      -请查看[是否与 SLAT 兼容？WP8 SDK Tip 01](/archive/blogs/devfish/are-you-slat-compatible-wp8-sdk-tip-01)文章，其中介绍了两种方法来检查 cpu 是否支持[SLATs，以](/sysinternals/downloads/coreinfo)确定 CPU 是否支持 SLAT。

## <a name="cluster-transition-states-during-cluster-os-rolling-upgrade"></a>群集操作系统滚动升级期间的群集转换状态

本部分介绍使用群集操作系统滚动升级来升级到 Windows Server 2016 的 Windows Server 2012 R2 群集的各种转换状态。

为了使群集工作负荷在群集操作系统滚动升级过程中保持运行，将群集工作负荷从 Windows Server 2012 R2 节点移至 Windows Server 2016 节点的工作方式与两个节点都运行的是 Windows Server 2012 R2 操作系统相同。 将 Windows Server 2016 节点添加到群集时，它们会在 Windows Server 2012 R2 兼容模式下运行。 称为 "混合 OS 模式" 的新概念群集模式允许不同版本的节点存在于同一群集中 (参阅图 1) 。

![显示群集操作系统滚动升级三个阶段的插图：所有节点 Windows Server 2012 R2、混合 OS 模式和所有节点 Windows Server 2016 ](media/Cluster-Operating-System-Rolling-Upgrade/Clustering_RollingUpgrade_Overview.png)
 **图1：群集操作系统状态转换**

将 Windows Server 2016 节点添加到群集时，Windows Server 2012 R2 群集将进入混合 OS 模式。 此过程完全可逆-可以从群集中删除 Windows Server 2016 节点，并且可以在此模式下将 Windows Server 2012 R2 节点添加到群集中。 如果在群集上运行 Update-clusterfunctionallevel PowerShell cmdlet，则会出现 "不返回点"。 为了使此 cmdlet 成功，所有节点都必须是 Windows Server 2016，并且所有节点必须都处于联机状态。

## <a name="transition-states-of-a-four-node-cluster-while-performing-rolling-os-upgrade"></a>执行滚动 OS 升级时，四个节点的群集的转换状态

本部分介绍和描述了群集的四个不同阶段，其中包含共享存储，其节点从 Windows Server 2012 R2 升级到 Windows Server 2016。

"阶段 1" 是初始状态-从 Windows Server 2012 R2 群集开始。

![显示初始状态的插图：所有节点 Windows Server 2012 R2 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_Stage1.png)
 **图2：初始状态： windows Server 2012 R2 故障转移群集 (阶段 1) **

在 "阶段 2" 中，使用 Windows Server 2016 暂停、排出、逐出、重新格式化和安装两个节点。

![显示混合 OS 模式下的群集的插图：示例 4-节点群集，两个节点正在运行 Windows Server 2016，两个节点正在运行 Windows Server 2012 R2 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_Stage2.png)
 **图3：中间状态：混合 OS 模式： Windows Server 2012 R2 和 Windows Server 2016 故障转移群集 (第2阶段) **

在 "阶段 3" 中，群集中的所有节点都已升级到 Windows Server 2016，并且群集已准备好使用 Update-clusterfunctionallevel PowerShell cmdlet 进行升级。

> [!NOTE]
> 在此阶段，可以完全反转进程，并将 Windows Server 2012 R2 节点添加到此群集中。

![此图显示群集已完全升级到 Windows Server 2016，并且已准备好进行 Update-clusterfunctionallevel cmdlet，以便将群集功能级别提升到 Windows Server 2016 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_Stage3.png)
 **图4：中间状态：所有节点已升级到 windows server 2016，已准备好进行更新-update-clusterfunctionallevel (第3阶段) **

运行 ClusterFunctionalLevelcmdlet 后，群集将进入 "阶段 4"，其中可以使用新的 Windows Server 2016 群集功能。

![显示群集滚动 OS 升级已成功完成的插图;所有节点都已升级到 Windows Server 2016，并且群集正在 Windows Server 2016 群集功能级别运行 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_Stage4.png)
 **。图5：最终状态： Windows Server 2016 故障转移群集 (阶段 4) **

## <a name="cluster-os-rolling-upgrade-process"></a>群集操作系统滚动升级过程

本部分介绍用于执行群集操作系统滚动升级的工作流。

![图示 ](media/Cluster-Operating-System-Rolling-Upgrade/Clustering_RollingUpgrade_Workflow.png)
 **：群集操作系统滚动升级过程工作**流

群集操作系统滚动升级包括以下步骤：

1. 为操作系统升级准备群集，如下所示：
    1. 群集操作系统滚动升级需要从群集中一次删除一个节点。 检查群集上是否有足够的容量来维护 HA Sla （当从群集中删除其中一个群集节点进行操作系统升级时）。 换句话说，在群集操作系统滚动升级过程中，如果从群集中删除一个节点，你是否需要将工作负荷故障转移到另一个节点？ 如果从群集中删除一个节点进行群集操作系统滚动升级，则群集是否具有运行所需工作负荷的容量？
    2. 对于 Hyper-v 工作负荷，请检查所有 Windows Server 2016 Hyper-v 主机是否具有 CPU 支持二级地址表 (SLAT) 。 仅支持 SLAT 的计算机可以使用 Windows Server 2016 中的 Hyper-v 角色。
    3. 检查是否已完成任何工作负荷备份，并考虑备份群集。 在将节点添加到群集时停止备份操作。
    4. 使用 cmdlet 检查所有群集节点是否处于联机状态/running/up [`Get-ClusterNode`](/powershell/module/failoverclusters/Get-ClusterNode?view=win10-ps) (参阅图 7) 。

        ![截图显示运行 Start-clusternode cmdlet 的结果 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_GetClusterNode.png) **图7：使用 Start-clusternode cmdlet 确定节点状态**

    5. 如果正在 (CAU) 运行群集感知更新，请使用**群集感知更新**UI 或 cmdlet 验证当前是否正在运行 cau [`Get-CauRun`](/powershell/module/clusterawareupdating/Get-CauRun?view=win10-ps) (参见图 8) 。 使用 cmdlet 停止 CAU [`Disable-CauClusterRole`](/powershell/module/clusterawareupdating/Disable-CauClusterRole?view=win10-ps) (参阅图 9) ，以防止在群集 OS 滚动升级过程中，CAU 暂停和耗尽任何节点。

        ![截图显示 Invoke-caurun cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_GetCAU.png) **图8：使用 [`Get-CauRun`](/powershell/module/clusterawareupdating/Get-CauRun?view=win10-ps) Cmdlet 确定群集感知更新是否正在群集上运行**

        ![截图显示 Add-cauclusterrole cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_DisableCAU.png) **图9：使用 [`Disable-CauClusterRole`](/powershell/module/clusterawareupdating/Disable-CauClusterRole?view=win10-ps) Cmdlet 禁用群集感知更新角色**

2. 对于群集中的每个节点，完成以下操作：
    1. 使用群集管理器 UI，选择节点并使用 "**暂停" |排出菜单选项**若要排出节点 (参阅图 10) 或使用 [`Suspend-ClusterNode`](/powershell/module/failoverclusters/Suspend-ClusterNode?view=win10-ps) cmdlet (参见图 11) 。

        ![截图演示如何使用群集管理器 UI 排出角色 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_FCM_DrainRoles.png) **图10：使用故障转移群集管理器排出节点中的角色**

        ![截图显示 Start-clusternode cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_SuspendNode.png) **图11：使用 [`Suspend-ClusterNode`](/powershell/module/failoverclusters/Suspend-ClusterNode?view=win10-ps) Cmdlet 从节点排出角色**

    2.  使用群集管理器 UI，从群集中**逐出**暂停的节点，或使用 [`Remove-ClusterNode`](/powershell/module/failoverclusters/Remove-ClusterNode?view=win10-ps) cmdlet。

        ![截图显示 Start-clusternode cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_RemoveNode.png)
         **图12：使用 [`Remove-ClusterNode`](/powershell/module/failoverclusters/Remove-ClusterNode?view=win10-ps) cmdlet 从群集中删除节点**

    3.  使用**自定义：仅安装 windows (advanced) **安装，重新格式化系统驱动器并在节点上执行 Windows Server 2016 的 "干净操作系统安装" (参见图 13) setup.exe 选项。 避免选择 "**升级：安装 Windows 并保留文件、设置和应用程序**" 选项，因为群集 OS 滚动升级不鼓励就地升级。

        ![Windows Server 2016 安装向导的截图，其中显示了所选的 "自定义安装" 选项 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_InstallOption.png)
         **图13： Windows Server 2016 的可用安装选项**

    4.  将节点添加到相应的 Active Directory 域。
    5.  将相应用户添加到管理员组。
    6.  使用服务器管理器 UI 或 Add-windowsfeature PowerShell cmdlet 安装所需的任何服务器角色，如 Hyper-v。

        ```PowerShell
        Install-WindowsFeature -Name Hyper-V
        ```

    7.  使用服务器管理器 UI 或 Add-windowsfeature PowerShell cmdlet 安装故障转移群集功能。

        ```PowerShell
        Install-WindowsFeature -Name Failover-Clustering
        ```

    8.  安装群集工作负载所需的任何其他功能。
    9. 使用故障转移群集管理器 UI 检查网络和存储连接设置。
    10. 如果使用的是 Windows 防火墙，请检查群集的防火墙设置是否正确。 例如，群集感知更新 (CAU) 启用的群集可能需要防火墙配置。
    11. 对于 Hyper-v 工作负荷，请使用 Hyper-v 管理器 UI 启动 "虚拟交换机管理器" 对话框 (参见图 14) 。

        检查群集中的所有 Hyper-v 主机节点所使用的虚拟交换机)  (的名称是否相同。

        ![显示 Hyper-v 虚拟交换机管理器对话框位置的截图 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_VMSwitch.png)
         **图14：虚拟交换机管理器**

    12. 在 Windows Server 2016 节点上 (不要使用 Windows Server 2012 R2 节点) ，请使用故障转移群集管理器 (参阅图 15) 连接到群集。

        ![显示 "选择群集" 对话框的截图 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_AddNode.png)
         **图15：使用故障转移群集管理器向群集添加节点**

    13. 使用故障转移群集管理器 UI 或 [`Add-ClusterNode`](/powershell/module/failoverclusters/Add-ClusterNode?view=win10-ps) cmdlet (参见图 16) ，将节点添加到群集。

        ![截图显示 Start-clusternode cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_AddNode3.png)
         **图16：使用 [`Add-ClusterNode`](/powershell/module/failoverclusters/Add-ClusterNode?view=win10-ps) Cmdlet 向群集添加节点**

        > [!NOTE]
        > 当第一个 Windows Server 2016 节点加入群集时，群集将进入 "混合 OS" 模式，并且群集核心资源会移动到 Windows Server 2016 节点。 混合操作系统模式群集是一个功能齐全的群集，其中的新节点在与旧节点兼容模式下运行。 "混合 OS" 模式是群集的暂时性模式。 这并不是永久性的，并且期望客户在四周更新其群集的所有节点。

    14. 将 Windows Server 2016 节点成功添加到群集后，你可以 () 选择将某些群集工作负荷移动到新添加的节点，以便在群集间重新平衡工作负荷，如下所示：

        ![截图显示 Move-clustervirtualmachinerole cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_MoveVMRole.png)
         **图17：使用 [`Move-ClusterVirtualMachineRole`](/powershell/module/failoverclusters/Move-ClusterVirtualMachineRole?view=win10-ps) cmdlet 将群集工作负荷移 (群集 VM 角色) **

        1. 使用故障转移群集管理器**实时迁移**虚拟机或 [`Move-ClusterVirtualMachineRole`](/powershell/module/failoverclusters/Move-ClusterVirtualMachineRole?view=win10-ps) Cmdlet (参阅图 17) 执行虚拟机的实时迁移。

            ```PowerShell
            Move-ClusterVirtualMachineRole -Name VM1 -Node robhind-host3
            ```

        2. 对于**Move**其他群集工作负载，请使用从故障转移群集管理器或 [`Move-ClusterGroup`](/powershell/module/failoverclusters/Move-ClusterGroup?view=win10-ps) cmdlet 进行移动。

3. 如果每个节点都已升级到 Windows Server 2016 并添加回群集，或者已逐出任何其他 Windows Server 2012 R2 节点，请执行以下操作：

    > [!IMPORTANT]
    > -   更新群集功能级别后，无法返回到 Windows Server 2012 R2 功能级别，并且无法将 Windows Server 2012 R2 节点添加到群集。
    > -   在 [`Update-ClusterFunctionalLevel`](/powershell/module/failoverclusters/Update-ClusterFunctionalLevel?view=win10-ps) 运行 cmdlet 之前，该过程是完全可逆的，可以将 Windows server 2012 R2 节点添加到此群集，并且可以删除 Windows server 2016 节点。
    > -   [`Update-ClusterFunctionalLevel`](/powershell/module/failoverclusters/Update-ClusterFunctionalLevel?view=win10-ps)运行 cmdlet 后，新功能将可用。

    1.  使用故障转移群集管理器 UI 或 [`Get-ClusterGroup`](/powershell/module/failoverclusters/Get-ClusterGroup?view=win10-ps) cmdlet 检查群集上的所有群集角色是否按预期运行。 在以下示例中，未使用可用存储，而是使用 CSV，因此，可用存储显示**脱机**状态 (参见图 18) 。

        ![截图显示 Get-clustergroup cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_GetClusterGroup.png)
         **图18：验证所有群集组 (群集角色) 是否正在使用 [`Get-ClusterGroup`](/powershell/module/failoverclusters/Get-ClusterGroup?view=win10-ps) cmdlet 运行**

    2.  使用 cmdlet 检查所有群集节点是否均已联机且正在运行 [`Get-ClusterNode`](/powershell/module/failoverclusters/Get-ClusterNode?view=win10-ps) 。
    3.  运行 [`Update-ClusterFunctionalLevel`](https://technet.microsoft.com/library/mt589702.aspx) cmdlet-不应返回任何错误 (参见图 19) 。

        ![截图显示 Update-clusterfunctionallevel cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_SelectFunctionalLevel.png)
         **图19：使用 PowerShell 更新群集的功能级别**

    4.  [`Update-ClusterFunctionalLevel`](/powershell/module/failoverclusters/Update-ClusterFunctionalLevel?view=win10-ps)运行 cmdlet 后，可以使用新功能。

4. Windows Server 2016-恢复常规群集更新和备份：

    1. 如果以前运行过 CAU，请使用 CAU UI 重启它，或使用 [`Enable-CauClusterRole`](/powershell/module/clusterawareupdating/Enable-CauClusterRole?view=win10-ps) cmdlet (参阅图 20) 。

        ![截图显示 Add-cauclusterrole ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_EnableCAUClusterRole.png) **图20：使用 [`Enable-CauClusterRole`](/powershell/module/clusterawareupdating/Enable-CauClusterRole?view=win10-ps) Cmdlet 启用群集感知更新角色**的输出

    2. 恢复备份操作。

5. 启用并使用 Hyper-v 虚拟机上的 Windows Server 2016 功能。

    1. 群集升级到 Windows Server 2016 功能级别后，许多工作负荷（如 Hyper-v Vm）将具有新功能。 ，获取新的 Hyper-v 功能的列表。 请参阅[迁移和升级虚拟机](../virtualization/hyper-v/deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md)

    2. 在群集中的每个 Hyper-v 主机节点上，使用 [`Get-VMHostSupportedVersion`](/powershell/module/hyper-v/Get-VMHostSupportedVersion?view=win10-ps) cmdlet 查看主机支持的 HYPER-V VM 配置版本。

        ![截图显示 VMHostSupportedVersion cmdlet 的输出 ](media/Cluster-Operating-System-Rolling-Upgrade/Clustering_GetVMHostSupportVersion.png) **图21：查看主机支持的 hyper-v VM 配置版本**

   3. 在群集中的每个 Hyper-v 主机节点上，可以通过使用用户计划简短的维护时段、备份、关闭虚拟机并运行 cmdlet 来升级 Hyper-v VM 配置版本 [`Update-VMVersion`](/powershell/module/hyper-v/Update-VMVersion?view=win10-ps) (参见图 22) 。 这将更新虚拟机版本并启用新的 Hyper-v 功能，无需再 (IC) 更新。 此 cmdlet 可以从托管 VM 的 Hyper-v 节点运行，也 `-ComputerName` 可以使用参数远程更新 Vm 版本。 在此示例中，我们将 VM1 的配置版本从5.0 升级到7.0，以利用与此 VM 配置版本关联的许多新 Hyper-v 功能，如生产检查点 (应用程序一致性备份) 和二进制 VM 配置文件。

       ![截图在操作图22中显示 VMVersion cmdlet ](media/Cluster-Operating-System-Rolling-Upgrade/Cluster_RollingUpgrade_StopVM.png) **：使用 VMVersion PowerShell CMDLET 升级 VM 版本**

6. 可以使用[StoragePool](/powershell/module/storage/Update-StoragePool?view=win10-ps) PowerShell cmdlet 升级存储池-这是一个联机操作。

尽管我们的目标是私有云方案（特别是可以在不停机的情况下升级的 Hyper-v 和横向扩展文件服务器群集），但群集 OS 滚动升级过程可用于任何群集角色。

## <a name="restrictions--limitations"></a>限制/限制
- 此功能仅适用于 Windows Server 2012 R2 到 Windows Server 2016 版本。 此功能无法将早期版本的 Windows Server （如 Windows Server 2008、Windows Server 2008 R2 或 Windows Server 2012）升级到 Windows Server 2016。
- 每个 Windows Server 2016 节点应重新格式化/仅新安装。 不建议 "就地" 或 "升级" 安装类型。
- Windows Server 2016 节点必须用于向群集添加 Windows Server 2016 节点。
- 管理混合 OS 模式群集时，始终从运行 Windows Server 2016 的上级节点执行管理任务。 下层 Windows Server 2012 R2 节点不能对 Windows Server 2016 使用 UI 或管理工具。
- 我们鼓励客户快速浏览群集升级过程，因为某些群集功能没有针对混合 OS 模式进行优化。
- 由于从 Windows server 2016 节点故障转移到下层 Windows Server 2012 R2 节点的故障转移可能不兼容，因此应避免在 Windows Server 2016 节点上创建或调整其大小。

## <a name="frequently-asked-questions"></a>常见问题
**故障转移群集在混合 OS 模式下运行的时间有多长？**
我们鼓励客户在四周内完成升级。 Windows Server 2016 中有很多优化。 我们已成功升级 Hyper-v 和横向扩展文件服务器群集，在四个小时内不会出现停机时间。

**是否会将此功能移植回 Windows Server 2012、Windows Server 2008 R2 或 Windows Server 2008？**
我们没有任何计划将此功能移植回以前的版本。 群集操作系统滚动升级是将 Windows Server 2012 R2 群集升级到 Windows Server 2016 和更高版本的愿景。

**Windows Server 2012 R2 群集是否需要在开始群集 OS 滚动升级过程之前安装所有软件更新？**
是，在开始群集 OS 滚动升级过程之前，请验证是否已更新所有群集节点的最新软件更新。

**[`Update-ClusterFunctionalLevel`](/powershell/module/failoverclusters/Update-ClusterFunctionalLevel?view=win10-ps)节点关闭或暂停时，是否可以运行 cmdlet？**
否。 所有群集节点都必须处于启用状态，并且在 active 成员身份中，才能使该 [`Update-ClusterFunctionalLevel`](/powershell/module/failoverclusters/Update-ClusterFunctionalLevel?view=win10-ps) cmdlet 正常运行。

**群集操作系统滚动升级是否适用于任何群集工作负荷？它是否适用于 SQL Server？**
是的，群集操作系统滚动升级适用于任何群集工作负荷。 但是，Hyper-v 和横向扩展文件服务器群集只需零停机时间。 大多数其他工作负载会导致一些停机时间， (通常几分钟后) 故障转移，并且在群集 OS 滚动升级过程中至少需要一次故障转移。

**是否可以使用 PowerShell 自动执行此过程？**
是的，我们已设计好群集操作系统滚动升级，可以使用 PowerShell 自动完成。

**对于具有额外工作负荷和故障转移容量的大型群集，能否同时升级多个节点？**
是的。 从群集中删除一个节点以升级 OS 时，群集将有一个较小的故障转移节点，因此，故障转移能力会降低。 对于具有足够工作负荷和故障转移容量的大型群集，可以同时升级多个节点。 可以暂时将群集节点添加到群集，以便在群集操作系统滚动升级过程中提供改善的工作负荷和故障转移容量。

**如果在成功运行后发现群集中的问题，该怎么办 [`Update-ClusterFunctionalLevel`](/powershell/module/failoverclusters/Update-ClusterFunctionalLevel?view=win10-ps) ？**
如果在运行之前已使用系统状态备份对群集数据库进行了备份 [`Update-ClusterFunctionalLevel`](/powershell/module/failoverclusters/Update-ClusterFunctionalLevel?view=win10-ps) ，则应该能够在 Windows Server 2012 R2 群集节点上执行权威还原，并还原原始群集数据库和配置。

**是否可以对每个节点使用就地升级，而不是通过重新格式化系统驱动器来使用干净的安装？**
我们不鼓励使用 Windows Server 的就地升级，但我们知道，在使用默认驱动程序的某些情况下，它可以正常工作。 请仔细阅读群集节点就地升级过程中显示的所有警告消息。

**如果要在 Hyper-v 群集上为 Hyper-v VM 使用 Hyper-v 复制，则在群集操作系统滚动升级过程中和之后，复制是否保持不变？**
是的，在群集操作系统滚动升级过程中和之后，Hyper-v 副本将保持不变。

**是否可以使用 System Center 2016 Virtual Machine Manager (SCVMM) 自动执行群集操作系统滚动升级过程？**
是的，你可以使用 System Center 2016 中的 VMM 自动执行群集操作系统滚动升级过程。

## <a name="additional-references"></a>其他参考
-   [发行说明：Windows Server 2016 中的重要问题](../get-started/windows-server-2016-ga-release-notes.md)
-   [Windows Server 2016 中的新增功能](../get-started/whats-new-in-windows-server-2016.md)
-   [Windows Server 中的故障转移群集的新增功能](whats-new-in-failover-clustering.md)