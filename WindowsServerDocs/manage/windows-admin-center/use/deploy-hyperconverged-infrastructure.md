---
title: 通过 Windows 管理中心部署超聚合基础结构
ms.topic: article
author: cosmosdarwin
ms.author: cosdar
ms.prod: windows-server
ms.technology: manage
ms.date: 11/04/2019
ms.openlocfilehash: 62bf21dd0afcb99aa77cff8a733e80fc4cffe2fb
ms.sourcegitcommit: 1da993bbb7d578a542e224dde07f93adfcd2f489
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73587227"
---
# <a name="deploy-hyperconverged-infrastructure-with-windows-admin-center"></a>通过 Windows 管理中心部署超聚合基础结构

> 适用于： Windows 管理中心、Windows 管理中心预览

可以使用 Windows 管理中心[版本 1910](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center)或更高版本，使用两个或更多适用的 Windows 服务器部署超聚合基础结构。 这项新功能采用了多阶段工作流的形式，指导你完成以下操作：安装功能、配置网络、创建群集以及部署存储空间直通和/或软件定义的网络（SDN）（如果已选中）。

![群集创建工作流的屏幕截图](../media/deploy-hyperconverged-infrastructure/deployment-workflow-screenshot.png)

  > [!Important]
  > 此功能处于积极开发阶段。 它在预览版中提供，因此你可以提前试用并共享你的反馈。

## <a name="preview-the-workflow"></a>预览工作流

### <a name="1-prerequisites"></a>1. 先决条件

Windows 管理中心中的群集创建工作流不会执行裸机操作系统安装，因此需要先在每台服务器上安装 Windows Server。 支持的版本为 Windows Server 2016、Windows Server 2019 和 Windows Server 有问必答 Preview。 还需要在启动工作流之前，将每台服务器加入到运行 Windows 管理中心的相同 Active Directory 域。

### <a name="2-install-windows-admin-center"></a>2. 安装 Windows 管理中心
 
按照说明[下载并安装](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center)最新版本的 Windows 管理中心。

### <a name="3-install-the-cluster-creation-extension"></a>3. 安装群集创建扩展

通过 Windows 管理中心扩展源传递和更新群集创建工作流。 这样我们就可以解决你的反馈，并在预览阶段更快速地做出改进。

若要安装该扩展，请启动 Windows 管理中心，然后执行以下操作：

1.  在右上方，选择 "设置" 图标
2.  导航到扩展
3.  查找群集创建扩展
4.  选择安装

![安装群集创建扩展的四个步骤的屏幕截图](../media/deploy-hyperconverged-infrastructure/how-to-install.png)

安装后，从左上角的下拉列表中选择群集创建扩展：

![启动群集创建扩展的屏幕截图](../media/deploy-hyperconverged-infrastructure/how-to-launch.png)

## <a name="limitations-of-the-preview-release"></a>预览版本的限制

群集创建工作流处于积极开发下，换言之，并未完成。

下面是当前预览版本的一些限制：

