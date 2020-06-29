---
title: 群集的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 8ee2e85723cc2449e8cb9c42ccb7d6b761482e3a
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474864"
---
# <a name="performance-history-for-clusters"></a>群集的性能历史记录

> 适用于：Windows Server 2019

此子主题存储空间直通的[性能历史记录](performance-history.md)介绍了为群集收集的性能历史记录。

没有源自群集级别的序列。 相反， `clusternode.cpu.usage` 将对群集中的所有服务器聚合服务器系列，例如。 `volume.iops.total`对于群集中的所有卷，将聚合卷系列，例如。 为群集中的所有驱动器聚合和驱动器序列（如 `physicaldisk.size.total` ）。

## <a name="usage-in-powershell"></a>PowerShell 中的用法

使用[Cluster](https://docs.microsoft.com/powershell/module/failoverclusters/get-cluster) cmdlet：

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="additional-references"></a>其他参考

- [存储空间直通的性能历史记录](performance-history.md)
