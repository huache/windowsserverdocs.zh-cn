---
title: NIC 组合疑难解答
description: 本主题提供有关 Windows Server 2016 中 NIC 组合疑难解答的信息。
manager: dougkim
ms.topic: article
ms.assetid: fdee02ec-3a7e-473e-9784-2889dc1b6dbb
ms.author: lizross
author: eross-msft
ms.date: 09/13/2018
ms.openlocfilehash: 33e287cdc13fdfe115fe1f42c9009d18bda8277a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87952185"
---
# <a name="troubleshooting-nic-teaming"></a>NIC 组合疑难解答

>适用于：Windows Server（半年频道）、Windows Server 2016

在本主题中，我们将讨论对 NIC 组合（如硬件和物理交换机证券）进行故障排除的方法。  当标准协议的硬件实现不符合规范时，可能会影响 NIC 组合性能。 另外，根据配置，NIC 组合可能会发送来自同一 IP 地址的数据包，其中包含多个 MAC 地址，以便在物理交换机上打开安全功能。


## <a name="hardware-that-doesnt-conform-to-specification"></a>不符合规范的硬件

在正常操作过程中，NIC 组合可能会从相同的 IP 地址发送数据包，但会发送多个 MAC 地址。 根据协议标准，这些数据包的接收方必须将主机或 VM 的 IP 地址解析为特定的 MAC 地址，而不是从接收数据包响应 MAC 地址。  正确实现地址解析协议 (ARP 和 NDP 的客户端) 发送具有正确目标 MAC 地址的数据包，即拥有该 IP 地址的 VM 或主机的 MAC 地址。

某些嵌入的硬件无法正确实现地址解析协议，也不能使用 ARP 或 NDP 将 IP 地址显式解析为 MAC 地址。  例如，SAN) 控制器 (的存储区域网络可能以这种方式执行。 不符合的设备从收到的数据包复制源 MAC 地址，然后在相应的传出数据包中将其用作目标 MAC 地址，导致数据包发送到错误的目标 MAC 地址。 因此，Hyper-v 虚拟交换机会丢弃数据包，因为它们与任何已知的目标都不匹配。

如果在连接到 SAN 控制器或其他嵌入的硬件时遇到问题，则应该获取数据包捕获，确定硬件是否正确实现 ARP 或 NDP，并与硬件供应商联系以获得支持。


## <a name="physical-switch-security-features"></a>物理交换机安全功能
根据配置，NIC 组合可能会从具有多个源 MAC 地址（在物理交换机上占用安全功能）的相同 IP 地址发送数据包。 例如，动态 ARP 检查或 IP 源防护，尤其是在物理交换机不知道这些端口是团队的一部分时，这种情况是在以交换机为独立模式配置 NIC 组合时发生的。 检查交换机日志以确定交换机安全功能是否会导致连接问题。

## <a name="disabling-and-enabling-network-adapters-by-using-windows-powershell"></a>使用 Windows PowerShell 禁用和启用网络适配器

NIC 团队失败的一个常见原因是：团队界面被禁用，在许多情况下，当运行一系列命令时，会出现意外情况。  这一特定的命令序列不会启用所有禁用的 NetAdapters，因为禁用 Nic 的所有底层物理成员将删除 NIC 组接口。

在这种情况下，NIC 组接口不再显示在 Get-netadapter 中，因此， **enable-get-netadapter \\ *** 不会启用 NIC 组。 但**get-netadapter \\ *** 命令会启用成员 nic，然后在短时间) 重新创建团队界面后 (。 在重新启用之前，团队界面仍处于 "已禁用" 状态，从而允许网络流量开始流动。

以下 Windows PowerShell 命令序列可能会意外禁用团队界面：

```PowerShell
Disable-NetAdapter *
Enable-NetAdapter *
```



## <a name="related-topics"></a>相关主题
- [NIC 组合](NIC-Teaming.md)：在本主题中，我们概括介绍了 Windows Server 2016 中的网络接口卡 (NIC) 组合。 NIC 组合允许在一个或多个基于软件的虚拟网络适配器之间分组到32物理以太网网络适配器。 这些虚拟网络适配器可以提高性能，并在网络适配器发生故障时提供容错能力。

- [NIC 组合 MAC 地址使用和管理](NIC-Teaming-MAC-Address-Use-and-Management.md)：在使用 "交换机独立" 模式配置 nic 组，并使用 "地址哈希" 或 "动态负载分配" 时，团队将使用 media access CONTROL (MAC) 地址的主 NIC 组成员的出站流量。 主 NIC 组成员是操作系统从一组初始团队成员中选择的网络适配器。

- [Nic 组合设置](nic-teaming-settings.md)：在本主题中，我们将为你概述 NIC 组属性，例如组合和负载平衡模式。 此外，我们还会向你介绍备用适配器设置和主团队接口属性的详细信息。 如果 NIC 组中至少有两个网络适配器，则无需指定备用适配器来实现容错。



