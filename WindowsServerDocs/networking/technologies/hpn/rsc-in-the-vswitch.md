---
title: 在 vSwitch 中接收段合并 (RSC)
description: 在 vSwitch 中 (RSC) 的接收段合并是 Windows Server 2019 和 Windows 10 2018 10 月版更新中的一项功能，可帮助降低主机 CPU 利用率，并通过将多个 TCP 段合并为较少的段，提高虚拟工作负荷的吞吐量。 处理更少的情况下， (合并) 的大段比处理很多小型段更为有效。
manager: dougkim
ms.topic: article
ms.author: dacuo
author: dcuomo
ms.date: 09/07/2018
ms.openlocfilehash: 66f0f72dc6a577030ad43103e5f9d08a9458e64d
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87995093"
---
# <a name="rsc-in-the-vswitch"></a>VSwitch 中的 RSC
>适用于：Windows Server 2019

在 vSwitch 中 (RSC) 的接收段合并是 Windows Server 2019 和 Windows 10 2018 10 月版更新中的一项功能，可帮助降低主机 CPU 利用率，并通过将多个 TCP 段合并为较少的段，提高虚拟工作负荷的吞吐量。 处理更少的情况下， (合并) 的大段比处理很多小型段更为有效。

Windows Server 2012 和更高版本包括仅限硬件的卸载版本 (在该技术（也称为接收段合并）的物理网络适配器) 中实现。 此卸载版本的 RSC 仍可用于更高版本的 Windows。 但是，它与虚拟工作负载不兼容，一旦将物理网络适配器连接到 vSwitch，就会被禁用。 有关 RSC 的仅限硬件版本的详细信息，请参阅[接收段合并 (rsc) ](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh997024(v=ws.11))。

## <a name="scenarios-that-benefit-from-rsc-in-the-vswitch"></a>从 vSwitch 中的 RSC 受益的方案

其数据路径遍历虚拟交换机的工作负荷从此功能获益。

例如：

-   承载虚拟 Nic，包括：

    -   软件定义的网络

    -   Hyper-V 主机

    -   存储空间直通

-   Hyper-v 来宾虚拟 Nic

-   软件定义的网络 GRE 网关

-   容器

不兼容此功能的工作负荷包括：

-   软件定义的网络 IPSEC 网关

-   启用 SR-IOV 的虚拟 Nic

-   SMB 直通

## <a name="configure-rsc-in-the-vswitch"></a>在 vSwitch 中配置 RSC


默认情况下，在外部 Vswitch 上启用 RSC。

**查看当前设置：**

```PowerShell
Get-VMSwitch -Name vSwitchName | Select-Object *RSC*
```

**在 vSwitch 中启用或禁用 RSC**


>[!IMPORTANT]
>重要提示：可以在不影响现有连接的情况下，动态启用和禁用 vSwitch。


**在 vSwitch 中禁用 RSC**

```PowerShell
Set-VMSwitch -Name vSwitchName -EnableSoftwareRsc $false
```

**在 vSwitch 中重新启用 RSC**

```PowerShell
Set-VMSwitch -Name vSwitchName -EnableSoftwareRsc $True
```
有关详细信息，请参阅[集-VMSwitch](/powershell/module/hyper-v/set-vmswitch?view=win10-ps)。