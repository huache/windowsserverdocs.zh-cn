---
title: 网络控制器高可用性
description: 你可以使用本主题来了解 Windows Server 2016 中的软件定义的网络 (SDN) 的网络控制器高可用性。
manager: grcusanz
ms.topic: get-started-article
ms.assetid: 334b090d-bec4-4e67-8307-13831dbdd1d8
ms.author: anpaul
author: AnirbanPaul
ms.openlocfilehash: 838ce8dfc11cb08b20349f121405991fcbe00270
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87991340"
---
# <a name="network-controller-high-availability"></a>网络控制器高可用性

>适用于：Windows Server（半年频道）、Windows Server 2016

可以使用本主题了解软件定义的网络 SDN 的网络控制器高可用性和可伸缩性配置 \( \) 。

在数据中心部署 SDN 时，可以使用网络控制器来集中部署、监视和管理多个网络元素，包括 RAS 网关、软件负载均衡器、用于租户通信的虚拟网络策略、数据中心防火墙策略、 \( SDN 策略的服务 QoS 质量 \) 、混合网络策略等。

由于网络控制器是 SDN 管理的基础，因此网络控制器部署非常重要，它可提供高可用性，并使你能够轻松地根据数据中心需求增加或减少网络控制器节点。

尽管可以将网络控制器部署为单一计算机群集，但为了实现高可用性和故障转移，你必须将网络控制器部署到最少三台计算机的多个计算机群集中。

>[!NOTE]
>你可以在服务器计算机或 \( \) 运行 Windows Server 2016 Datacenter edition 的虚拟机 vm 上部署网络控制器。 如果在 Vm 上部署网络控制器，则 Vm 必须在同时运行 Datacenter edition 的 Hyper-v 主机上运行。 网络控制器在 Windows Server 2016 Standard edition 上不可用。

## <a name="network-controller-as-a-service-fabric-application"></a>作为 Service Fabric 应用程序的网络控制器

为了实现高可用性和可伸缩性，网络控制器依赖于 Service Fabric。 Service Fabric 提供了一种分布式系统平台，用于构建可伸缩、可靠且易于管理的应用程序。

作为平台，Service Fabric 提供构建可伸缩分布式系统所需的功能。 它提供在多个操作系统实例上托管的服务、在实例之间同步状态信息、选拔领导、故障检测、负载均衡等。

>[!NOTE]
>有关 Azure 中的 Service Fabric 的信息，请参阅[azure Service Fabric 概述](/azure/service-fabric/service-fabric-overview)。

在多台计算机上部署网络控制器时，网络控制器作为 Service Fabric 群集上的单个 Service Fabric 应用程序运行。 可以通过连接一组操作系统实例来形成 Service Fabric 群集。

网络控制器应用程序由多个有状态 Service Fabric 服务组成。 每个服务负责网络功能，例如物理网络管理、虚拟网络管理、防火墙管理或网关管理。

每个 Service Fabric 服务都有一个主副本和两个辅助副本。 主服务副本处理请求，而两个辅助服务副本在主副本处于禁用或不可用的情况下提供高可用性。

下图描绘了包含五台计算机 Service Fabric 群集的网络控制器。 四个服务分布在五台计算机上：防火墙服务、网关服务、软件负载平衡 \( SLB \) 服务和虚拟网络 \( Vnet \) 服务。  四种服务中的每一项都包括一个主服务副本和两个辅助服务副本。

![网络控制器 Service Fabric 群集](../../../media/Network-Controller-HA/Network-Controller-HA.jpg)

## <a name="advantages-of-using-service-fabric"></a>使用 Service Fabric 的优点

下面是使用网络控制器群集的 Service Fabric 的主要优点。

### <a name="high-availability-and-scalability"></a>高可用性和可伸缩性

由于网络控制器是数据中心网络的核心，因此它必须能够灵活应对故障，并可灵活地适应在一段时间内进行数据中心网络的敏捷更改。 以下功能提供了这些功能：

- **快速故障转移**。 Service Fabric 提供了极快的故障转移。 多个热辅助服务副本始终可用。 如果由于硬件故障而导致操作系统实例变得不可用，则会立即将一个辅助副本升级为主副本。
- **规模的灵活性**。 你可以轻松快速地从几个实例扩展到多个实例，然后根据资源需求恢复到几个实例。

### <a name="persistent-storage"></a>永久性存储

网络控制器应用程序的配置和状态具有较大的存储要求。 应用程序还必须能够在计划内和计划外中断时使用。 为此，Service Fabric 提供了一个键-值存储 \( KVS， \) 这是一个复制的事务和持久存储。

### <a name="modularity"></a>模块化

网络控制器采用模块化体系结构进行设计，每个网络服务（例如虚拟网络服务和防火墙服务）都 \- 作为单个服务内置。

此应用程序体系结构具有以下优势。

1. 随着需求的发展，网络控制器模块化允许单独开发每个受支持的服务。 例如，可以更新软件负载平衡服务，而不会影响任何其他服务或网络控制器的正常运行。
2. 当网络发展时，网络控制器模块化允许添加新服务。 可以在不影响现有服务的情况下将新服务添加到网络控制器。

>[!NOTE]
>在 Windows Server 2016 中，不支持将第三方服务添加到网络控制器。

Service Fabric 模块使用服务模型架构来最大程度地提高应用程序的开发、部署和服务。

## <a name="network-controller-deployment-options"></a>网络控制器部署选项

若要使用 System Center Virtual Machine Manager vmm 部署网络 \( 控制器 \) ，请参阅[在 Vmm 构造中设置 SDN 网络控制器](/system-center/vmm/sdn-controller?view=sc-vmm-2019)。

若要使用脚本部署网络控制器，请参阅[使用脚本部署软件定义的网络基础结构](../../deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md)。

若要使用 Windows PowerShell 部署网络控制器，请参阅[使用 Windows Powershell 部署网络控制器](../../deploy/Deploy-Network-Controller-using-Windows-PowerShell.md)

有关网络控制器的详细信息，请参阅[网络控制器](Network-Controller.md)。