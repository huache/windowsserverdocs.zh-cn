---
title: 测试实验室指南-演示 DirectAccess 多站点部署
description: 本主题是测试实验室指南-演示适用于 Windows Server 2016 的 DirectAccess 多站点部署的一部分
manager: brianlic
ms.topic: article
ms.assetid: 3c98106c-67cc-406a-810e-f2e09f7e2c5e
ms.author: lizross
author: eross-msft
ms.openlocfilehash: bee710cea7711118e1953f138a4c69ee513ff2b0
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87955184"
---
# <a name="test-lab-guide-demonstrate-a-directaccess-multisite-deployment"></a>测试实验室指南：演示 DirectAccess 多站点部署

>适用于：Windows Server（半年频道）、Windows Server 2016

远程访问是 Windows Server 2016、Windows Server 2012 R2 和 Windows Server 2012 操作系统中的一种服务器角色，使远程用户可以使用 DirectAccess 或 RRAS VPN 安全访问内部网络资源。 本指南包含扩展[测试实验室指南的分步说明：演示混合使用 IPv4 和 IPv6 的 DirectAccess 单服务器设置](https://go.microsoft.com/fwlink/p/?LinkId=237004)，以演示多站点方案中的远程访问。

通过在多站点方案中部署远程访问，你可以在地理位置不同的位置配置远程访问服务器。 之前，远程用户需要始终通过特定 DirectAccess 服务器连接到企业网络。 对于 Windows Server 2016、Windows Server 2012 R2 或 Windows Server 2012 以及 windows 10 或 windows 8，您可以为部署中的每个地理位置配置入口点。 每个入口点可以是单个远程访问服务器，也可以是远程访问服务器的群集。 远程用户可以选择连接到任何组织的远程访问入口点。 例如，如果一个远程用户通常连接到位于亚洲的远程访问入口点，但随后又进入了欧洲，则客户端计算机会自动连接到最近的远程访问入口点。

## <a name="about-this-guide"></a>关于本指南
本指南包含使用九个服务器和三台客户端计算机配置和演示远程访问的说明。 已完成的远程访问多站点测试实验室模拟了 intranet、Internet 和家庭网络，并演示了不同 Internet 连接方案中的远程访问功能。

> [!IMPORTANT]
> 此实验室是一个使用最小量计算机的概述证明。 本指南中详细介绍的配置仅适用于测试实验室目的，不可用于生产环境。



