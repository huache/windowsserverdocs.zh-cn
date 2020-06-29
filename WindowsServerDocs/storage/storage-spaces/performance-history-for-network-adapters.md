---
title: 网络适配器的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 597abd8e389421eb6875ff3cc94b457f341be3b7
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474744"
---
# <a name="performance-history-for-network-adapters"></a>网络适配器的性能历史记录

> 适用于：Windows Server 2019

本主题中的[存储空间直通性能历史记录](performance-history.md)详细说明了为网络适配器收集的性能历史记录。 网络适配器性能历史记录适用于群集中每个服务器上的每个物理网络适配器。 远程直接内存访问（RDMA）性能历史记录适用于启用了 RDMA 的每个物理网络适配器。

   > [!NOTE]
   > 无法为关闭的服务器中的网络适配器收集性能历史记录。 服务器重新启动时，收集将自动恢复。

## <a name="series-names-and-units"></a>序列名称和单位

为每个符合条件的网络适配器收集这些系列：

| 系列                               | 计价单位            |
|--------------------------------------|-----------------|
| `netadapter.bandwidth.inbound`       | 每秒位数 |
| `netadapter.bandwidth.outbound`      | 每秒位数 |
| `netadapter.bandwidth.total`         | 每秒位数 |
| `netadapter.bandwidth.rdma.inbound`  | 每秒位数 |
| `netadapter.bandwidth.rdma.outbound` | 每秒位数 |
| `netadapter.bandwidth.rdma.total`    | 每秒位数 |

   > [!NOTE]
   > 网络适配器性能历史记录以**比特**/秒为单位，而不是每秒字节数。 1 10 GbE 网络适配器每秒可发送和接收大约1000000000位 = 125000000 字节 = 1.25 GB/秒，其理论最大为每秒。

## <a name="how-to-interpret"></a>如何解释

| 系列                               | 如何解释                                                      |
|--------------------------------------|-----------------------------------------------------------------------|
| `netadapter.bandwidth.inbound`       | 网络适配器接收的数据速率。                         |
| `netadapter.bandwidth.outbound`      | 网络适配器发送的数据速率。                             |
| `netadapter.bandwidth.total`         | 网络适配器接收或发送的数据的总速率。           |
| `netadapter.bandwidth.rdma.inbound`  | 网络适配器通过 RDMA 接收的数据速率。               |
| `netadapter.bandwidth.rdma.outbound` | 网络适配器通过 RDMA 发送的数据速率。                   |
| `netadapter.bandwidth.rdma.total`    | 网络适配器通过 RDMA 接收或发送的数据的总速率。 |

## <a name="where-they-come-from"></a>它们来自何处

`bytes.*`从 `Network Adapter` 安装了网络适配器的服务器上的性能计数器集中收集序列，每个网络适配器一个实例。

| 系列                           | 源计数器           |
|----------------------------------|--------------------------|
| `netadapter.bandwidth.inbound`   | 8×`Bytes Received/sec` |
| `netadapter.bandwidth.outbound`  | 8×`Bytes Sent/sec`     |
| `netadapter.bandwidth.total`     | 8×`Bytes Total/sec`    |

`rdma.*`从 `RDMA Activity` 安装了网络适配器的服务器上的性能计数器集中收集序列，每个启用了 RDMA 的网络适配器都有一个实例。

| 系列                               | 源计数器           |
|--------------------------------------|--------------------------|
| `netadapter.bandwidth.rdma.inbound`  | 8×`Inbound bytes/sec`  |
| `netadapter.bandwidth.rdma.outbound` | 8×`Outbound bytes/sec` |
| `netadapter.bandwidth.rdma.total`    | 8 x*以上的总和*   |

   > [!NOTE]
   > 计数器在整个间隔内进行测量，而不是采样。 例如，如果网络适配器空闲了9秒，但在第10秒钟内传输200位，则在 `netadapter.bandwidth.total` 此10秒的时间间隔内平均将其记录为每秒20位。 这可确保其性能历史记录捕获所有活动，并使干扰稳定。

## <a name="usage-in-powershell"></a>PowerShell 中的用法

使用[get-netadapter](https://docs.microsoft.com/powershell/module/netadapter/get-netadapter) cmdlet：

```PowerShell
Get-NetAdapter <Name> | Get-ClusterPerf
```

## <a name="additional-references"></a>其他参考

- [存储空间直通的性能历史记录](performance-history.md)
