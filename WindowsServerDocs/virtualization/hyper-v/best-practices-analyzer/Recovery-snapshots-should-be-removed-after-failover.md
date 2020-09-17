---
title: 故障转移后，应删除恢复快照
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 922115fa-e8dd-4055-aaf1-4a4437c5cf28
ms.date: 8/16/2016
ms.openlocfilehash: b30dbf9996f2406e3d260c825dbe2dbbc6918324
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745542"
---
# <a name="recovery-snapshots-should-be-removed-after-failover"></a>故障转移后，应删除恢复快照

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Operations|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>**问题**
*故障转移虚拟机有一个或多个恢复快照。*

## <a name="impact"></a>**影响**
*可用空间可能会在存储快照文件的物理磁盘上运行。如果发生这种情况，则不能在物理存储上执行其他磁盘操作。依赖于物理存储的任何虚拟机都可能会受到影响。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>**解决方法**
*对于每个故障转移的虚拟机，请使用 Windows PowerShell 中的 Start-vmfailover cmdlet 来删除恢复快照并指示故障转移完成。*



