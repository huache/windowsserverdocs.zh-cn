---
ms.assetid: a6343f1c-e9dd-4a02-91ad-39bd519d66cd
title: 简化的 SMB 多通道和多 NIC 群集网络
ms.topic: article
author: RobHindman
ms.author: robhind
ms.date: 09/15/2016
ms.openlocfilehash: 7fad43cb5f3de5c10ed815fa802b6168c15850d1
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87990748"
---
# <a name="simplified-smb-multichannel-and-multi-nic-cluster-networks"></a>简化的 SMB 多通道和多 NIC 群集网络

> 适用于：Windows Server 2019、Windows Server 2016

简化的 SMB 多通道和多<abbr title="网络接口卡">NIC</abbr> 群集网络是一项功能，可在同一群集网络子网上使用多个 Nic，并自动启用 SMB 多通道。

简化的 SMB 多通道和多 NIC 群集网络具有以下优势：
- 故障转移群集会自动识别使用同一交换机/相同子网的节点上的所有 Nic-无需其他配置。
- 自动启用 SMB 多通道。
- 仅群集链接本地 (fe80) IP 地址资源的网络在仅限群集的 (专用) 网络上被识别。
- 默认情况下，会在每个群集访问点 (CAP) 网络名称 (NN) 配置单个 IP 地址资源。
- 当在同一子网上找到多个 Nic 时，群集验证不再发出警告消息。

## <a name="requirements"></a>要求
-   每台服务器多个 Nic，使用同一个交换机/子网。

## <a name="how-to-take-advantage-of-multi-nic-clusters-networks-and-simplified-smb-multichannel"></a>如何利用多 NIC 群集网络和简化的 SMB 多通道
本部分介绍如何利用新的多 NIC 群集网络和简化的 SMB 多通道功能。

### <a name="use-at-least-two-networks-for-failover-clustering"></a>为故障转移群集使用至少两个网络
虽然很少见，但网络交换机可能会失败，但最好还是至少使用两个网络进行故障转移群集。 找到的所有网络都用于群集检测信号。 避免对故障转移群集使用单个网络，以避免单点故障。 理想情况下，群集中的节点之间应该有多个物理通信路径，并且无单点故障。

![用于故障转移群集的两个网络示意图 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig1.png)
 **图1：对故障转移群集使用至少两个网络**

### <a name="use-multiple-nics-across-clusters"></a>跨群集使用多个 Nic

在存储和存储工作负荷群集中使用多个 Nic 时，可实现简化的 SMB 多通道的最大优势。 这允许工作负荷群集 (Hyper-v、SQL Server 故障转移群集实例、存储副本 ) 等）使用 SMB 多通道，从而更有效地使用网络。 在聚合 (也称为非聚合) 群集配置，其中，横向扩展文件服务器群集用于存储 Hyper-v 或 SQL Server 故障转移群集实例群集的工作负荷数据，此网络通常称为 "北南部子网"/网络。 许多客户通过购买支持 RDMA 的 NIC 卡和交换机来最大限度地提高此网络的吞吐量。

![北南部 SMB 子网 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig2.png)
 **图2：若要实现最大网络吞吐量，请在横向扩展文件服务器群集和 hyper-v 或 SQL Server 故障转移群集实例群集上使用多个 nic，该群集共享北南部子网**

![截图在同一子网中使用多个 Nic 的两个群集利用 SMB 多通道 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig3.png)
 **图3：两个群集 (横向扩展文件服务器用于存储，SQL Server <abbr title=" 故障转移群集实例 "> FCI </abbr> 用于工作负荷) 两者都在同一子网中使用多个 Nic 来利用 SMB 多通道并获得更好的网络吞吐量。**

## <a name="automatic-recognition-of-ipv6-link-local-private-networks"></a>自动识别 IPv6 链接本地专用网络
仅当检测到专用 (群集) 具有多个 Nic 的网络时，群集将自动识别每个子网上每个 NIC 的 IPv6 链接本地 (fe80) IP 地址。 这会节省管理员时间，因为他们不再需要手动配置 IPv6 链接本地 (fe80) IP 地址资源。

如果仅) 网络使用多个专用 (群集，请检查 IPv6 路由配置以确保路由未配置为跨子网，因为这会降低网络性能。

![故障转移群集管理器 UI 中自动网络配置的截图 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig4.png)
 **图4：自动 IPv6 链接本地 (Fe80) 地址资源配置**

## <a name="throughput-and-fault-tolerance"></a>吞吐量和容错
Windows Server 2019 和 Windows Server 2016 会自动检测 NIC 功能，并将尝试在尽可能快的配置中使用每个 NIC。 使用 RSS 的 nic 和具有 RDMA 功能的 nic 都可以使用。 下表总结了使用这些技术时的利弊。 当使用多个支持 RDMA 的 Nic 时，实现最大吞吐量。 有关详细信息，请参阅[SMB Mutlichannel 的基础知识](/archive/blogs/josebda/the-basics-of-smb-multichannel-a-feature-of-windows-server-2012-and-smb-3-0)。

![各种 NIC 配置的吞吐量和容错的图示 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig5.png)
 **图5：各种 Nic 的吞吐量和容错 conifigurations**

## <a name="frequently-asked-questions"></a>常见问题
**多 NIC 网络中是否有用于信号的 Nic？**
是的。

**多 NIC 网络是否只能用于群集通信？还是只能将它用于客户端和群集通信？**
任何一个配置都将起作用-所有群集网络角色将在多 NIC 网络上运行。

**SMB 多通道还用于 CSV 和群集通信？**
是的，默认情况下，所有群集和 CSV 流量将使用可用的多 NIC 网络。 管理员可以使用故障转移群集 PowerShell cmdlet 或故障转移群集管理器 UI 来更改网络角色。

**如何查看 SMB 多通道设置？**
使用**SMBServerConfiguration** Cmdlet 查找 EnableMultiChannel 属性的值。

**群集公用属性是否在多 NIC 网络上 PlumbAllCrossSubnetRoutes？**
是的。

## <a name="additional-references"></a>其他参考
- [Windows Server 中的故障转移群集的新增功能](whats-new-in-failover-clustering.md)