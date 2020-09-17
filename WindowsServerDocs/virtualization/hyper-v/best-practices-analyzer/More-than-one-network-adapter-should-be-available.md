---
title: 应该提供多个网络适配器
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 59940e56-e06a-490f-90ea-cf30d9f80b09
ms.date: 8/16/2016
ms.openlocfilehash: 05dc0583424ed155c4780f9f0b4c016be850a71c
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746262"
---
# <a name="more-than-one-network-adapter-should-be-available"></a>应该提供多个网络适配器

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*此服务器配置有一个网络适配器，该网络适配器必须由管理操作系统和所有需要访问物理网络的虚拟机共享。*

## <a name="impact"></a>影响

*在管理操作系统中，网络性能可能会下降。*

## <a name="resolution"></a>解决方法

*将更多网络适配器添加到此计算机。若要保留一个网络适配器以供管理操作系统独占使用，请不要将它配置为用于外部虚拟网络。*

有关将网络适配器添加到计算机的信息，请参阅计算机或网络适配器的文档。 然后，将其仅用于管理操作系统，不要将其连接到虚拟交换机。



