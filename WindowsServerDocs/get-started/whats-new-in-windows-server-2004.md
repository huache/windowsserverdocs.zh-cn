---
title: Windows Server 版本 2004 中的新增功能
description: Windows Server 版本 2004 中的新功能
ms.topic: article
author: Heidilohr
ms.author: helohr
ms.date: 05/27/2020
ms.localizationpriority: high
ms.openlocfilehash: 210aa06711c67af46d35a38fe4308bc4060691e8
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87957004"
---
# <a name="whats-new-in-windows-server-version-2004"></a>Windows Server 版本 2004 中的新增功能

>适用于：Windows Server（半年频道）

若要了解 Windows 中的最新功能，请参阅 [Windows Server 中的新增功能](whats-new-in-windows-server.md)。 本主题将介绍 Windows Server 版本 2004 中的一些新功能。

## <a name="server-core-container-improvements"></a>Server Core 容器改进

我们减小了 Server Core 容器映像的总体大小，以提高下载速度和性能。 我们已包括了以下改进：

- 从 Server Core 容器映像中删除了大多数 NGEN 映像，以使映像大小更小。
- 基于 Server Core 容器映像构建的 .NET Framework 运行时映像现在已经针对 ASP.NET 应用和 Windows PowerShell 脚本性能进行了优化。
- .NET 团队还确保了每个 NGEN 映像只有一个副本，从而减小 .NET Framework 映像的大小。

为了帮助你更好地了解这些容器的大小，下表将容器的当前版本（截至 [2020 年 5 月为止的每月安全更新](https://support.microsoft.com/help/4561769/windows-server-containers-for-may-2020)，也称为“5B”更新）与以前的版本进行比较。

| 容器版本 | 下载大小 | 磁盘上的大小 |
|---|---|---|
| Windows Server 版本 1903 | 2.311 GB | 5.1 GB |
| Windows Server 版本 1909 | 2.257 GB | 4.97 GB |
| Windows Server 版本 2004 | 1.830 GB | 3.98 GB |

有关 Windows Server 版本 2004 更新的详细信息，请参阅[我们的博客文章](https://techcommunity.microsoft.com/t5/containers/windows-server-version-2004-now-available/ba-p/1419194)。 若要详细了解一般情况下的 Windows 容器更新，请参阅[更新 Windows Server 容器](/virtualization/windowscontainers/deploy-containers/update-containers/)。
