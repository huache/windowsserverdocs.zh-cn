---
ms.assetid: f0d4cecc-5a03-448c-bef9-86c4730b4eb0
title: 虚拟机负载均衡概述
ms.topic: article
author: bhattacharyaz
manager: eldenc
ms.author: subhatt
ms.date: 09/19/2016
ms.openlocfilehash: 60d6c1b10840b5e0f673099c71b72033178aeb2d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87957124"
---
# <a name="virtual-machine-load-balancing-overview"></a>虚拟机负载均衡概述

> 适用于：Windows Server 2019、Windows Server 2016

私有云部署的重要注意事项是资本支出 (<abbr title="资本支出">CapEx</abbr>需要 ) 才能投入生产。 将冗余添加到私有云部署，以避免在生产高峰时段内容量不足，但这会增加 <abbr title="资本支出">CapEx</abbr>. 冗余需求由不平衡的私有云驱动，其中某些节点承载更多虚拟机 (<abbr title="虚拟机">VM</abbr>) 和其他 (使用不足，如) 全新重新启动的服务器。

<strong>快速视频概述</strong><br> (6 分钟) <br>
> [!VIDEO https://channel9.msdn.com/Blogs/windowsserver/Virtual-Machine-Load-Balancing-in-Windows-Server-2016/player]

## <a name="what-is-virtual-machine-load-balancing"></a><a id="what-is-vm-load-balancing"></a>什么是虚拟机负载平衡？
<abbr title="虚拟机">VM</abbr> 负载均衡是 Windows Server 2019 和 Windows Server 2016 中的内置功能，可用于优化故障转移群集中节点的使用。 它标识过度提交的节点并重新分发 <abbr title="虚拟机">VM</abbr> 从这些节点到已提交的节点。 此功能的一些突出特性如下：

* *这是一种零停机解决方案*： <abbr title="虚拟机">VM</abbr> 实时迁移到空闲节点。
* *与现有群集环境无缝集成*：故障策略，如消除相关性、容错域和可能的所有者。
* *用于平衡的试探法*： <abbr title="虚拟机">VM</abbr> 节点的内存压力和 CPU 使用率。
* *精细控制*：默认情况下启用。 可以按需或定期激活。
* *入侵阈值*：三个可用阈值，基于你的部署特征。

## <a name="the-feature-in-action"></a><a id="feature-in-action"></a>操作中的功能
### <a name="a-new-node-is-added-to-your-failover-cluster"></a><a id="new-node-added"></a>新节点将添加到故障转移群集
![要添加到故障转移群集中的新节点的图形](media/vm-load-balancing/overview-VM-load-balancing-1.png)

将新容量添加到故障转移群集时， <abbr title="虚拟机">VM</abbr> 负载平衡功能会按以下顺序自动将现有节点的容量平衡到新添加的节点：

1. 在故障转移群集中的现有节点上评估压力。
2. 标识超出阈值的所有节点。
3. 具有最高压力的节点确定确定均衡的优先级。
4. <abbr title="虚拟机">VM</abbr> 实时迁移的 (，没有停机时间) 从超出阈值的节点到故障转移群集中的新添加节点。

### <a name="recurring-load-balancing"></a><a id="recurring-load-balancing"></a>周期性负载平衡
![定期 VM 负载平衡的图形](media/vm-load-balancing/overview-VM-load-balancing-2.png)

配置为定期平衡时，对群集节点的压力评估每30分钟进行一次平衡。 或者，压力可以按需计算。 下面是这些步骤的流：

1. 在私有云中的所有节点上评估压力。
2. 标识了超出阈值和低于阈值的所有节点。
3. 具有最高压力的节点确定确定均衡的优先级。
4. <abbr title="虚拟机">VM</abbr> 实时迁移的 (，) 在 "最小阈值" 下超出 "阈值" 节点的节点。

## <a name="see-also"></a>另请参阅
* [虚拟机负载平衡深入探讨](vm-load-balancing-deep-dive.md)
* [故障转移群集](failover-clustering-overview.md)
* [Hyper-v 概述](../virtualization/hyper-v/Hyper-V-on-Windows-Server.md)
