---
title: 通过 Windows 管理中心部署超聚合基础结构
ms.topic: article
author: cosmosdarwin
ms.author: cosdar
ms.date: 11/04/2019
ms.openlocfilehash: 06062f4add54fda3ddcda4d092d6eaf1d692ebf8
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87993486"
---
# <a name="deploy-hyperconverged-infrastructure-with-windows-admin-center"></a>通过 Windows 管理中心部署超聚合基础结构

> 适用于：Windows Admin Center、Windows Admin Center 预览版

可以使用 Windows 管理中心[版本 1910](../overview.md)或更高版本，使用两个或更多适用的 Windows 服务器部署超聚合基础结构。 这项新功能采用多阶段工作流的形式，指导你完成以下操作：安装功能、配置网络、创建群集以及部署存储空间直通和/或软件定义的网络 (SDN) （如果已选中）。

从 Windows 管理中心版本2007，Windows 管理中心支持 Azure Stack HCI OS。 阅读有关[如何在 Windows 管理中心中的 AZURE STACK HCI 文档中部署群集](/azure-stack/hci/getting-started)的信息。Althought 本文档重点介绍 Azure Stack HCI，说明也适用于 Windows Server 部署。

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
> `Remove-VMSwitch`Cmdlet 会自动删除任何虚拟适配器，并撤消物理适配器的交换机嵌入组合。

如果修改了网络适配器属性，如名称、IPv4 地址和 VLAN ID：

> [!Warning]
> 这些 cmdlet 会删除网络适配器名称和 IP 地址。 请确保你具有以后连接所需的信息，如下面的脚本中排除的管理适配器。 此外，请确保知道服务器的连接方式，如 MAC 地址之类的物理属性，而不只是 Windows 中的适配器名称。

```PowerShell
Get-NetAdapter | Where Name -Ne "Management" | Rename-NetAdapter -NewName $(Get-Random)
Get-NetAdapter | Where Name -Ne "Management" | Get-NetIPAddress -ErrorAction SilentlyContinue | Where AddressFamily -Eq IPv4 | Remove-NetIPAddress
Get-NetAdapter | Where Name -Ne "Management" | Set-NetAdapter -VlanID 0
```

你现在已准备好开始工作流。

## <a name="additional-references"></a>其他参考

- [你好，Windows 管理中心](../overview.md)
- [部署存储空间直通](../../../storage/storage-spaces/deploy-storage-spaces-direct.md)