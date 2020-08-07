---
title: 从活动故障转移群集成员中删除节点
description: 本文解决了从活动故障转移群集成员身份中删除节点的问题。
ms.date: 05/28/2020
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: da46b39f853476676a06bcaaa20338dd1a178586
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935567"
---
# <a name="nodes-being-removed-from-failover-cluster-membership-on-vmware-esx"></a>正在从 VMWare ESX 上的故障转移群集成员身份中删除的节点

本文解决了在 VMWare ESX 上托管节点时查找从活动故障转移群集成员身份中删除的节点的问题。

## <a name="symptom"></a>症状

出现此问题时，你将在事件查看器的系统事件日志中看到：

![事件1135](media/nodes-failover-cluster-vmware/1135.png)

## <a name="resolution"></a>解决方法

由于入站缓冲区设置得太低，无法处理大量流量，因此 VMXNET3 适配器会丢弃入站网络数据包。 我们可以通过使用性能监视器查看 "网络 Interface\Packets 收到的丢弃" 计数器来轻松找出这一问题。

![添加计数器](media/nodes-failover-cluster-vmware/0527.png)

添加此计数器后，查看平均值、最小值和最大值，如果它们是大于零的任何值，则需要为适配器调整接收缓冲区。 VMWare 知识库中介绍了此问题：在[ESXi 1.x/vNIC 中的 VMXNET3 上的来宾操作系统级别大数据包丢失](https://kb.vmware.com/s/article/2039495)。
