---
title: 安装 MultiPoint 服务
description: 了解如何在 Windows Server 2016 中安装和配置 MultiPoint 服务
ms.date: 07/22/2016
ms.topic: article
ms.assetid: f6f8970b-de3f-4255-b2a1-5472a16ed02f
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: b1148c8261e97a5cb3c839337a64442520744827
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87970664"
---
# <a name="install-multipoint-services"></a>安装 MultiPoint 服务
如果从头开始安装服务器，请按照这些说明安装 MultiPoint 服务。

安装 Windows Server 2016 后，以管理员身份登录成功。 使用可以启用 MultiPoint 服务的服务器管理器。 服务器管理器在启动时自动打开。 在仪表板上，选择 "**添加角色和功能**" 以启用 MultiPoint 服务，然后按照向导中的说明进行操作。

在安装类型部分中，你可能会选择
- 基于角色或基于功能的安装或
- 远程桌面服务安装

对于标准 MultiPoint 服务部署，我们建议选择远程桌面服务安装，这将允许你在 "部署类型" 下轻松选择 "MultiPoint 服务" 角色。 对于基于角色的安装，你将需要在角色列表中选择 " **MultiPoint 服务**"。 安装成功后，服务器将重新启动。

## <a name="configure-your-primary-station"></a>配置主工作站

1.  在 "**创建 MultiPoint Server 工作站**" 页上，为该监视器键入键盘上指定的字母。 正确的密钥条目将该工作站的键盘和鼠标关联起来。
2.  以管理员身份登录。