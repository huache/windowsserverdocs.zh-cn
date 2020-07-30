---
title: 调整故障转移基线网络阈值
description: 本文介绍了用于调整故障转移群集网络阈值的解决方案。
ms.prod: windows-server
ms.technology: server-general
ms.date: 05/28/2020
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: 86a7023f6480e68f917cb8cdd9d0c69c417d3145
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409788"
---
# <a name="iaas-with-sql-alwayson---tuning-failover-cluster-network-thresholds"></a>使用 SQL AlwaysOn 的 IaaS - 调整故障转移群集网络阈值

本文介绍了用于调整故障转移群集网络阈值的解决方案。

## <a name="symptom"></a>症状

当在 IaaS 中运行 SQL Server AlwaysOn 的 Windows 故障转移群集节点时，建议将群集设置更改为更宽松的监视状态。 现成的群集设置具有限制性，并可能导致不必要的中断。 默认设置适用于高度优化的本地网络，并不考虑多租户环境（如 Windows Azure （IaaS））导致的延迟。

Windows Server 故障转移群集不断监视 Windows 群集中节点的网络连接和运行状况。  如果某个节点不可通过网络访问，则执行恢复操作进行恢复，并使应用程序和在线服务进入群集中的另一个节点上。 群集节点之间的通信延迟可能导致以下错误：

> 错误1135（系统事件日志）

从活动故障转移群集成员身份中删除了群集节点节点**1** 。 此节点上的群集服务可能已停止。 这也可能是由于节点与故障转移群集中的其他活动节点失去了通信。 运行验证配置向导检查您的网络配置。 如果此情况仍然存在，请检查与此节点上的网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

Cluster .log 示例：

```console
0000ab34.00004e64::2014/06/10-07:54:34.099 DBG   [NETFTAPI] Signaled NetftRemoteUnreachable event, local address 10.xx.x.xxx:3343 remote address 10.x.xx.xx:3343
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [IM] got event: Remote endpoint 10.xx.xx.xxx:~3343~ unreachable from 10.xx.x.xx:~3343~
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [IM] Marking Route from 10.xxx.xxx.xxxx:~3343~ to 10.xxx.xx.xxxx:~3343~ as down
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [NDP] Checking to see if all routes for route (virtual) local fexx::xxx:5dxx:xxxx:3xxx:~0~ to remote xxx::cxxx:xxxd:xxx:dxxx:~0~ are down
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [NDP] All routes for route (virtual) local fxxx::xxxx:5xxx:xxxx:3xxx:~0~ to remote fexx::xxxx:xxxx:xxxx:xxxx:~0~ are down
0000ab34.00007328::2014/06/10-07:54:34.099 INFO  [CORE] Node 8: executing node 12 failed handlers on a dedicated thread
0000ab34.00007328::2014/06/10-07:54:34.099 INFO  [NODE] Node 8: Cleaning up connections for n12.
0000ab34.00007328::2014/06/10-07:54:34.099 INFO  [Nodename] Clearing 0 unsent and 15 unacknowledged messages.
0000ab34.00007328::2014/06/10-07:54:34.099 INFO  [NODE] Node 8: n12 node object is closing its connections
0000ab34.00008b68::2014/06/10-07:54:34.099 INFO  [DCM] HandleNetftRemoteRouteChange
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [IM] Route history 1: Old: 05.936, Message: Response, Route sequence: 150415, Received sequence: 150415, Heartbeats counter/threshold: 5/5, Error: Success, NtStatus: 0 Timestamp: 2014/06/10-07:54:28.000, Ticks since last sending: 4
0000ab34.00007328::2014/06/10-07:54:34.099 INFO  [NODE] Node 8: closing n12 node object channels
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [IM] Route history 2: Old: 06.434, Message: Request, Route sequence: 150414, Received sequence: 150402, Heartbeats counter/threshold: 5/5, Error: Success, NtStatus: 0 Timestamp: 2014/06/10-07:54:27.665, Ticks since last sending: 36
0000ab34.0000a8ac::2014/06/10-07:54:34.099 INFO  [DCM] HandleRequest: dcm/netftRouteChange
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [IM] Route history 3: Old: 06.934, Message: Response, Route sequence: 150414, Received sequence: 150414, Heartbeats counter/threshold: 5/5, Error: Success, NtStatus: 0 Timestamp: 2014/06/10-07:54:27.165, Ticks since last sending: 4
0000ab34.00004b38::2014/06/10-07:54:34.099 INFO  [IM] Route history 4: Old: 07.434, Message: Request, Route sequence: 150413, Received sequence: 150401, Heartbeats counter/threshold: 5/5, Error: Success, NtStatus: 0 Timestamp: 2014/06/10-07:54:26.664, Ticks since last sending: 36
```

```console
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <realLocal>10.xxx.xx.xxx:~3343~</realLocal>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <realRemote>10.xxx.xx.xxx:~3343~</realRemote>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <virtualLocal>fexx::xxxx:xxxx:xxxx:xxxx:~0~</virtualLocal>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <virtualRemote>fexx::xxxx:xxxx:xxxx:xxxx:~0~</virtualRemote>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <Delay>1000</Delay>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <Threshold>5</Threshold>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <Priority>140481</Priority>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO    <Attributes>2147483649</Attributes>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO  </struct mscs::FaultTolerantRoute>
0000ab34.00007328::2014/06/10-07:54:34.100 INFO   removed
```

