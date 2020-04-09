---
title: 群集的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7a5eec986d6e7d633f1917c599ab6fcd244c7008
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856200"
---
# <a name="performance-history-for-clusters"></a>群集的性能历史记录

> 适用于： Windows Server 2019

此子主题存储空间直通的[性能历史记录](performance-history.md)介绍了为群集收集的性能历史记录。

没有源自群集级别的序列。 相反，服务器系列（如 `clusternode.cpu.usage`）将聚合到群集中的所有服务器。 对于群集中的所有卷，将聚合卷系列，例如 `volume.iops.total`。 对于群集中的所有驱动器，将聚合和驱动器序列，如 `physicaldisk.size.total`。

## <a name="usage-in-powershell"></a>在 PowerShell 中的用法

使用[Cluster](https://docs.microsoft.com/powershell/module/failoverclusters/get-cluster) cmdlet：

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="see-also"></a>另请参阅

- [存储空间直通的性能历史记录](performance-history.md)
