---
title: 软件定义的网络 (SDN)
description: 软件定义的网络 (SDN) 提供了一种方法，可用于在数据中心内集中配置和管理物理和虚拟网络设备（如路由器、交换机和网关）。 使用本主题了解 Windows Server、System Center 和 Microsoft Azure 提供的软件定义的网络 (SDN) 技术。
manager: grcusanz
ms.topic: article
ms.assetid: 9a1ea73c-20cd-42c5-95ad-b003b9cc6d64
ms.author: anpaul
author: AnirbanPaul
ms.date: 08/09/2018
ms.openlocfilehash: ac42422a8827f3c31bc7a5dd8326865fb730e50e
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87966644"
---
# <a name="sdn-in-windows-server-overview"></a>在 Windows Server 概述 SDN

>适用于：Windows Server（半年频道）、Windows Server 2016


软件定义的网络 (SDN) 提供了一种方法，可用于在数据中心内集中配置和管理物理和虚拟网络设备（如路由器、交换机和网关）。 你可以使用现有的 SDN 兼容设备在虚拟网络与物理网络之间实现更深入的集成。 虚拟网络元素（如 Hyper-v 虚拟交换机、Hyper-v 网络虚拟化和 RAS 网关）旨在作为 SDN 基础结构的有机组成部分。

>[!Note]
>运行 SDN 基础结构服务器 (Vm) （如网络控制器和软件负载平衡节点）的 hyper-v 主机和虚拟机必须安装了 Windows Server 2016 Datacenter edition。
>
>仅包含连接到 SDN 控制的网络的租户工作负荷 Vm 的 hyper-v 主机可以使用 Windows Server 2016 Standard edition。

可以采用 SDN，因为网络平面不再绑定到网络设备本身。 但是，其他实体（如 System Center 2016 等数据中心管理软件）使用网络平面。 SDN 使你可以动态地管理数据中心网络，同时提供一种自动化的集中方式来满足应用程序和工作负载的要求。

可以使用 SDN 执行以下操作：

- 动态创建、保护和连接你的网络，以满足你的应用不断发展的需求
- 以无中断的方式提高工作负荷的部署速度
- 包含传播到网络中的安全漏洞
- 定义和控制管理物理和虚拟网络的策略
- 大规模按比例一致地实现网络策略

SDN 允许你完成所有这一切，同时降低总体基础结构成本。



## <a name="contact-the-datacenter-and-cloud-networking-product-team"></a>联系数据中心和云网络产品团队

如果对与 Microsoft 或其他 SDN 客户讨论 SDN 技术感兴趣，可以通过多种方法进行联系。

有关详细信息，请参阅[联系数据中心和云网络团队](contact-sdn-team.md)。
