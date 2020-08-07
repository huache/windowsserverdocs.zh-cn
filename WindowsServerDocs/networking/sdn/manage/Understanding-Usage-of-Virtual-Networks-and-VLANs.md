---
title: 了解虚拟网络和 Vlan 的使用情况
description: 本主题介绍 Hyper-v 网络虚拟化虚拟网络，以及这些网络与虚拟局域网 (Vlan) 的不同之处。 通过 Hyper-v 网络虚拟化，你可以创建覆盖虚拟网络（也称为虚拟网络）。
manager: grcusanz
ms.topic: article
ms.assetid: 84ac2458-3fcf-4c4f-acfe-6105443dd83f
ms.author: anpaul
author: AnirbanPaul
ms.date: 08/26/2018
ms.openlocfilehash: 1f1f1f56fbac8c7faa7628ac0adb0cbeef3a78d3
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87962209"
---
# <a name="understand-the-usage-of-virtual-networks-and-vlans"></a>了解虚拟网络和 Vlan 的使用情况

>适用于：Windows Server（半年频道）、Windows Server 2016

本主题介绍 Hyper-v 网络虚拟化虚拟网络，以及这些网络与虚拟局域网 (Vlan) 的不同之处。 通过 Hyper-v 网络虚拟化，你可以创建覆盖虚拟网络（也称为虚拟网络）。




Windows Server 2016 中的软件定义的网络 (SDN) 基于 Hyper-v 虚拟交换机内覆盖虚拟网络的编程策略。 可以通过 Hyper-v 网络虚拟化创建覆盖虚拟网络（也称为虚拟网络）。

部署 Hyper-v 网络虚拟化时，会通过将原始租户虚拟机的第2层以太网帧封装为覆盖或隧道标 (头来创建覆盖网络，例如，VXLAN 或 NVGRE) 以及是 (或物理) 网络中的第3层 IP 和第2层以太网标头。 覆盖虚拟网络由24位虚拟网络标识符 (VNI) 标识，以维护租户通信隔离并允许重叠的 IP 地址。 VNI 由虚拟子网 ID (VSID) 、逻辑交换机 ID 和隧道 ID 组成。

此外，为每个租户分配一个路由域 (类似于虚拟路由和转发-VRF) ，以便 VNI) 表示的多个虚拟子网前缀 (都可以直接相互路由。 不支持跨租户 (或跨路由域) 路由，而无需通过网关。

每个租户的封装流量在其上进行隧道传输的物理网络由名为提供程序逻辑网络的逻辑网络表示。 此提供程序逻辑网络包含一个或多个子网，每个子网由一个 IP 前缀和一个 VLAN 802.1 q 标记（可选）表示。

出于基础结构目的，你可以创建其他逻辑网络和子网来携带管理流量、存储流量、实时迁移流量等。

Microsoft SDN 不支持通过使用 Vlan 隔离租户网络。 租户隔离仅通过使用 Hyper-v 网络虚拟化覆盖虚拟网络和封装来完成。


