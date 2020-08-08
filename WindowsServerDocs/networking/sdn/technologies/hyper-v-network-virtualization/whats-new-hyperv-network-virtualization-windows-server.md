---
title: Windows Server 2016 中 Hyper-v 网络虚拟化的新增功能
description: 本主题提供有关 Windows Server 2016 中 Hyper-v 网络虚拟化的新增功能的信息
manager: grcusanz
ms.topic: article
ms.assetid: 0254275a-0a77-40a9-b68a-1029284c03fe
ms.author: anpaul
author: AnirbanPaul
ms.date: 03/19/2018
ms.openlocfilehash: aa53b13526172e37a46fbb3108278ad7aa859b64
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87952482"
---
# <a name="whats-new-in-hyper-v-network-virtualization-in-windows-server-2016"></a>Windows Server 2016 中 Hyper-v 网络虚拟化的新增功能

>适用于：Windows Server（半年频道）、Windows Server 2016

本主题介绍了 Windows Server 2016 中新增或更改的 Hyper-v 网络虚拟化 (HNV) 功能。

## <a name="updates-in-hnv"></a><a name="BKMK_IPAM2012R2"></a>HNV 中的更新
HNV 提供以下几个方面的增强支持：

|特性/功能|新功能或改进功能|描述|
|--------------------------|-------------------|---------------|
|[可编程 Hyper-v 交换机](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#SDN)|新建|HNV 策略通过 Microsoft 网络控制器进行编程。|
|[VXLAN 封装支持](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#VXLAN)|新建|HNV 现在支持 VXLAN 封装。|
|[软件负载均衡器 (SLB) 互操作性](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#SLB)|新建|HNV 完全与 Microsoft 软件负载平衡器集成。|
|[符合 IEEE 以太网标头](../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/../../../sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md#L2)|改进了|符合 IEEE 以太网标准|

### <a name="programmable-hyper-v-switch"></a><a name="SDN"></a>可编程 Hyper-v 交换机
HNV 是 Microsoft 的更新软件定义的网络 (SDN) 解决方案的基本构建基块，完全集成到 SDN 堆栈中。

Microsoft 的新网络控制器将 HNV 策略推送到每个主机上运行的主机代理，使用开放 vSwitch 数据库管理协议 (OVSDB) 作为 SouthBound 接口 (SBI) 。 主机代理使用[VTEP 架构](https://github.com/openvswitch/ovs/blob/master/vtep/vtep.ovsschema)的自定义来存储此策略，并将复杂流规则计划为 hyper-v 交换机中的高性能流引擎。

Hyper-v 交换机内的流引擎是 Microsoft Azure 中使用的相同引擎，已在 &trade; Microsoft Azure 公有云中的超大规模验证。 此外，整个 SDN 堆栈通过网络控制器，网络资源提供程序 (即将发布的详细信息) 与 Microsoft Azure 一致，因此，将 Microsoft Azure 公有云的功能带入我们的企业和托管服务提供商客户。

> [!NOTE]
> 有关 OVSDB 的详细信息，请参阅[RFC 7047](https://www.rfc-editor.org/info/rfc7047)。

Hyper-v 交换机支持无状态和有状态流规则，这些规则基于 Microsoft 的流引擎内的简单 "匹配操作"。

![Windows Server 2016 Hyper-v 交换机](../../../media/what-s-new-in-hyper-v-network-virtualization-in-windows-server/HNVOverview.png)

### <a name="vxlan-encapsulation-support"></a><a name="VXLAN"></a>VXLAN 封装支持
虚拟可扩展局域网 (VXLAN- [RFC 7348](https://www.rfc-editor.org/info/rfc7348)) 协议已在市场位置广泛采用，并支持来自 Cisco、织锦、DELL、HP 和其他供应商等供应商。 HNV 现在还支持通过 Microsoft 网络控制器使用 MAC 分发模式的此封装方案，以对租户覆盖网络 IP 地址 (客户地址或)  (提供程序地址或 PA) 的 CA 的映射进行编程。 支持通过第三方驱动程序提高性能，同时支持 NVGRE 和 VXLAN 任务卸载。

### <a name="software-load-balancer-slb-interoperability"></a><a name="SLB"></a>软件负载均衡器 (SLB) 互操作性
Windows Server 2016 包括软件负载平衡器 (SLB) ，完全支持虚拟网络流量，并与 HNV 无缝交互。 SLB 通过数据平面 v-交换机中的高性能流引擎来实现，并由虚拟 IP (VIP) /动态 IP (DIP) 映射的网络控制器控制。

### <a name="compliant-ieee-ethernet-headers"></a><a name="L2"></a>符合 IEEE 以太网标头
HNV 实现了正确的 L2 以太网标头，以确保与依赖于行业标准协议的第三方虚拟设备和物理设备进行互操作。 Microsoft 确保所有传输的数据包在所有字段中都具有符合的值，以确保此互操作性。 此外，在物理 L2 网络中支持巨型帧 (MTU > 1780) ，将需要 VXLAN 封装协议引入的数据包开销 (NVGRE，) ，同时确保连接到 HNV 虚拟网络的来宾虚拟机保持 1514 MTU。

## <a name="additional-references"></a>其他参考

-   [Hyper-V 网络虚拟化概述](hyperv-network-virtualization-overview-windows-server.md)

-   [Hyper-V 网络虚拟化技术细节](hyperv-network-virtualization-technical-details-windows-server.md)

-   [软件定义的网络](../../Software-Defined-Networking--SDN-.md)
