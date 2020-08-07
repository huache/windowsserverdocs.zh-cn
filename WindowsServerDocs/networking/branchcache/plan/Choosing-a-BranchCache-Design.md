---
title: 选择一个 BranchCache 设计
description: 本主题是适用于 Windows Server 2016 的 BranchCache 部署指南的一部分，它演示了如何在分布式和托管缓存模式下部署 BranchCache，以优化分支机构中的 WAN 带宽使用情况
manager: brianlic
ms.topic: get-started-article
ms.assetid: 86c1ccad-2aa4-40fe-84c1-f77c49eb1216
ms.author: lizross
author: eross-msft
ms.openlocfilehash: f64d27f3ef36c587e2ec5c08f51723942ba6a28c
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87937506"
---
# <a name="choosing-a-branchcache-design"></a>选择一个 BranchCache 设计

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题来了解 BranchCache 模式并为您的部署选择最佳模式。

您可以使用本指南通过以下模式和模式组合部署 BranchCache。

-   所有分支机构均配置为分布式缓存模式。

-   所有分支机构都配置为使用托管缓存模式，并且在站点上具有托管缓存服务器。

-   某些分支机构配置为使用分布式缓存模式，而某些分支机构在站点上有托管缓存服务器，并且配置为使用托管缓存模式。

下图描绘了双重模式安装，其中一个分支机构配置为使用分布式缓存模式，一个分支机构配置为托管缓存模式。

![选择一种 BranchCache 设计](../../media/Choosing-a-BranchCache-Design/bc_new_modes.jpg)

部署 BranchCache 之前，请选择你想要为组织中的每个分支机构使用的模式。



