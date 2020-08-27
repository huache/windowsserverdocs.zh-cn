---
ms.assetid: e6b72a80-e8b7-4305-be0c-0a290f468d36
title: 在 Windows Server 2003 组织中部署 AD DS
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 708e18d739933d279cb79fa28e5c420f6d2b2a58
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938007"
---
# <a name="deploying-ad-ds-in-a-windows-server-2003-organization"></a>在 Windows Server 2003 组织中部署 AD DS

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

如果你的组织当前正在运行 Windows Server 2003 Active Directory，你可以通过执行将部分或全部域控制器的操作系统就地升级到 Windows Server 2008 或引入在你的环境中运行 Windows Server 2008 的域控制器，来 Active Directory 域服务 (AD DS) 部署 Windows Server 2008。

在将运行 Windows Server 2008 的域控制器添加到现有 Windows Server 2003 Active Directory 域之前，必须运行 **adprep**，这是一个命令行工具。 Adprep 扩展了 AD DS 架构，更新了所选对象的默认安全描述符，并添加了某些应用程序所需的新目录对象。 Adprep 在 Windows Server 2008 安装磁盘上可用 ( # A0) 。 有关详细信息，请参阅 [Adprep](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc731728(v=ws.11))。

下图显示了在当前运行 Windows Server 2003 Active Directory 的网络环境中部署 Windows Server 2008 AD DS 的步骤。

![在 windows 2003 组织中部署](media/Deploying-AD-DS-in-a-Windows-Server-2003-Organization/900c4eee-1119-4a9a-9310-755597428b71.gif)

> [!NOTE]
> 如果要将域或林功能级别设置为 Windows Server 2008，环境中的所有域控制器都必须运行 Windows Server 2008 操作系统。

将从 Windows Server 2003 环境升级的资源域和帐户域合并为 Windows Server 2008 AD DS 部署的一部分可能需要林间或林内域重构。 在林之间重新构建 AD DS 域有助于降低组织在 AD DS 中的表示形式的复杂性，并有助于降低关联的管理成本。 重构林中 AD DS 域可减少复制流量，减少所需的用户和组管理量，并简化组策略的管理，从而帮助你降低组织的管理开销。 有关详细信息，请参阅 [ADMT 指南：迁移和重新构建 Active Directory 域](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc974332(v=ws.10))。

有关可用于在运行 Windows Server 2003 Active Directory 的组织中计划和部署 AD DS 的详细任务的列表，请参阅 [清单：在 Windows server 2003 组织中部署 AD DS](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771407(v=ws.10))。
