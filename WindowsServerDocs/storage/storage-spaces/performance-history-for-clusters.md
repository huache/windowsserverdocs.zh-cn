---
title: 群集的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: e013295364ae2951ffe8a963fb61a85d7863f5b6
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962049"
---
# <a name="performance-history-for-clusters"></a>群集的性能历史记录

> 适用于：Windows Server 2019

此子主题存储空间直通的[性能历史记录](performance-history.md)介绍了为群集收集的性能历史记录。

没有源自群集级别的序列。 相反， `clusternode.cpu.usage` 将对群集中的所有服务器聚合服务器系列，例如。 `volume.iops.total`对于群集中的所有卷，将聚合卷系列，例如。 为群集中的所有驱动器聚合和驱动器序列（如 `physicaldisk.size.total` ）。

## <a name="usage-in-powershell"></a>PowerShell 中的用法

使用[Cluster](/powershell/module/failoverclusters/get-cluster) cmdlet：

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="additional-references"></a>其他参考

- [存储空间直通的性能历史记录](performance-history.md)
