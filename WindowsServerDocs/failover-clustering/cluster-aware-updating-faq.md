---
ms.assetid: 6416d125-bcaf-433d-971a-2f0283bca2c2
title: 群集感知更新-常见问题
ms.topic: article
ms.prod: windows-server
manager: lizross
ms.author: jgerend
author: JasonGerend
ms.date: 04/28/2017
description: 有关 Windows Server 中的群集感知更新的常见问题的解答。
ms.openlocfilehash: ca81e952c0524af36ab6d241a205bd1cc971c74a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80828100"
---
# <a name="cluster-aware-updating-frequently-asked-questions"></a>群集感知更新：常见问题

> 适用于： Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

[群集感知更新](cluster-aware-updating.md)\(CAU\) 是一项协调故障转移群集中所有服务器上的软件更新的功能，这种方法不会影响服务可用性，而不会影响群集节点的计划内故障转移。 对于一些具有连续可用性功能的应用程序 \(如使用实时迁移的 Hyper-v\-V 或具有 SMB 透明故障转移的 SMB 1.x 文件服务器\)，CAU 可协调自动群集更新，而不影响服务可用性。

## <a name="does-cau-support-updating-storage-spaces-direct-clusters"></a>CAU 是否支持更新存储空间直通群集？  
可以。 CAU 支持更新[存储空间直通](../storage/storage-spaces/storage-spaces-direct-overview.md)群集，而不考虑部署类型：超聚合或聚合。 具体而言，CAU 业务流程可确保暂停每个群集节点等待底层群集存储空间正常。

## <a name="does-cau-work-with-windowsserver-2008r2-or-windows7"></a>CAU 是否可以与 Windows Server 2008 R2 或 Windows 7 一起使用？  
No。 CAU 仅在运行 Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows 10、Windows 8.1 或 Windows 8 的计算机中协调群集更新操作。 正在更新的故障转移群集必须运行 Windows Server 2016、Windows Server 2012 R2 或 Windows Server 2012。
  
## <a name="is-cau-limited-to-specific-clustered-applications"></a>CAU 是否限于特定的群集应用程序？  
No。 CAU 对于群集应用程序类型是不可知的。 CAU 是\-更新在群集 Api 和 PowerShell cmdlet 之上分层的解决方案的外部群集。 同样，CAU 可以协调 Windows Server 故障转移群集中配置的任何群集应用程序的更新。  
  
> [!NOTE]  
> 目前，对以下群集工作负载进行 CAU 测试和认证： SMB、超级\-V、DFS 复制、DFS 命名空间、iSCSI 和 NFS。  
  
## <a name="does-cau-support-updates-from-microsoft-update-and-windows-update"></a>CAU 是否支持从 Microsoft Update 和 Windows Update 更新？  
可以。 默认情况下，CAU 配置有一个在群集节点上使用 Windows 更新代理 \(WUA\) 实用工具 Api 的插件\-。 WUA 基础结构可配置为指向 Microsoft 更新和 Windows 更新或 Windows Server Update Services \(WSUS\) 作为其更新源。  
  
## <a name="does-cau-support-wsus-updates"></a>CAU 是否支持 WSUS 更新？  
可以。 默认情况下，CAU 配置有一个在群集节点上使用 Windows 更新代理 \(WUA\) 实用工具 Api 的插件\-。 WUA 基础结构可配置为指向 Microsoft 更新和 Windows 更新或本地 Windows Server Update Services \(WSUS\) 服务器作为其更新源。  
  
## <a name="can-cau-apply-limited-distribution-release-updates"></a>CAU 是否可应用有限分发版本更新？  
可以。 有限分发版本 \(LDR\) 更新（也称为修补程序）不通过 Microsoft 更新或 Windows 更新发布，因此不能通过 Windows 更新代理 \(WUA 下载它们，\) 默认情况下，CAU 中的\-。  
  
但是，CAU 包含第二个插\-，你可以选择应用修补程序更新。 还可以自定义此修补程序的插入\-，以应用非\-Microsoft 驱动程序、固件和 BIOS 更新。  
  
