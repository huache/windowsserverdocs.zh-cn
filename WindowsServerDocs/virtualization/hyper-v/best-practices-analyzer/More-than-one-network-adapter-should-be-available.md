---
title: 应该提供多个网络适配器
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 59940e56-e06a-490f-90ea-cf30d9f80b09
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 56cb747ac44d48b115dbf105ea96e4623d458b28
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861890"
---
# <a name="more-than-one-network-adapter-should-be-available"></a>应该提供多个网络适配器

>适用于：Windows Server 2016

有关最佳实践和扫描的详细信息，请参阅 [最佳实践分析程序](https://go.microsoft.com/fwlink/?LinkId=122786)。  
  
|属性|详细信息|  
|-|-|  
|**操作系统**|Windows Server 2016|  
|**产品/功能**|Hyper-V|  
|**对应**|错误|  
|**类别**|配置|  

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题  
  
*此服务器配置有一个网络适配器，该网络适配器必须由管理操作系统和所有需要访问物理网络的虚拟机共享。*  
  
## <a name="impact"></a>影响  
  
*在管理操作系统中，网络性能可能会下降。*  
  
## <a name="resolution"></a>分辨率  
  
*将更多网络适配器添加到此计算机。若要保留一个网络适配器以供管理操作系统独占使用，请不要将它配置为用于外部虚拟网络。*  
  
有关将网络适配器添加到计算机的信息，请参阅计算机或网络适配器的文档。 然后，将其仅用于管理操作系统，不要将其连接到虚拟交换机。   
  


