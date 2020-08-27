---
ms.assetid: 692bd2af-deee-44cf-9af9-f364677e267f
title: 规划域控制器放置
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 9c96537650f5c49aa25a75211e28430b6bcf5f34
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941037"
---
# <a name="planning-domain-controller-placement"></a>规划域控制器放置

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

收集了将用于设计站点拓扑的所有网络信息后，请规划要在何处放置域控制器，包括林根域控制器、区域域控制器、操作主机角色持有者和全局编录服务器。

在 Windows Server 2008 中，还可以利用只读域控制器 (Rodc) 。 RODC 是一种新型的域控制器，承载 Active Directory 数据库的只读分区。 除帐户密码之外，RODC 保存了可写域控制器所保留的所有 Active Directory 对象和属性。 但是，不能对存储在 RODC 上的数据库进行更改。 更改必须在可写域控制器上进行，然后复制回 RODC。

RODC 主要用于在远程或分支机构环境中部署，这通常是相对较少的用户、物理安全性差、中心站点的网络带宽相对较差的人员，以及 (IT) 的信息技术知识有限的人员。 部署 Rodc 会提高安全性并更有效地访问网络资源。 有关 RODC 功能的详细信息，请参阅 [AD DS：只读域控制器](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732801(v=ws.10))。 有关如何部署 RODC 的详细信息，请参阅 [只读域控制器循序渐进指南](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc772234(v=ws.10))

> [!NOTE]
> 本指南不说明如何确定每个站点中每个域的正确数量的域控制器和域控制器硬件要求。

## <a name="in-this-section"></a>本节内容

- [规划目录林根级域控制器放置](../../ad-ds/plan/Planning-Forest-Root-Domain-Controller-Placement.md)

- [规划区域域控制器放置](../../ad-ds/plan/Planning-Regional-Domain-Controller-Placement.md)

- [规划全局编录服务器放置](../../ad-ds/plan/Planning-Global-Catalog-Server-Placement.md)

- [规划操作主机角色放置](../../ad-ds/plan/Planning-Operations-Master-Role-Placement.md)
