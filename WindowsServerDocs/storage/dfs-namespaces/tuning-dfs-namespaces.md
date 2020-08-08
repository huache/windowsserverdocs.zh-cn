---
title: 调整 DFS 命名空间
description: 本文介绍如何调整或优化 DFS 命名空间。
ms.date: 6/5/2017
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 348a34e24cf7d22dc376df37607f21f1dceea74a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939393"
---
# <a name="tuning-dfs-namespaces"></a>调整 DFS 命名空间

> 适用于： Windows Server 2019，Windows Server (半年通道) ，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2，Windows Server 2008

创建命名空间并添加文件夹和目标之后，请参阅下列部分调试或优化 DFS 命名空间处理引用以及轮询 Active Directory 域服务 (AD DS) 获取更新的命名空间数据的方式：

-   [在命名空间上启用基于访问权限的枚举](enable-access-based-enumeration-on-a-namespace.md)
-   [启用或禁用引用和客户端故障回复](enable-or-disable-referrals-and-client-failback.md)
-   [更改客户端缓存引用的时间](change-the-amount-of-time-that-clients-cache-referrals.md)
-   [为引用中的目标设置排序方法](set-the-ordering-method-for-targets-in-referrals.md)
-   [设置目标优先级以替代引用排序](set-target-priority-to-override-referral-ordering.md)
-   [优化命名空间轮询](optimize-namespace-polling.md)
-   [对基于访问权限的枚举使用继承权限](using-inherited-permissions-with-access-based-enumeration.md)

> [!NOTE]
> 若要搜索文件夹或文件夹目标，请选择命名空间，单击**搜索**选项卡，并在文本框中键入搜索字符串，然后单击**搜索**。