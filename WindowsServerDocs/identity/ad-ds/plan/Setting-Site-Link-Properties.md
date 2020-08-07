---
ms.assetid: de054ac2-a386-43ec-a537-c0de21549741
title: 设置站点链接属性
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: e576d28048a7ad1a5d2bc53d692ef9b02a6a7ebd
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87945587"
---
# <a name="setting-site-link-properties"></a>设置站点链接属性

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

根据连接对象的属性进行站点间复制。 当知识一致性检查器 (KCC) 创建连接对象时，它将从站点链接对象的属性派生复制计划。 每个站点链接对象均表示两个或多个站点之间的广域网) 连接 (。

设置站点链接对象属性包括以下步骤：

-   确定与该复制路径相关联的开销。 KCC 使用成本来确定复制相同目录分区的两个站点之间复制的开销最少的路由。

-   确定定义发生站点间复制的时间的计划。

-   确定复制时间间隔，该时间间隔定义允许复制的时间（按计划中的定义）。

## <a name="in-this-guide"></a>本指南包含的内容

-   [确定成本](../../ad-ds/plan/Determining-the-Cost.md)

-   [确定计划](../../ad-ds/plan/Determining-the-Schedule.md)

-   [确定间隔](../../ad-ds/plan/Determining-the-Interval.md)



