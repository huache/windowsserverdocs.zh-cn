---
title: 群集感知更新概述
description: 群集感知更新（CAU）在运行 Windows Server 的群集上自动执行软件更新安装。
ms.topic: article
ms.prod: windows-server
manager: lizross
author: JasonGerend
ms.author: jgerend
ms.technology: storage-failover-clustering
ms.date: 08/06/2018
ms.assetid: 3c2993b4-aa81-452b-a5c3-3724ad95d892
ms.openlocfilehash: bd3c15d08b0d4b6f174fd9c790f0dacb2457472e
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85473284"
---
# <a name="cluster-aware-updating-overview"></a>群集感知更新概述

> 适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本主题概述群集 \- 感知更新 \( CAU \) ，这是一项功能，可在群集服务器上自动执行软件更新过程，同时保持可用性。

> [!NOTE]
> 更新[存储空间直通](../storage/storage-spaces/storage-spaces-direct-overview.md)群集时，建议使用群集感知更新。

## <a name="feature-description"></a><a name="BKMK_OVER"></a>功能说明
群集感知更新是一项自动化功能，使你能够在[故障转移群集](failover-clustering-overview.md)中更新服务器，在更新过程中的可用性极少或无损失。 在更新运行期间，群集感知更新以透明方式执行以下任务：

1. 将群集的每个节点置于节点维护模式下。
2. 将群集角色移出节点。
3. 安装更新和所有从属更新。
4. 必要时执行重启。
5. 使节点退出维护模式。
6. 还原节点上的群集角色。
7. 移动以更新下一个节点。

对于群集中的许多群集角色，自动更新过程将触发计划的故障转移。 对连接的客户端而言，这可能导致暂时性服务中断。 但是，对于连续可用的工作负荷（例如 \- 具有实时迁移的 hyper-v 或具有 SMB 透明故障转移的文件服务器），群集感知更新可以在不影响服务可用性的情况下协调群集更新。

## <a name="practical-applications"></a>实际的应用程序

-   CAU 可减少群集服务中的服务中断，降低对手动更新解决方法的需求，并 \- 使 \- 管理员能够更可靠地进行端到端群集更新。 当 CAU 功能与连续可用的群集工作负荷（例如连续可用的文件服务器 \( 的文件服务器工作负荷，具有 SMB 透明故障转移或 hyper-v）结合使用时， \) \- 可以执行群集更新，但不会影响客户端的服务可用性。

-   CAU 方便在企业内部采用一致的 IT 流程。 可以为不同的故障转移群集类创建更新运行配置文件，然后在文件共享上集中管理这些配置文件，以确保整个 IT 组织内的 CAU 部署可以一致地应用更新，即使群集是由不同 \- \- 业务线或管理员管理的。

-   CAU 可以计划按照每天、每周或每月的定期间隔运行更新运行，有助于协调群集更新和其他 IT 管理过程。

-   CAU 提供了可扩展的体系结构，以群集感知方式更新群集软件清单 \- 。 发布者可以使用此功能来协调未发布到 Windows 更新或 Microsoft 更新的软件更新的安装，或者不能从 Microsoft 获得的软件更新的安装，例如，对于非 \- microsoft 设备驱动程序的更新。

-   CAU 自我 \- 更新模式允许 "机箱中的群集" 设备 \( 一组群集物理计算机，通常打包在一个机箱中 \) 以进行自我更新。 这类设备一般部署在只提供最少本地 IT 支持的分支机构中，用于管理群集。 自我 \- 更新模式可在这些部署方案中提供巨大价值。

## <a name="important-functionality"></a>重要功能
下面介绍了重要的群集感知更新功能：

-   用户界面 \( UI \) -群集感知更新窗口-和一组 cmdlet，可用于预览、应用、监视和报告更新

-   \- \- 群集更新操作的端到端自动化 \- \( ：更新运行 \) ，由一个或多个更新协调器计算机协调

-   一个默认插件 \- ，它与现有 Windows 更新 Agent \( WUA \) 和 \( \) Windows Server 中的 Windows Server Update Services WSUS 基础结构进行集成，以应用重要的 Microsoft 更新

-   第二个插件 \- 可用于应用 Microsoft 修补程序，可以对其进行自定义以应用非 \- Microsoft 更新

-   你使用“更新运行”选项的设置所配置的“更新运行配置文件”，例如每个节点更新可以重试的最大次数。 “更新运行配置文件”允许你迅速在各个更新运行之间重复使用相同设置并与其他故障转移群集共享更新设置。

-   支持新的插件开发的可扩展体系结构 \- \- ，以便在群集中协调其他节点更新工具，例如自定义软件安装程序、BIOS 更新工具和网络适配器或主机总线适配器 \( HBA \) 更新工具。

群集感知更新可以两种模式协调完整的群集更新操作：

-   **自检 \- 模式**：在此模式下，CAU 群集角色被配置为要更新的故障转移群集上的工作负荷，并定义关联的更新计划。 群集会通过使用默认或自定义更新运行配置文件在计划的时间自行更新。 在更新运行中，CAU 更新协调器进程会在当前拥有 CAU 群集角色的节点上启动，此进程就会按顺序在每个群集节点上执行更新。 为了更新当前的群集节点，CAU 群集角色将故障转移到另一个群集节点，该节点上新的更新协调器进程将接管更新运行的控制权。 在自我 \- 更新模式中，CAU 可以通过使用完全自动化的端 \- 到端更新过程来更新故障转移群集 \- 。 管理员还可以 \- 在此模式下按需触发更新，或者只是在 \- 需要时使用远程更新方法。 在自我 \- 更新模式中，管理员可通过连接到群集并运行**get \- invoke-caurun** Windows PowerShell cmdlet 来获取有关正在进行的更新运行的摘要信息。

