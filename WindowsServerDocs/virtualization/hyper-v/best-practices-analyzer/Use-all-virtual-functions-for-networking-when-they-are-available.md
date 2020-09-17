---
title: 在可用时使用所有虚拟函数进行网络连接
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: bf895484-6a0d-4aa4-9a42-9fac739e875d
ms.date: 8/16/2016
ms.openlocfilehash: 4a1502180350c338793bf811cddc675785e9c67a
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746802"
---
# <a name="use-all-virtual-functions-for-networking-when-they-are-available"></a>在可用时使用所有虚拟函数进行网络连接

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*某些硬件加速功能没有被使用*

## <a name="impact"></a>影响
*此配置可能会导致总体 CPU 利用率高于所需的使用率。在以下虚拟机上，网络性能可能不是最佳的：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*如果物理硬件支持 SR-IOV 并且此配置不与虚拟机所需的网络功能发生冲突，请考虑为 SR-IOV 配置虚拟网络适配器。*



