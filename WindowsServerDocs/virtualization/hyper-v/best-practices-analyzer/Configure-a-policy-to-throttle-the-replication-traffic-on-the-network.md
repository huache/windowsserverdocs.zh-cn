---
title: 配置策略以限制网络上的复制流量
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 82cb1aef-cdc3-4d0a-88d4-ef497ab79606
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 5b3afd594f56973007a2f0f4318de8a8c7a98209
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365111"
---
# <a name="configure-a-policy-to-throttle-the-replication-traffic-on-the-network"></a>配置策略以限制网络上的复制流量

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。  
  
|属性|详细信息|  
|-|-|  
|**操作系统**|Windows Server 2016|  
|**产品/功能**|Hyper-V|  
|**Severity**|警告|  
|**类别**|配置|  
  
在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。  
  
## <a name="issue"></a>问题  
*可能不会限制允许复制使用的网络带宽量。*  
  
## <a name="impact"></a>影响  
*网络带宽可能会被复制流量完全占用，影响其他关键网络活动。这会影响以下端口：*  
  
虚拟机 \<列表 >  
  
## <a name="resolution"></a>分辨率  
*如果使用另一种方法来限制网络流量，则可以忽略此情况。否则，请使用组策略编辑器来配置策略，将网络流量限制为副本服务器的相关端口。*  
  
  


