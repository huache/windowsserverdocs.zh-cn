---
ms.assetid: af76ddbe-83a2-4a62-9989-873e3bb1c772
title: 站点拓扑所有者角色
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 8da8960a88de676c6611751d10f73f327f051fba
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938327"
---
# <a name="site-topology-owner-role"></a>站点拓扑所有者角色

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

管理站点拓扑的管理员称为站点拓扑所有者。 站点拓扑所有者了解站点之间网络的条件，并有权更改 Active Directory 域服务 (AD DS) 中的设置，以实现对站点拓扑所做的更改。 更改站点拓扑会影响复制拓扑中的更改。 站点拓扑所有者的责任包括：

-   控制网络连接性更改时的站点拓扑更改。

-   获取并维护网络组中有关网络连接和路由器的信息。 站点拓扑所有者必须维护子网地址列表、子网掩码以及每个子网地址的位置。 站点拓扑所有者还必须了解有关网络速度和容量的任何问题，这些问题会影响站点拓扑以有效地设置站点链接成本。

-   如果域控制器的 IP 地址更改为其他站点中的不同子网，或者如果该子网本身分配到不同的站点，则移动表示站点之间域控制器的 Active Directory 服务器对象。 在任一情况下，站点拓扑所有者都必须手动将域控制器的 Active Directory server 对象移到新站点。



