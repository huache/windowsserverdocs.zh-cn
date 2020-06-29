---
title: 系统见解数据源
description: 在 System Insights 中编写新功能时，可以指定要在本地收集和分析的现有数据源或新数据源。 本主题介绍在注册新功能时可以选择的数据源。
ms.prod: windows-server
ms.technology: system-insights
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 7/31/2018
ms.openlocfilehash: 5dc44d9309c25ca1475e512a11d9868d7fa49e97
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85473664"
---
# <a name="system-insights-data-sources"></a>系统见解数据源

>适用于：Windows Server 2019

系统见解引入了可扩展的数据收集功能。 编写新功能时，可以指定要在本地收集和分析的现有数据源或新数据源。 本主题介绍在注册新功能时可以选择的数据源。

## <a name="data-sources"></a>数据源
编写新功能时，必须确定要为每个功能收集的特定数据源。 您指定的数据源将直接在您的计算机上收集并持久保存，您可以从三种类型的数据源中进行选择：

- **性能计数器**：
    - 指定计数器路径、名称和实例，系统见解将收集这些性能计数器报告的相关数据。

- **系统事件**：
    - 指定通道名称和事件 ID，系统见解会记录事件发生的次数。

- **已知系列**
    - 系统见解为一些定义完善的资源收集计算机上的一些基本信息。 这些系列用于默认功能，但也可用于任何自定义功能。 这些信息将收集以下信息：

        - **磁盘**：
            - *属性*： Guid
            - *数据*：大小
        - **卷**：
            - *属性*： UniqueId、驱动器号、FileSystemLabel、Size
            - *数据*：已用大小
        - **网络适配器**：
            - *属性*： InterfaceGuid、InterfaceDescription、速度
            - *数据*：接收的字节数/秒，发送的字节数/秒，字节总数/秒
        - **CPU**：
            - *属性*：-
            - *数据*：处理器时间百分比

    - 指定众所周知的系列，系统见解将返回该系列收集的数据。


## <a name="retention-timelines-and-collection-intervals"></a>保留时间线和收集间隔
上述数据源具有不同的保留时间线和收集间隔。 下表显示了每个数据源的收集时间和频率：

| 数据源 | 保留时间线 | 收集间隔 |
| --------------- | --------------- | ----------- |
| 性能计数器 | 3 个月 | 15 分钟 |
| 系统事件 | 3 个月 | 15 分钟 |
| 已知系列 | 1 年 | 1 小时 |


### <a name="aggregation-types"></a>聚合类型
由于每个序列仅记录每个收集间隔的一个数据点，因此每个序列都有一个关联它的聚合类型。 下表描述了数据源和相应的聚合类型：

>[!NOTE]
>对于性能计数器，可以从几种不同的聚合类型中进行选择。

| 数据源 | 聚合类型 |
| --------------- | --------------- |
| 性能计数器 | Sum、average、max、min |
| 系统事件 | 计数 |
| 磁盘熟知系列 | Last （收集间隔中的最新值） |
| 卷知名系列 | Last （收集间隔中的最新值） |
| CPU 熟知系列 | 平均值 |
| 网络知名系列 | 平均值 |

## <a name="data-footprint"></a>数据占用量

System Insights 将所有数据收集到本地 C 驱动器（C：）。 通常，系统见解数据占用适中。 它直接取决于每个功能指定的数据源的类型和数量，下表详细说明了每种数据类型的存储使用量：

| 数据源 | 最大需求量 |
| --------------- | --------------- |
| 性能计数器 | 240 KB |
| 系统事件 | 200 KB |
| 磁盘熟知系列 | 每个磁盘 200 KB |
| 卷知名系列 | 每卷 300 KB |
| CPU 熟知系列 | 100 KB |
| 网络知名系列 | 每个网络适配器 300 KB |

>[!NOTE]
>**对于默认预测功能，大多数独立计算机的最大需求量应小于 10 MB。**

## <a name="additional-references"></a>其他参考
若要了解有关系统见解的详细信息，请使用以下资源：

- [系统见解概述](overview.md)
- [了解功能](understanding-capabilities.md)
- [管理功能](managing-capabilities.md)
- [添加和开发功能](adding-and-developing-capabilities.md)
- [系统见解常见问题解答](faq.md)
