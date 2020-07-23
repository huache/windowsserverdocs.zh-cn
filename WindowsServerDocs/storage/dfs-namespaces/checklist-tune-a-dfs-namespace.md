---
title: 清单：调整 DFS 命名空间
description: 本文介绍如何优化 DFS 命名空间处理引用和轮询 AD DS 以获得更新的命名空间数据的方式
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 67e272657c23926adbbf9f0db5174d00f4852137
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961749"
---
# <a name="checklist-tune-a-dfs-namespace"></a>清单：调整 DFS 命名空间

> 适用于： Windows Server 2019，Windows Server （半年频道），Windows Server 2016，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2，Windows Server 2008

创建命名空间并添加文件夹和目标之后，请使用以下清单来优化或优化 DFS 命名空间处理 Active Directory 域服务（AD DS）更新的命名空间数据的引用和轮询的方式。

-   阻止用户查看命名空间中他们无权访问的文件夹。 [在命名空间上启用基于访问权限的枚举](enable-access-based-enumeration-on-a-namespace.md)
-   允许或阻止用户在访问命名空间中的文件夹时被引用到该命名空间或文件夹目标。 [启用或禁用引用和客户端故障回复](enable-or-disable-referrals-and-client-failback.md)
-   调整在请求新引用之前客户端缓存引用的时间。 [更改客户端缓存引用的时间](change-the-amount-of-time-that-clients-cache-referrals.md)
-   优化命名空间服务器轮询 AD DS 以获取最新的命名空间数据的方式。 [优化命名空间轮询](optimize-namespace-polling.md)
-   使用继承的权限控制哪些用户可以查看命名空间中对其启用基于访问的枚举的文件夹。 [对基于访问权限的枚举使用继承权限](using-inherited-permissions-with-access-based-enumeration.md)

此外，使用称为目标优先级的 DFS 命名空间增强功能，可以指定服务器的优先级，以便使特定服务器始终作为客户端访问命名空间中包含目标的文件夹时接收的服务器列表（称为引用）中的第一项或最后一项。

-   指定应将用户引用到文件夹目标的顺序。 [为引用中的目标设置排序方法](set-the-ordering-method-for-targets-in-referrals.md)
-   替代特定命名空间服务器或文件夹目标的引用排序。 [设置目标优先级以替代引用排序](set-target-priority-to-override-referral-ordering.md)

## <a name="additional-references"></a>其他参考

-   [命名空间](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771914(v=ws.11))
-   [清单：部署 DFS 命名空间](checklist-deploy-dfs-namespaces.md)
-   [调整 DFS 命名空间](tuning-dfs-namespaces.md)
