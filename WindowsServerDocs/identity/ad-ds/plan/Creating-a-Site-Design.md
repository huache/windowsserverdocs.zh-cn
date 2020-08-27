---
ms.assetid: 83f746e5-81db-4610-9977-1d5c57699f50
title: 创建站点设计
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: cad87edb2c29ea0fa445bc194598dc54996731d5
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941147"
---
# <a name="creating-a-site-design"></a>创建站点设计

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

创建站点设计涉及确定哪些位置将成为站点、创建站点对象、创建子网对象，以及将子网与站点相关联。

## <a name="deciding-which-locations-will-become-sites"></a>确定哪些位置将成为站点

确定要为其创建站点的位置，如下所示：

- 为你打算在其中放置域控制器的所有位置创建站点。 请参阅 "域控制器布局" ( # A0) 工作表中所述的信息，以确定包含域控制器的位置。
- 为这些位置创建站点，这些位置包括运行需要创建站点的应用程序的服务器。 某些应用程序（如分布式文件系统命名空间 (DFSN) ）使用站点对象将最近的服务器定位到客户端。

> [!NOTE]
> 如果你的组织有多个接近快速、可靠的连接的网络，则可以在一个 Active Directory 站点中包含这些网络的所有子网。 例如，如果不同子网中两台服务器之间的往返返回网络延迟为10毫秒或更少，则可以在同一 Active Directory 站点中包含两个子网。 如果两个位置之间的网络延迟大于10毫秒，则不应在单个 Active Directory 站点中包含子网。 即使延迟为10毫秒或更低，你也可以选择部署单独的站点（如果你想要将站点间的流量分段用于基于 Active Directory 的应用程序）。

- 如果某个位置不需要站点，请将该位置的子网添加到位置具有最大广域网络的站点中 (WAN) 速度和可用带宽。

将成为站点以及每个位置中的网络地址和子网掩码的文档位置。 要使工作表可以帮助你记录站点，请参阅 [Windows Server 2003 部署工具包的作业帮助](https://microsoft.com/download/details.aspx?id=9608)，下载 Job_Aids_Designing_and_Deploying_Directory_and_Security_Services.zip，并打开 "将子网与站点关联" ( # A1) 。

## <a name="creating-a-site-object-design"></a>创建站点对象设计

对于决定创建站点的每个位置，请计划在 Active Directory 域服务 (AD DS) 中创建站点对象。 将成为 "将子网与站点关联" 工作表中的站点的文档位置。

有关如何创建站点对象的详细信息，请参阅文章 [创建站点](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc772304(v=ws.11))。

## <a name="creating-a-subnet-object-design"></a>创建子网对象设计

对于与每个位置关联的每个 IP 子网和子网掩码，请计划在 AD DS 中创建子网对象，以表示站点内的所有 IP 地址。

创建 Active Directory 子网对象时，有关网络 IP 子网和子网掩码的信息会自动转换为网络前缀长度表示法格式 <IP address> / <prefix length> 。 例如，使用子网掩码 255.255.252.0 (IPv4) 地址172.16.4.0 的网络 IP 版本4将显示为 172.16.4.0/22。 除 IPv4 地址之外，Windows Server 2008 还支持 IP 版本 6 (IPv6) 子网前缀，例如3FFE： FFFF：0： C000：：/64。 有关每个位置中的 IP 子网的详细信息，请参阅 [收集网络信息](../../ad-ds/plan/Collecting-Network-Information.md) 和 [附录 A：位置和子网前缀](Appendix-A--Locations-and-Subnet-Prefixes.md) ( # A0) 工作表中的 "位置和子网"。

通过引用 "确定要成为站点的位置" 部分中的 "将子网与站点关联" ( # A0) 工作表将每个子网对象与站点对象关联，以确定要将哪个子网关联到哪个站点。 记录与 "将子网与站点关联" ( # A0) 工作表中的每个位置关联的 Active Directory 子网对象。

有关如何创建子网对象的详细信息，请参阅 [创建子网一](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc770372(v=ws.11))文。
