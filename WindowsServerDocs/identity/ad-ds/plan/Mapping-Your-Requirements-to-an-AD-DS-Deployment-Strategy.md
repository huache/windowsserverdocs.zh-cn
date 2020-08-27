---
ms.assetid: ce3be131-06ad-41dc-a26b-1168fa68c8ed
title: 将要求映射到 AD DS 部署策略
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: fc8dec94aad6c742fa62560d73b74e4c8f22b466
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938997"
---
# <a name="mapping-your-requirements-to-an-ad-ds-deployment-strategy"></a>将要求映射到 AD DS 部署策略

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

查看并确定 Active Directory 域服务 (AD DS) 设计和部署要求，并确定与特定部署相关的要求后，可以将这些要求映射到特定的 AD DS 部署策略。

使用下表来确定哪个 AD DS 部署策略将映射到组织 AD DS 设计和部署要求的适当组合。  ( "是" 表示部署策略需要特定要求;"否" 表示部署策略不需要特定要求。 ) 

此表仅引用这三个主要 AD DS 部署策略，如本指南中所述：

-   [在新组织中部署 AD DS](../../ad-ds/plan/Deploying-AD-DS-in-a-New-Organization.md)

-   [在 Windows Server 2003 组织中部署 AD DS](../../ad-ds/plan/Deploying-AD-DS-in-a-Windows-Server-2003-Organization.md)

-   [在 Windows 2000 组织中部署 AD DS](../../ad-ds/plan/Deploying-AD-DS-in-a-Windows-2000-Organization.md)

不过，你可以通过使用 AD DS 设计和部署要求的任意组合来创建混合或自定义 AD DS 部署策略，以满足你的组织的需求。

| AD DS 设计和部署要求 | 在新组织中部署 AD DS | 在 Windows Server 2003 组织中部署 AD DS | 在 Windows Server 2000 组织中部署 AD DS |
| ---------------------------------------- | ------------------------------------- | ----------------------------------------------------- |----------------------------------------------- |
| [设计 Windows Server 2008 AD DS 的逻辑结构](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc770806(v=ws.10)) | 是 | 是 | 是 |
| [设计 Windows Server 2008 AD DS 的站点拓扑](Designing-the-Site-Topology.md) | 是 | 是 | 是 |
| 规划域控制器容量 | 是 | 是 | 是 |
| [部署 Windows Server 2008 目录林根级域](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174(v=ws.10)) | 是 | 否 | 否 |
| [部署 Windows Server 2008 地区域](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755118(v=ws.10)) | 是 | 是 | 是 |
| [为 AD DS 启用高级功能](../../ad-ds/plan/Enabling-Advanced-Features-for-AD-DS.md) | 是 |是，但在将域或林功能级别设置为 Windows Server 2008 之前，环境中的所有域控制器都必须运行 Windows Server 2008。 | 是，但在将域或林功能级别设置为 Windows Server 2008 之前，环境中的所有域控制器都必须运行 Windows Server 2008。 |
| [将 Active Directory 域升级到 Windows Server 2008 和 Windows Server 2008 R2 AD DS 域](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731188(v=ws.10)) | 否 | 是 | 是 |
| [ADMT 指南：迁移和重新构建 Active Directory 域](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332(v=ws.10)) | 是的，如果想要将试点域迁移到生产环境中，请与另一个组织合并，并将这两项信息技术整合 (它) 基础结构，或者合并从 Windows 2000 或 Windows Server 2003 环境就地升级的资源和帐户域。 | 是，如果要与另一个组织合并，并合并两个 IT 基础结构，或者合并你就地从 Windows 2000 或 Windows Server 2003 环境升级的资源和帐户域。 | 是，如果要与另一个组织合并，并合并两个 IT 基础结构，或者合并你就地从 Windows 2000 或 Windows Server 2003 环境升级的资源和帐户域。 |
| [ADMT 指南：迁移和重新构建 Active Directory 域](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332(v=ws.10)) | 否 | 是的，如果需要减少域的数量、减少复制流量以及所需的用户和组管理量，或者简化组策略的管理。 | 是的，如果需要减少域的数量、减少复制流量以及所需的用户和组管理量，或者简化组策略的管理。 |