-   **远程 \- 更新模式**对于此模式，将使用 CAU 工具配置远程计算机（称为更新协调器）。 更新协调器并不是在更新运行期间更新的群集的成员。 在远程计算机上，管理员 \- 通过使用默认或自定义更新运行配置文件，触发按需更新运行。 远程 \- 更新模式对于监视 \- 更新运行期间的实时进度以及在服务器核心安装上运行的群集非常有用。

## <a name="hardware-and-software-requirements"></a>硬件和软件要求

CAU 可在所有版本的 Windows Server 上使用，包括服务器核心安装。 有关详细要求信息，请参阅[群集感知更新要求和最佳实践](cluster-aware-updating-requirements.md)。

### <a name="installing-cluster-aware-updating"></a>安装群集感知更新
若要使用 CAU，请在 Windows Server 中安装故障转移群集功能并创建故障转移群集。 会在每个群集节点上自动安装支持 CAU 功能的组件。

若要安装故障转移群集功能，你可使用以下工具：
- 服务器管理器中的“添加角色和功能向导”
- [Add-windowsfeature](https://docs.microsoft.com/powershell/module/servermanager/Install-WindowsFeature?view=winserver2012r2-ps&viewFallbackFrom=win10-ps)  Windows PowerShell cmdlet
- 部署映像服务和管理 (DISM) 命令行工具

有关详细信息，请参阅[安装故障转移群集功能](create-failover-cluster.md#install-the-failover-clustering-feature)。

你还必须安装故障转移群集工具，该工具是远程服务器管理工具的一部分，并且在服务器管理器中安装故障转移群集功能时默认安装。 故障转移群集工具包括群集感知更新用户界面和 PowerShell cmdlet。

必须按如下所示安装故障转移群集工具以支持不同的 CAU 更新模式：

- 若要在自我更新模式中使用 CAU \- ，请在每个群集节点上安装故障转移群集工具。

- 若要启用远程 \- 更新模式，请在网络连接到故障转移群集的计算机上安装故障转移群集工具。

> [!NOTE]
> -   不能使用 Windows Server 2012 上的故障转移群集工具来管理较新版本的 Windows Server 上的群集感知更新。
> -   若要仅在远程更新模式中使用 CAU \- ，则不需要在群集节点上安装故障转移群集工具。 但是，某些 CAU 功能将不可用。 有关详细信息，请参阅[群集 \- 感知更新的要求和最佳方案](cluster-aware-updating-requirements.md)。
> -   除非仅在自我更新模式中使用 CAU \- ，否则，安装 cau 工具并且协调更新的计算机不能是故障转移群集的成员。

### <a name="enabling-self-updating-mode"></a>启用自我更新模式
若要启用自我更新模式，必须将群集感知更新群集角色添加到故障转移群集。 为此，请使用以下方法之一：
- 在服务器管理器中，选择 "**工具**" "  >  **群集感知更新**"，然后在 "群集感知更新" 窗口中选择 "**配置群集自我更新选项**"。
- 在 PowerShell 会话中，运行[add-cauclusterrole](https://docs.microsoft.com/powershell/module/clusterawareupdating/Add-CauClusterRole?view=win10-ps) cmdlet。

若要卸载 CAU，请使用服务器管理器、 [uninstall](https://docs.microsoft.com/powershell/module/servermanager/Uninstall-WindowsFeature?view=win10-ps) CMDLET 或 DISM 命令行工具卸载故障转移群集功能或故障转移群集工具 \- 。

### <a name="additional-requirements-and-best-practices"></a>其他要求和最佳做法

若要确保 CAU 成功更新群集节点，以及获取有关配置故障转移群集环境以使用 CAU 的其他指导，你可以运行 CAU 最佳做法分析器。

有关使用 CAU 的详细要求和最佳实践，以及有关运行 CAU 最佳做法分析器的信息，请参阅[群集 \- 感知更新的要求和最佳实践](cluster-aware-updating-requirements.md)。

### <a name="starting-cluster-aware-updating"></a>启动群集感知更新

##### <a name="to-start-cluster-aware-updating-from-server-manager"></a>从服务器管理器启动群集感知更新

1.  启动服务器管理器。

2.  执行下列操作之一：

    -   在 "**工具**" 菜单上，单击 "**群集 \- 感知更新**"。

    -   如果将一个或多个群集节点或群集添加到服务器管理器，请在 "**所有服务器**" 页上右键 \- 单击节点名称 \( 或群集名称 \) ，然后单击 "**更新群集**"。

## <a name="additional-references"></a>其他参考
以下链接提供了有关使用群集感知更新的详细信息。

-   [群集感知更新的要求和最佳做法 \-](cluster-aware-updating.md)

-   [群集 \- 感知更新：常见问题](cluster-aware-updating-faq.md)

-   [适用于 CAU 的高级选项和更新运行配置文件](cluster-aware-updating-options.md)

-   [CAU 插件的 \- 工作原理](cluster-aware-updating-plug-ins.md)

-   [\-Windows PowerShell 中的群集感知更新 cmdlet](https://docs.microsoft.com/powershell/module/clusterawareupdating/?view=win10-ps&viewFallbackFrom=winserverr2-ps)

-   [群集 \- 感知更新插件 \- 引用](https://docs.microsoft.com/previous-versions/windows/desktop/mscs/cluster-aware-update-plug-in-interfaces-and-classes)