## <a name="can-i-use-cau-to-apply-cumulative-updates"></a>我是否可以使用 CAU 来应用累积更新？  
可以。 如果累积更新是常规的分发版本更新或 LDR 更新，CAU 可以应用它们。  
  
## <a name="can-i-schedule-updates"></a>能否计划更新？  
可以。 CAU 支持以下更新模式，都允许对更新进行计划：  
  
**自行\-更新**允许群集根据定义的配置文件和定期计划（例如在每月维护时段内）更新自身。 你还可以随时启动\-按需更新运行。 若要启用自行\-更新模式，必须将 CAU 群集角色添加到群集。 CAU 自我\-更新功能与其他任何群集工作负荷一样，可与更新协调器计算机的计划内和计划外故障转移无缝协作。  
  
**远程\-更新**使你能够在运行 Windows 或 Windows Server 的计算机上随时启动更新运行。 可以通过群集感知更新窗口或通过使用**Invoke\-Invoke-caurun** PowerShell cmdlet 来启动更新运行。 远程\-更新是 CAU 的默认更新模式。 你可使用任务计划程序从不属于群集节点的远程计算机对所需的计划运行 [Invoke-CauRun](https://technet.microsoft.com/itpro/powershell/windows/cluster-aware-updating/invoke-caurun) cmdlet。  
  
## <a name="can-i-schedule-updates-to-apply-during-a-backup"></a>能否计划在备份期间应用更新？  
可以。 在这方面，CAU 不会施加任何约束。 但是，当服务器备份正在进行时，在服务器\) \(上执行软件更新将不是一种最佳做法。 请注意：CAU 只会依赖群集 API 确定资源故障转移和故障回复；因此，CAU 不知道服务器备份状态。  
  
## <a name="can-cau-work-with-configuration-manager"></a>CAU 能否与 Configuration Manager 配合工作？  
CAU 是一种工具，用于协调群集节点上的软件更新，并 Configuration Manager 还执行服务器软件更新。 必须配置这些工具，使其不会在任何数据中心部署中覆盖相同的服务器，包括使用不同 Windows Server Update Services 服务器。 这可确保使用 CAU 后的目标不会无意中失效，因为 Configuration Manager\-驱动的更新不会合并群集感知。  
  
## <a name="do-i-need-administrative-credentials-to-run-cau"></a>我是否需要管理凭据才能运行 CAU？  
可以。 为了运行 CAU 工具，CAU 需要本地服务器的管理凭据或需要运行所在本地服务器或客户端计算机的“身份验证后模拟客户端”用户权限。 但是，若要协调群集节点上的软件更新，CAU 需要每个节点上的群集管理凭据。 尽管 CAU UI 无需凭据即可启动，但它会在连接到群集实例以预览或应用更新时提示输入群集管理凭据。  
  
## <a name="can-i-script-cau"></a>能否为 CAU 编写脚本？  
可以。 CAU 附带 PowerShell cmdlet，提供一组丰富的脚本选项。 其中有和 CAU UI 为了执行 CAU 操作所调用的相同的 cmdlet。  

## <a name="what-happens-to-active-clustered-roles"></a>活动群集角色会发生什么情况？

群集角色 \(以前称为应用程序和服务\)，在节点上处于活动状态，可以在软件更新开始之前故障转移到其他节点。 CAU 通过使用维护模式来编排这些故障转移，该模式可暂停和耗尽节点的所有活动群集角色。 当软件更新完成时，CAU 恢复节点，群集角色会故障回复到更新节点。 这就确保相对于节点的群集角色分布在一个群集的 CAU 更新运行中保持相同。  
  
## <a name="how-does-cau-select-target-nodes-for-clustered-roles"></a>CAU 如何选择群集角色的目标节点？

CAU 依赖群集 API 协调故障转移。 群集 API 实现通过依赖于内部指标和智能放置试探法 \(（例如跨目标节点\) 的工作负荷级别）选择目标节点。  
  
## <a name="does-cau-load-balance-the-clustered-roles"></a>CAU 负载是否会平衡群集角色？

CAU 不会对群集节点进行负载平衡，但它会尝试保留群集角色的分布。 当 CAU 完成群集节点的更新时，它会尝试将以前托管的群集角色的故障回复到该节点。 CAU 依赖群集 API 将资源故障回复到暂停程序的开始处。 由于没有计划外故障转移和首选所有者设置，群集角色的分布会保持不变。  
  
## <a name="how-does-cau-select-the-order-of-nodes-to-update"></a>CAU 如何选择节点的更新顺序？  
默认情况下，CAU 会根据活动的级别选择节点的更新顺序。 托管最少群集角色节点会最先更新。 但是，管理员可以通过在 CAU UI 中为更新运行指定参数或使用 PowerShell cmdlet 来指定更新节点的特定顺序。  
  
## <a name="what-happens-if-a-cluster-node-is-offline"></a>如果群集节点处于脱机状态，会发生什么情况？

启动更新运行的管理员可指定能脱机的节点数量的可接受阈值。 因此，即使所有群集节点都没有联机，更新运行仍然可以在群集上继续。  
  
## <a name="can-i-use-cau-to-update-only-a-single-node"></a>是否可以使用 CAU 仅更新单个节点？  
No。 CAU 是\-作用域更新工具的群集，因此它只允许你选择要更新的群集。 如果希望更新单独一个节点，你可使用 CAU 以外的已有服务器工具。  
  
## <a name="can-cau-report-updates-that-are-initiated-from-outside-cau"></a>是否可以从 CAU 外部启动 CAU 报表更新？  
No。 CAU 仅可报告在 CAU 内启动的更新运行。 但是，当后续的 CAU 更新运行启动时，将适当地考虑通过非\-CAU 方法安装的更新，以确定可能适用于每个群集节点的其他更新。  
  
## <a name="can-cau-support-my-unique-it-process-needs"></a>CAU 是否可以支持我的独特 IT 流程需求？  
可以。 CAU 提供以下尺度的灵活性来满足企业客户的独特 IT 程序需求：  
  
**脚本**更新运行可以指定预\-更新 PowerShell 脚本和 post\-更新 PowerShell 脚本。 在暂停节点之前，将在每个群集节点上运行预\-更新脚本。 安装节点更新后，会在每个群集节点上运行 post\-更新脚本。  
  
> [!NOTE]  
> 若要在每个群集节点上运行\-update 和 post\-更新脚本，必须在每个群集节点上安装 .NET Framework 4.6 或4.5 和 PowerShell。 还必须在群集节点上启用 PowerShell 远程处理。 有关详细的系统要求，请参阅[群集感知更新的要求和最佳方案](cluster-aware-updating-requirements.md)。  
  
**高级更新运行选项**管理员还可以从大量高级更新运行选项中进行指定，例如每个节点上重试更新过程的最大次数。 可以使用 CAU UI 或 CAU PowerShell cmdlet 指定这些选项。 这些自定义设置可以保存在更新运行配置文件中，供以后执行更新运行时重复使用。  
  
**体系结构中的公用即插\-** CAU 包含注册、注销和选择插件\-的功能。 CAU 附带了两个默认的插件\-：一个在每个群集节点上协调 Windows 更新代理 \(WUA\) Api;第二个应用手动复制到群集节点可访问的文件共享的修补程序。 如果企业有这两个即插即用\-无法满足的独特需求，企业可以根据公共 API 规范构建一个新的 CAU 插件\-。 有关详细信息，请参阅[群集\-感知更新插件\-引用](https://msdn.microsoft.com/library/hh418084(VS.85).aspx)。  
  
若要了解如何配置和自定义 CAU 插件\-以支持不同的更新方案，请参阅[插件\-的工作方式](assetId:///847b571b-12b3-473c-953f-75a5a1f51333)。  
  
## <a name="how-can-i-export-the-cau-preview-and-update-results"></a>如何导出 CAU 预览和更新结果？  
CAU 通过命令\-line 接口和 UI 提供导出选项。  
  
**命令\-行接口选项：**  
  
-   使用 PowerShell cmdlet 调用预览结果 **\-invoke-causcan |Convertto-html\-Xml**。 输出：XML  
  
-   使用 PowerShell cmdlet 调用报告结果 **\-invoke-caurun |Convertto-html\-Xml**。 输出：XML  
  
-   使用 PowerShell cmdlet **Get\-get-caureport 来报告结果 |导出\-Get-caureport**。 输出：HTML、CSV  
  
**UI 选项：**  
  
-   从 **“预览更新”** 屏幕复制报告结果。 输出：CSV  
  
-   从 **“生成报告”** 屏幕复制报告结果。 输出：CSV  
  
-   从 **“生成报告”** 屏幕导出报告结果。 输出：HTML  
  
## <a name="how-do-i-install-cau"></a>如何安装 CAU？  
CAU 安装已无缝集成到故障转移群集功能中。 CAU 安装方式如下：  
  
-   在群集节点上安装故障转移群集时，将自动安装 CAU Windows Management Instrumentation \(WMI\) 提供程序。  
  
-   当在服务器或客户端计算机上安装故障转移群集工具功能时，将自动安装群集感知更新 UI 和 PowerShell cmdlet。
  
## <a name="does-cau-need-components-running-on-the-cluster-nodes-that-are-being-updated"></a>CAU 是否需要正在更新的群集节点上运行的组件？  
CAU 不需要在群集节点上运行的服务。 但是，CAU 需要在群集节点上安装的 WMI 提供程序\) \(软件组件。 此组件是使用故障转移群集功能安装的。  
  
若要启用自助式\-更新模式，还必须将 CAU 群集角色添加到群集。  
  
## <a name="what-is-the-difference-between-using-cau-and-vmm"></a>使用 CAU 和 VMM 之间的区别是什么？  
  
-   System Center Virtual Machine Manager \(VMM\) 只侧重于更新 Hyper-v\-V 群集，而 CAU 可以更新任何类型的受支持的故障转移群集，包括 Hyper-v\-V 群集。  
  
-   VMM 需要额外的许可，而 CAU 已获得适用于所有 Windows Server。 CAU 功能、工具和 UI 是使用故障转移群集组件安装的。  
  
-   如果你已经拥有 System Center 许可证，则可以继续使用 VMM 更新\-Hyper-v 群集，因为它提供了集成的管理和软件更新体验。  
  
-   仅在运行 Windows Server 2016、Windows Server 2012 R2 和 Windows Server 2012 的群集上支持 CAU。 VMM 还支持运行 Windows Server 2008 R2 和 Windows Server 2008 的计算机上的 Hyper-v\-V 群集。  
  
## <a name="can-i-use-remote-updating-on-a-cluster-that-is-configured-for-self-updating"></a>能否在配置为自行\-更新的群集上使用远程\-更新？  
可以。 可以通过远程\-更新配置\-在\-需求上更新配置的故障转移群集，就像你可以在计算机上强制执行 Windows 更新扫描一样，即使 Windows 更新配置为自动安装更新也是如此。 但是，你需要确保更新运行没有已在进行中。  
  
## <a name="can-i-reuse-my-cluster-update-settings-across-clusters"></a>我能不能在群集间重复使用群集更新设置。  
可以。 CAU 支持很多可以确定更新运行在其更新群集时的行为情况的更新运行选项。 这些选项可被另存为“更新运行配置文件”，并且可以在任何群集间重复使用。 我们建议你保存并在拥有相似更新需求的故障转移群集之间重复使用你的设置。 例如，你可以为支持业务\-关键服务的所有 Microsoft SQL Server 群集创建 "业务\-严重 SQL Server 群集更新运行配置文件"。  
  
## <a name="where-is-the-cau-plug-in-specification"></a>在规范中，CAU 插件\-在何处？  
  
-   [群集\-感知更新插件\-引用](https://msdn.microsoft.com/library/hh418084(VS.85).aspx)  
  
-   [群集感知更新\-插件示例](https://code.msdn.microsoft.com/windowsdesktop/Cluster-Aware-Updating-6a8854c9)  
  
## <a name="see-also"></a>另请参阅  
  
-   [群集感知更新概述\-  
  
