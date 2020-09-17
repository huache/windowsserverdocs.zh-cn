---
title: 使用中的逻辑处理器数不得超过支持的最大值
description: 提供有关如何解决此最佳做法分析器规则报告的问题的说明。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 66df8b02-91d1-424b-8934-a39c214d530e
ms.date: 8/16/2016
ms.openlocfilehash: 580d04af45416e08e536d815390be0e45b760312
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746142"
---
# <a name="the-number-of-logical-processors-in-use-must-not-exceed-the-supported-maximum"></a>使用中的逻辑处理器数不得超过支持的最大值

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|策略|

在以下部分中，斜体表示在此问题的最佳做法分析器工具中出现的文本。

## <a name="issue"></a>问题

*为服务器配置的逻辑处理器太多。*

## <a name="impact"></a>影响

*Microsoft 不支持在此计算机上运行 Hyper-v。*

## <a name="resolution"></a>解决方法

*从此计算机中删除一些处理器，或使用 msconfig 限制可用处理器的数量。*

请参阅以下说明以使用 Msconfig。 有关删除处理器的详细信息，请参阅计算机附带的说明或联系硬件制造商。 有关 Hyper-v 支持的最高配置的详细信息，请参阅 [在 Windows Server 2016 中规划 hyper-v 可伸缩性](../plan/plan-hyper-v-scalability-in-windows-server.md)。

### <a name="to-limit-the-number-of-available-processors"></a>限制可用处理器的数量

1.   ( # A0) 打开 "系统配置" 应用。 为此，请单击 " **开始**"，键入 **msconfig**，右键单击 " **系统配置** " 桌面应用程序，然后单击 "以 **管理员身份运行**"。

2.  从 " **启动** " 选项卡中，单击 " **高级选项**"。

3.  选择 " **处理器数量** "，然后在列表中选择一个编号。 单击“确定”。

4.  重新启动计算机以使用新数目的处理器运行它。