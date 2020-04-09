---
title: 添加文件夹目标
description: 本主题介绍如何添加文件夹目标（UNC 路径）
ms.prod: windows-server
ms.author: jgerend
manager: brianlic
ms.technology: storage
ms.topic: article
author: jasongerend
ms-date: 06/05/2017
ms.openlocfilehash: d2f3845a612556a51692aaf51d256bbedd518e7a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854100"
---
# <a name="add-folder-targets"></a>添加文件夹目标

> 适用于： Windows Server 2019，Windows Server （半年频道），Windows Server 2016，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2，Windows Server 2008

文件夹目标是共享文件夹或与命名空间中的某个文件夹关联的另一个命名空间的通用命名约定 (UNC) 路径。 添加多个文件夹目标可以提高命名空间中文件夹的可用性。

## <a name="to-add-a-folder-target"></a>添加文件夹目标的步骤

若要使用 DFS 管理添加文件夹目标，请按照以下过程操作：

1.  单击“开始”、指向“管理工具”，然后单击“DFS 管理”。

2.  在控制台树中的**命名空间**节点下，右键单击某文件夹，然后单击**添加文件夹目标**。

3.  键入该文件夹目标的路径，或者单击**浏览**以找到该文件夹目标。

4.  如果使用 DFS 复制对文件夹进行复制，则可指定是否向复制组添加新文件夹目标。

> [!TIP]
> 若要使用 Windows PowerShell 添加文件夹目标，请使用 [New-DfsnFolderTarget](https://docs.microsoft.com/powershell/module/dfsn/new-dfsnfoldertarget) cmdlet。 Windows Server 2012 中引入了 DFSN Windows PowerShell 模块。

> [!NOTE]
> 文件夹可以包含文件夹目标或其他 DFS 文件夹，但是不能在文件夹层次结构中的同一级别同时包含两者。

## <a name="see-also"></a>另请参阅

-   [部署 DFS 命名空间](deploying-dfs-namespaces.md)
-   [委派 DFS 命名空间的管理权限](delegate-management-permissions-for-dfs-namespaces.md)
-   [使用 DFS 复制复制文件夹目标](replicate-folder-targets-using-dfs-replication.md)