```console
0000ab34.0000a7c0::2014/06/10-07:54:38.433 ERR   [QUORUM] Node 8: Lost quorum (3 4 5 6 7 8)
0000ab34.0000a7c0::2014/06/10-07:54:38.433 ERR   [QUORUM] Node 8: goingAway: 0, core.IsServiceShutdown: 0
0000ab34.0000a7c0::2014/06/10-07:54:38.433 ERR   lost quorum (status = 5925)
```

## <a name="cause"></a>原因

有两个设置用于配置群集的连接运行状况。

**延迟**–定义在节点之间发送分类检测信号的频率。  延迟是发送下一个检测信号之前等待的秒数。  在同一群集中，同一子网中的节点与不同子网中的节点之间可能存在不同的延迟。

**阈值**–此值定义在群集采取恢复操作之前丢失的检测信号数。  阈值为多个检测信号。  在同一群集中，同一子网上的节点与不同子网中的节点之间可能存在不同的阈值。

默认情况下，Windows Server 2016 将**SameSubnetThreshold**设置为10，将**SameSubnetDelay**设置为1000毫秒。 例如，如果连接监视失败10秒，则达到故障转移阈值会导致无法访问从群集成员身份中删除的节点。 这会导致将资源移到群集上的另一个可用节点。 将报告群集错误，包括群集错误1135（以上）。

## <a name="resolution"></a>解决方法

在 IaaS 环境中，放宽群集网络配置设置。

### <a name="steps-to-verify-current-configuration"></a>验证当前配置的步骤

检查当前群集网络配置设置是否使用 "获取群集" 命令：

```powershell
C:\Windows\system32> get-cluster | fl *subnet*
```

每个支持 OS 的默认值、最小值、最大值和推荐值

| 说明 | (OS) | Min | Max | 默认 | 建议 |
|--|--|--|--|--|--|
| CrossSubnetThreshold | 2008 R2 | 3 | 20 | 5 | 20 |
| CrossSubnet 阈值 | 2012 | 3 | 120 | 5 | 20 |
| CrossSubnet 阈值 | 2012 R2 | 3 | 120 | 5 | 20 |
| CrossSubnet 阈值 | 2016 | 3 | 120 | 20 | 20 |
| SameSubnet 阈值 | 2008 R2 | 3 | 10 | 5 | 10 |
| SameSubnet 阈值 | 2012 | 3 | 120 | 5 | 10 |
| SameSubnet 阈值 | 2012 R2 | 3 | 120 | 5 | 10 |
| SameSubnetThreshold | 2016 | 3 | 120 | 10 | 10 |

阈值的值反映有关部署范围的当前建议，如以下文章中所述：

[优化 Windows Server 2012 R2 中的故障转移群集网络阈值](https://support.microsoft.com/en-us/help/3153887/fine-tuning-failover-cluster-network-thresholds-in-windows-server-2012)

**阈值**定义在群集采取恢复操作之前丢失的检测信号数。  阈值为多个检测信号。  在同一群集中，同一子网中的节点与不同子网中的节点之间可能存在不同的阈值。

## <a name="recommendations-for-changing-to-more-relaxed-settings-for-multi-tenant-environments-like-azure-iaas"></a>针对多租户环境（例如 Azure （IaaS））更改为更宽松设置的建议

> [!NOTE]
> 通过调整群集网络配置设置，提高群集环境的复原能力会导致停机时间增加。 有关详细信息，请参阅[优化故障转移群集网络阈值](https://techcommunity.microsoft.com/t5/failover-clustering/tuning-failover-cluster-network-thresholds/ba-p/371834)。

1. 修改为更宽松的设置：

    > [!NOTE]
    > 更改群集阈值将立即生效，无需重新启动群集或任何资源。

    对于 AlwaysOn 可用性组的同一子网和跨区域部署，建议使用以下设置。

    ```powershell
    C:\Windows\system32> (get-cluster).SameSubnetThreshold = 20
    ```

    ```powershell
    C:\Windows\system32> (get-cluster).CrossSubnetThreshold = 20
    ```

2. 验证更改：

    ```powershell
    C:\Windows\system32> get-cluster | fl *subnet*
    ```

    :::image type="content" source="media/iaas-sql-failover-cluster/cmd.png" alt-text="cmd" border="false":::

## <a name="references"></a>参考

有关优化 Windows 群集网络配置设置的详细信息，请参阅[优化故障转移群集网络阈值](https://techcommunity.microsoft.com/t5/failover-clustering/tuning-failover-cluster-network-thresholds/ba-p/371834)。

有关使用 cluster.exe 优化 Windows 群集网络配置设置的信息，请参阅[如何为故障转移群集配置群集网络](/previous-versions/office/exchange-server-2007/bb690953(v=exchg.80)?redirectedfrom=MSDN)。
