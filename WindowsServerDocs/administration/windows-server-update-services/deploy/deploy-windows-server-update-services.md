---
title: 部署 Windows Server Update Services
description: Windows Server Update Service (WSUS) 主题 - 概述了部署流程，并提供了完成它的四个步骤的链接
ms.topic: get-started-article
ms.assetid: 2708f6b2-4252-4b8f-9b7e-84c9b4222075
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 78df9b93205e07e58310ad2077571b29b9ff5360
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624547"
---
# <a name="deploy-windows-server-update-services"></a>部署 Windows Server Update Services

>适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows Server Update Service (WSUS) 启用信息技术管理员部署最新的 Microsoft 产品更新。 WSUS 是可安装以管理和分配更新的 Windows Server 服务器角色。 WSUS 服务器可以作为组织内其他 WSUS 服务器的更新源。 充当更新源的 WSUS 服务器称为上游服务器。

在 WSUS 实现过程中，网络中必须至少有一台 WSUS 服务器连接到 Microsoft 更新以获取可用的更新信息。 你可以根据网络安全和配置来决定多少其他服务器直接连接到 Microsoft 更新。

本指南提供了有关规划和部署 Windows Server Update Service 的概念信息。

-   [规划 WSUS 部署](../plan/plan-your-wsus-deployment.md)

-   [步骤 1：安装 WSUS 服务器角色](1-install-the-wsus-server-role.md)

-   [步骤 2：配置 WSUS](2-configure-wsus.md)

-   [步骤 3：在 WSUS 中批准和部署更新](3-approve-and-deploy-updates-in-wsus.md)

-   [步骤 4：为自动更新配置组策略设置](4-configure-group-policy-settings-for-automatic-updates.md)
