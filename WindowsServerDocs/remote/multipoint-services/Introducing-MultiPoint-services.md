---
title: 引入 MultiPoint Services
description: 概述 MultiPoint 服务，一种允许多个用户共享系统的方法
ms.date: 07/22/2016
ms.topic: article
ms.assetid: 1cbef744-4661-4ba9-9e2b-0bbd8854fd5c
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: c1f317909b05c421058041bcd2546c4cc0e704bb
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87970634"
---
# <a name="introducing-multipoint-services"></a>引入 MultiPoint Services
Windows Server 2016 中的 MultiPoint 服务角色允许多个用户，每个用户都有自己的独立且熟悉的 Windows 体验，同时共享一台计算机。用户可以通过多种方式访问其会话。 其中一种方法是通过在任何设备上使用[远程桌面应用](../remote-desktop-services/clients/remote-desktop-clients.md)远程访问服务器。 另一种方法是通过工作站连接到 MultiPoint 服务器：

-   直接到计算机上的视频端口

-   通过专用 USB 零客户端 (也称为多功能 USB 集线器) ，以及通过类似的 USB 以太网设备。

-   通过局域网 (LAN) 

本文档后面的[MultiPoint Services 工作站](MultiPoint-services-Stations.md)中更详细地介绍了上述每种方法。

本文档介绍在计划部署 MultiPoint 服务时要考虑的以下因素：

-   要与 MultiPoint 服务系统一起使用哪种类型的桌面：是否需要会话、虚拟机或 Windows 电脑？

-   [为 MultiPoint 服务系统选择硬件](Selecting-Hardware-for-Your-MultiPoint-services-System.md)：应做出哪些硬件决策？

-   [硬件要求和性能建议](Hardware-Requirements-and-Performance-Recommendations.md)： MultiPoint 服务需要什么硬件？

-   [MultiPoint Services 站点规划](MultiPoint-services-Site-Planning.md)：在哪里可以找到运行 MultiPoint 服务及其工作站的计算机，以及如何配置这些计算机？

-   [网络注意事项和用户帐户](Network-Considerations-and-User-Accounts.md)：向其中部署 MultiPoint Services 系统的网络环境可能会影响用户帐户的管理方式。 什么是网络环境？ 如何管理用户帐户？

-   将[文件存储在 MultiPoint Services](Storing-Files-with-MultiPoint-services.md)中：存储用户文件的位置以及如何访问这些文件？

-   [预部署清单](Predeployment-Checklist.md)