---
ms.assetid: 28ecaf5c-9131-406c-b211-a230162e462e
title: 确定计划
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 1d30648523344d933025e779709815fc4e47f88a
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88939297"
---
# <a name="determining-the-schedule"></a>确定计划

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

可以通过设置站点链接的计划来控制站点链接的可用性。 当两个站点之间的复制遍历多个站点链接时，所有相关链接上的复制计划的交集将决定两个站点之间的连接计划。

若要规划设置站点链接计划，请在站点链接之间创建两个重叠的计划，这些站点链接包含彼此直接复制的域控制器。 使用这些链接上的默认 (100% 可用) 计划，除非你想要在高峰时段阻止复制流量。 通过阻止复制，可为其他流量指定优先级，但也会增加复制延迟。

域控制器在协调世界时 (UTC) 存储时间。 站点链接对象中的时间设置计划符合设置了计划的站点和计算机的本地时间。 当域控制器与位于不同站点和时区的计算机联系时，域控制器上的计划将根据计算机站点的本地时间显示时间设置。



