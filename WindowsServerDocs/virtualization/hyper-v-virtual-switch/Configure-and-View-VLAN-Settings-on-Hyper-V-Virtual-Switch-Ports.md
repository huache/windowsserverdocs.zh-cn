---
title: 配置和查看 HYPER-V 虚拟交换机端口上的 VLAN 设置
description: 你可以使用本主题来了解有关在 Windows Server 2016 中的 Hyper-v 虚拟交换机端口上配置和查看虚拟局域网 (VLAN) 设置的最佳实践。
manager: brianlic
ms.topic: article
ms.assetid: 69e0e28a-98ae-4ade-bd27-ce2ad7eb310f
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 85d622094ac81aea8a2d90e4ef6eb5d226d0b290
ms.sourcegitcommit: 50b295002d60f4183f452cc169f0768a347830ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2020
ms.locfileid: "91248580"
---
# <a name="configure-and-view-vlan-settings-on-hyper-v-virtual-switch-ports"></a>配置和查看 HYPER-V 虚拟交换机端口上的 VLAN 设置

>适用于：Windows Server（半年频道）、Windows Server 2016

你可以使用本主题来了解有关在 Hyper-v 虚拟交换机端口上配置和查看虚拟局域网 (VLAN) 设置的最佳实践。

如果要在 Hyper-v 虚拟交换机端口上配置 VLAN 设置，则可以使用 Windows &reg; Server 2016 Hyper-v 管理器或 System Center Virtual Machine Manager (VMM) "。

如果你使用的是 VMM，则 VMM 将使用以下 Windows PowerShell 命令来配置交换机端口。

```powershell
Set-VMNetworkAdapterIsolation <VM-name|-ManagementOS -IsolationMode VLAN -DefaultIsolationID <vlan-value> -AllowUntaggedTraffic $True
```
如果你未使用 VMM 并且在 Windows Server 中配置交换机端口，则可以使用 Hyper-v 管理器控制台或以下 Windows PowerShell 命令。
```powershell
Set-VMNetworkAdapterVlan <VM-name|-managementOS> -Access -VlanID <vlan-value>
```

由于这两种方法可以在 Hyper-v 虚拟交换机端口上配置 VLAN 设置，因此当你尝试查看交换机端口设置时，会出现以下情况：未配置 VLAN 设置-即使配置了这些设置。

## <a name="use-the-same-method-to-configure-and-view-switch-port-vlan-settings"></a>使用相同的方法配置和查看交换机端口 VLAN 设置

若要确保不会遇到这些问题，必须使用相同的方法来查看用于配置交换机端口 VLAN 设置的交换机端口 VLAN 设置。

若要配置和查看 VLAN 交换机端口设置，必须执行以下操作：

- 如果使用 VMM 或网络控制器来设置和管理网络，并且已将软件定义的网络 (SDN) 部署，则必须使用 **VMNetworkAdapterIsolation** cmdlet。
- 如果使用的是 Windows Server 2016 Hyper-v 管理器或 Windows PowerShell cmdlet，并且尚未将软件定义的网络 (SDN) 部署，则必须使用 **set-vmnetworkadaptervlan** cmdlet。

### <a name="possible-issues"></a>可能的问题

如果不遵循这些准则，你可能会遇到以下问题。

- 如果你已部署了 SDN 并使用 VMM、网络控制器或 **VMNetworkAdapterIsolation** cmdlet 来配置 Hyper-v 虚拟交换机端口上的 VLAN 设置：如果你使用 Hyper-v 管理器或 **获取 set-vmnetworkadaptervlan** 来查看配置设置，则命令输出不会显示你的 VLAN 设置。 相反，你必须使用 **VMNetworkIsolation** cmdlet 来查看 VLAN 设置。
- 如果你尚未部署 SDN，而是使用 Hyper-v 管理器或 **set-vmnetworkadaptervlan** cmdlet 来配置 Hyper-v 虚拟交换机端口上的 VLAN 设置：如果你使用 **VMNetworkIsolation** cmdlet 查看配置设置，则命令输出不会显示你的 VLAN 设置。 相反，你必须使用 **Get set-vmnetworkadaptervlan** cmdlet 来查看 VLAN 设置。

同时，不要尝试使用这两种配置方法来配置相同的交换机端口 VLAN 设置。 如果执行此操作，则不会错误地配置交换机端口，结果可能是网络通信失败。

### <a name="resources"></a>资源

有关本主题中所述的 Windows PowerShell 命令的详细信息，请参阅以下内容：

- [VmNetworkAdapterIsolation](/powershell/module/hyper-v/set-vmnetworkadapterisolation?view=win10-ps)
- [VmNetworkAdapterIsolation](/powershell/module/hyper-v/get-vmnetworkadapterisolation?view=win10-ps)
- [Set-vmnetworkadaptervlan](/powershell/module/hyper-v/set-vmnetworkadaptervlan?view=win10-ps)
- [Set-vmnetworkadaptervlan](/powershell/module/hyper-v/get-vmnetworkadaptervlan?view=win10-ps)
