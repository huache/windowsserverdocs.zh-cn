---
ms.assetid: 62708b2e-4090-4cf7-8ae6-a557f31f561f
title: 了解 Active Directory 逻辑模型
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: c04e699fe2069b22aa1bd07ccb34e1e37a3ad9cb
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938287"
---
# <a name="understanding-the-active-directory-logical-model"></a>了解 Active Directory 逻辑模型

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

为 Active Directory 域服务 (AD DS) 设计逻辑结构涉及定义目录中的容器之间的关系。 这些关系可能基于管理需求，如颁发机构委托，或者可能由操作要求定义，例如需要控制复制。

在设计 Active Directory 逻辑结构之前，了解 Active Directory 逻辑模型非常重要。 AD DS 是一种分布式数据库，用于存储和管理有关网络资源的信息，以及从启用目录的应用程序中特定于应用程序的数据。 AD DS 允许管理员将网络 (（如用户、计算机和) 设备）的元素组织为分层包含结构。 顶层容器是林。 林中为域，在域中是组织单位 (Ou) 。 这称为逻辑模型，因为它独立于部署的物理方面，例如每个域和网络拓扑中所需的域控制器的数量。

## <a name="active-directory-forest"></a>Active Directory 林
林是一个或多个 Active Directory 域的集合，这些域共享公共逻辑结构、目录架构 (类和属性定义) 、目录配置 (站点和复制信息) 以及 (林范围内的全局编录) 搜索功能。 同一林中的域自动与双向可传递信任关系关联。

## <a name="active-directory-domain"></a>Active Directory 域
域是 Active Directory 林中的分区。 通过对数据进行分区，组织可以仅将数据复制到需要的位置。 通过这种方式，目录可通过带宽有限的网络进行全局缩放。 此外，域还支持与管理相关的许多其他核心功能，包括：

-   网络范围的用户标识。 域允许创建一次用户标识，并在加入域所在的林的任何计算机上引用用户标识。 构成域的域控制器用于存储用户帐户和用户凭据 (如安全) 密码或证书。

-   身份验证。 域控制器为用户提供身份验证服务，并提供额外的授权数据（如用户组成员身份），这些数据可用于控制对网络上资源的访问。

-   信任关系。 域可通过信任将身份验证服务扩展到其自身林以外的域中的用户。

-   复制。 域定义了一个目录分区，其中包含的数据足以提供域服务，然后在域控制器之间进行复制。 通过这种方式，所有域控制器都是域中的对等方，并作为一个单元进行管理。

## <a name="active-directory-organizational-units"></a>Active Directory 组织单位
Ou 可用于构成域中容器的层次结构。 Ou 用于出于管理目的对对象进行分组，如应用组策略或颁发机构委托。 通过 OU 和其内部的对象控制 () 由访问控制列表 (Acl) 在 OU 和 OU 中的对象上。 为了便于管理大量对象，AD DS 支持授权委派的概念。 通过委派，所有者可以将对象的完全或有限管理控制转移到其他用户或组。 委派非常重要，因为它有助于跨多个受信任的用户（这些用户可以执行管理任务）分发大量对象的管理。



