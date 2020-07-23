---
title: 使用 DFS 复制对文件夹目标进行复制
description: 本文介绍如何使用 DFS 复制对文件夹目标进行复制
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 399d9915cccc5d66c2b25b1e9f51c30e37d8dff6
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966439"
---
# <a name="replicate-folder-targets-using-dfs-replication"></a>使用 DFS 复制对文件夹目标进行复制

> 适用于： Windows Server 2019，Windows Server （半年频道），Windows Server 2016，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2 和 Windows Server 2008

你可以使用 DFS 复制使文件夹目标的内容保持同步，以便用户可以看到相同的文件，无论将客户端计算机引用到哪个文件夹目标，都是如此。

## <a name="to-replicate-folder-targets-using-dfs-replication"></a>使用 DFS 复制对文件夹目标进行复制

1.  单击“开始”****、指向“管理工具”****，然后单击“DFS 管理”****。

2.  在控制台树中的**命名空间**节点下，右键单击包含两个或多个文件夹目标的文件夹，然后单击**复制文件夹**。

3.  按照“复制文件夹向导”中的说明操作。

> [!NOTE]
> 配置更改不会立即应用到所有成员，除非使用 [Suspend-DfsReplicationGroup](/powershell/module/dfsr/suspend-dfsreplicationgroup?view=win10-ps) 和 [Sync-DfsReplicationGroup](/powershell/module/dfsr/sync-dfsreplicationgroup?view=win10-ps) cmdlet。 必须将新配置复制到所有域控制器中，且复制组中的每个成员必须轮询其最近的域控制器，以获取更改。 此过程所需的时间取决于 Active Directory 目录服务 (AD DS) 复制延迟，以及每个成员上的长轮询时间间隔（60 分钟）。 若要立即轮询以获得配置更改，请打开命令提示符窗口，然后为复制组中的每个成员键入一次以下命令： <br /> dfsrdiag.exe PollAD /Member:DOMAIN\Server1
<br />
若要从 Windows PowerShell 会话执行此操作，请使用 [Update-DfsrConfigurationFromAD](/powershell/module/dfsr/update-dfsrconfigurationfromad?view=win10-ps) cmdlet（在 Windows Server 2012 R2 中引入）。

## <a name="additional-references"></a>其他参考

-   [部署 DFS 命名空间](deploying-dfs-namespaces.md)
-   [委派 DFS 命名空间的管理权限](delegate-management-permissions-for-dfs-namespaces.md)
-   [DFS 复制](../dfs-replication/dfsr-overview.md)