1.  **域要求。** 工作流当前要求你添加的每个服务器都必须已加入到运行 Windows 管理中心的同一个 Active Directory 域。
2.  **显示脚本。** 对于当前预览版本，使用 Windows 管理中心中的 "显示脚本" 功能无法查看工作流运行的脚本，也不能下载有关最终发生的所有内容的完整报表。 我们知道，这对于许多用户来说是很重要的-请保持优化。 同时，使用下面提供的 cmdlet 来[查看发生了什么情况](#see-whats-happening)。
3.  **恢复或重新开始。** 尽管可以通过工作流退出时发生，但当前预览版本不会处理从中断的位置继续，也不能在开始之前完全清除。 如果要在相同的服务器上重复部署以进行测试，请使用下面提供的 cmdlet 来[撤消和重新开始](#undo-and-start-over)。
4.  **远程直接内存访问（RDMA）。** 当前预览版本无法启用 RDMA 网络，该网络通常用于超聚合基础结构。 现在，请在不启用 RDMA 的情况下完成工作流，然后使用其他工具启用 RDMA，就像在其他情况下一样。

除了解决这些限制之外，在未来的版本中可能会增加无数个可能的功能：应用 Windows 更新，为群集仲裁配置见证服务器，导入虚拟机等。 若要帮助我们确定所需功能的优先级，请按如下所述[共享反馈](#feedback)。

## <a name="see-whats-happening"></a>查看正在进行的操作

使用这些 Windows PowerShell cmdlet 进行跟踪，并查看工作流正在执行的操作。

若要查看安装了哪些 Windows 功能，请使用 `Get-WindowsFeature` cmdlet。 例如：

```PowerShell
Get-WindowsFeature "Hyper-V", "Failover-Clustering", "Data-Center-Bridging", "BitLocker"
```

![PowerShell 输出的屏幕截图](../media/deploy-hyperconverged-infrastructure/script-out-1.png)

  > [!Note]
  > 安装哪些功能取决于所选群集的类型。

查看网络适配器及其属性，如名称、IPv4 地址和 VLAN ID：

```PowerShell
Get-NetAdapter | Where Status -Eq "Up" | Sort InterfaceAlias | Format-Table Name, InterfaceDescription, Status, LinkSpeed, VLANID, MacAddress
Get-NetAdapter | Where Status -Eq "Up" | Get-NetIPAddress -AddressFamily IPv4 -ErrorAction SilentlyContinue | Sort InterfaceAlias | Format-Table InterfaceAlias, IPAddress, PrefixLength
```

![PowerShell 输出的屏幕截图](../media/deploy-hyperconverged-infrastructure/script-out-2.png)

若要查看 Hyper-v 虚拟交换机，以及如何对物理网络适配器进行分组：

```PowerShell
Get-VMSwitch
Get-VMSwitchTeam
```

![PowerShell 输出的屏幕截图](../media/deploy-hyperconverged-infrastructure/script-out-3.png)

若要查看主机虚拟网络适配器（如果有），请运行：

```PowerShell
Get-VMNetworkAdapter -ManagementOS | Format-Table Name, IsManagementOS, SwitchName
Get-VMNetworkAdapterTeamMapping -ManagementOS | Format-Table NetAdapterName, ParentAdapter
```

![PowerShell 输出的屏幕截图](../media/deploy-hyperconverged-infrastructure/script-out-4.png)

若要查看当前故障转移群集及其成员节点，请运行：

```PowerShell
Get-Cluster
Get-ClusterNode
```

![PowerShell 输出的屏幕截图](../media/deploy-hyperconverged-infrastructure/script-out-5.png)

若要查看存储空间直通是否已启用，以及自动创建的默认存储池，请执行以下操作：

```PowerShell
Get-ClusterStorageSpacesDirect
Get-StoragePool -IsPrimordial $False
```

![PowerShell 输出的屏幕截图](../media/deploy-hyperconverged-infrastructure/script-out-6.png)

## <a name="undo-and-start-over"></a>撤消并重新开始

使用这些 Windows PowerShell cmdlet 撤消工作流所做的更改并重新开始。

### <a name="remove-virtual-machines-or-other-clustered-resources"></a>删除虚拟机或其他群集资源

如果你创建了任何虚拟机或其他群集资源（例如软件定义的网络的网络控制器），请先将它们删除。

例如，若要按名称删除资源，请使用：

```PowerShell
Get-ClusterResource -Name "<NAME>" | Remove-ClusterResource
```

### <a name="undo-the-storage-steps"></a>撤消存储步骤

如果启用了存储空间直通，请在此脚本中将其禁用：

> [!Warning]
> 这些 cmdlet 会永久删除存储空间直通卷中的所有数据。 这不能撤消。

```PowerShell
Get-VirtualDisk | Remove-VirtualDisk
Get-StoragePool -IsPrimordial $False | Remove-StoragePool
Disable-ClusterS2D
```

### <a name="undo-the-clustering-steps"></a>撤消群集步骤

如果已创建群集，请使用以下 cmdlet 将其删除：

```PowerShell
Remove-Cluster -CleanUpAD
```

若要同时删除群集验证报告，请在群集中的每个服务器上运行此 cmdlet：

```PowerShell
Get-ChildItem C:\Windows\cluster\Reports\ | Remove-Item
```

### <a name="undo-the-networking-steps"></a>撤消网络步骤

在属于群集的每个服务器上运行这些 cmdlet。

如果创建了 Hyper-v 虚拟交换机：

```PowerShell
Get-VMSwitch | Remove-VMSwitch
```

> [!Note]
> `Remove-VMSwitch` cmdlet 会自动删除任何虚拟适配器，并撤消物理适配器的交换机嵌入组合。

如果修改了网络适配器属性，如名称、IPv4 地址和 VLAN ID：

> [!Warning]
> 这些 cmdlet 会删除网络适配器名称和 IP 地址。 请确保你具有以后连接所需的信息，如下面的脚本中排除的管理适配器。 此外，请确保知道服务器的连接方式，如 MAC 地址之类的物理属性，而不只是 Windows 中的适配器名称。

```PowerShell
Get-NetAdapter | Where Name -Ne "Management" | Rename-NetAdapter -NewName $(Get-Random)
Get-NetAdapter | Where Name -Ne "Management" | Get-NetIPAddress -ErrorAction SilentlyContinue | Where AddressFamily -Eq IPv4 | Remove-NetIPAddress
Get-NetAdapter | Where Name -Ne "Management" | Set-NetAdapter -VlanID 0
```

你现在已准备好开始工作流。

## <a name="feedback"></a>反馈

此预览版本全部介绍你的反馈。 可以通过以下方式访问我们的团队：

- [在 UserVoice 上提交功能请求并为其投票](https://windowsserver.uservoice.com/forums/295071/category/319162?query=%5Bhci%5D)
- [加入 Microsoft 技术社区的 Windows 管理中心论坛](https://techcommunity.microsoft.com/t5/Windows-Server-Management/bd-p/WindowsServerManagement)
- 电子邮件 hci-部署 [at] microsoft.com
- 推文到[@servermgmt](https://twitter.com/servermgmt)

## <a name="report-an-issue"></a>报告问题

使用上面列出的通道报告群集创建工作流的问题。

如果可能，请提供以下信息，以帮助我们快速再现和解决你的问题：

- 所选群集的类型（示例： *"超聚合"* ）
- 遇到此问题的步骤（例如： *"3.2 Create cluster"* ）
- 群集创建扩展的版本。 请参阅 "**设置**" > **扩展** > **已安装的扩展**，并查看 "**版本**" 列（示例： *"1.0.30"* ）。
- 错误消息（无论是在屏幕上还是浏览器控制台中），都可以通过按**F12**打开。
- 有关环境的任何其他相关信息 

## <a name="see-also"></a>另请参阅

- [你好，Windows 管理中心](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center)
- [部署存储空间直通](https://docs.microsoft.com/windows-server/storage/storage-spaces/deploy-storage-spaces-direct)
