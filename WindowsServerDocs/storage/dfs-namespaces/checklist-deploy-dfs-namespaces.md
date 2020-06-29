---
title: 清单：部署 DFS 命名空间
description: 本文介绍如何配置和部署 DFS 命名空间。
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: adae586c67a34912ea34dca5749d8c69856033d0
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85473504"
---
# <a name="checklist-deploy-dfs-namespaces"></a>清单：部署 DFS 命名空间

> 适用于： Windows Server 2019，Windows Server （半年频道），Windows Server 2016，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2，Windows Server 2008

分布式文件系统 (DFS) 命名空间和 DFS 复制，可用于将文档、软件和业务线数据发布给整个组织的用户。 尽管只使用 DFS 复制就足以分发数据，但是可以使用 DFS 命名空间配置命名空间，以便文件夹由多台服务器承载，每台服务器存放该文件夹中的已更新副本。 这样，便可增加数据的可用性，并在服务器之间分发客户端负载。

浏览命名空间中的文件夹时，用户并不知道该文件夹由多个服务器托管。 在用户打开该文件夹时，系统会将客户端计算机自动引用到其站点上的服务器。 如果同一站点上的服务器不可用，你可以对命名空间进行配置，以将客户端引用到具有 Active Directory 目录服务 (AD DS) 中定义的最低连接成本的服务器。

若要部署 DFS 命名空间，请执行以下任务：

-   查看 DFS 命名空间的概念和要求。
[DFS 命名空间概述](dfs-overview.md)
-   [选择命名空间类型](choose-a-namespace-type.md)
-   [创建 DFS 命名空间](create-a-dfs-namespace.md)
-   将基于域的现有命名空间迁移到基于域的 Windows Server 2008 模式的命名空间。 [将基于域的命名空间迁移到 Windows Server 2008 模式](migrate-a-domain-based-namespace-to-windows-server-2008-mode.md)
-   通过将命名空间服务器添加到基于域的命名空间来增加可用性。 [将命名空间服务器添加到基于域的 DFS 命名空间](add-namespace-servers-to-a-domain-based-dfs-namespace.md)
-   将文件夹添加到命名空间。 [在 DFS 命名空间中创建文件夹](create-a-folder-in-a-dfs-namespace.md)
-   将文件夹目标添加到命名空间中的文件夹。 [添加文件夹目标](add-folder-targets.md)
-   通过使用 DFS 复制在文件夹目标之间复制内容（可选）。 [使用 DFS 复制复制文件夹目标](replicate-folder-targets-using-dfs-replication.md)


## <a name="additional-references"></a>其他参考

-   [命名空间](https://technet.microsoft.com/library/cc771914(v=ws.11).aspx)
-   [清单：优化 DFS 命名空间](checklist-tune-a-dfs-namespace.md)
-   [复制](https://technet.microsoft.com/library/cc770278(v=ws.11).aspx)


