---
title: 若要参与复制，故障转移群集中的服务器必须配置 Hyper-v 副本代理
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 5ec88ce5-a8b2-4ece-9062-366523c8b17f
ms.date: 8/16/2016
ms.openlocfilehash: 7fdd6167561be4922540a0def1f91f70b519aa0f
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746122"
---
# <a name="to-participate-in-replication-servers-in-failover-clusters-must-have-a-hyper-v-replica-broker-configured"></a>若要参与复制，故障转移群集中的服务器必须配置 Hyper-v 副本代理

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*对于故障转移群集，Hyper-v 副本需要使用 Hyper-v 副本代理名称，而不是单独的服务器名称。*

## <a name="impact"></a>影响
*如果将虚拟机移动到其他故障转移群集节点，复制将无法继续。*

## <a name="resolution"></a>解决方法
*使用故障转移群集管理器配置 Hyper-v 副本代理。在 "Hyper-v 管理器" 中，确保复制配置使用 Hyper-v 副本代理名称作为服务器名称。*



