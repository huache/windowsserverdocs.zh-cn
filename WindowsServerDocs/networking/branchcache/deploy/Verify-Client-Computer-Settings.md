---
title: 验证客户端计算机设置
description: 本主题是适用于 Windows Server 2016 的 BranchCache 部署指南的一部分，它演示了如何在分布式和托管缓存模式下部署 BranchCache，以优化分支机构中的 WAN 带宽使用情况
manager: brianlic
ms.topic: get-started-article
ms.assetid: 31ea58b0-d407-4f62-8ec6-6a1b19174042
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 14fcc91fc1fcf419a81dd5d774486dc5e0800f4e
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87937546"
---
# <a name="verify-client-computer-settings"></a>验证客户端计算机设置

>适用于：Windows Server（半年频道）、Windows Server 2016

你可以使用此过程来验证是否正确配置了 BranchCache 的客户端计算机。

> [!NOTE]
> 此过程包括手动更新组策略和重启 BranchCache 服务的步骤。 如果重新启动计算机，则无需执行这些操作，因为在这种情况下会自动执行这些操作。

你必须是**管理员**的成员或等效于执行此过程。

### <a name="to-verify-branchcache-client-computer-settings"></a>验证 BranchCache 客户端计算机设置

1.  若要在客户端计算机上刷新要验证其 BranchCache 配置的组策略，请以管理员身份运行 Windows PowerShell，键入以下命令，然后按 ENTER。

    `gpupdate /force`

2.  对于在托管缓存模式下配置并配置为通过服务连接点自动发现托管缓存服务器的客户端计算机，请运行以下命令，停止并重新启动 BranchCache 服务。

    `net stop peerdistsvc`

    `net start peerdistsvc`

3.  通过运行以下命令来检查当前 BranchCache 操作模式。

    `Get-BCStatus`

4.  在 Windows PowerShell 中，查看**BCStatus**命令的输出。

    **BranchCacheIsEnabled**的值应为**True**。

    在**ClientSettings**中， **CurrentClientMode**的值应为 " **DistributedClient** " 或 " **HostedCacheClient**"，具体取决于你使用本指南配置的模式。

    在**ClientSettings**中，如果在配置过程中配置了托管缓存模式并提供托管缓存服务器的名称，或者客户端已使用服务连接点自动定位了托管缓存服务器，则**HostedCacheServerList**应具有与托管缓存服务器的名称相同的值。 例如，如果托管缓存服务器命名为 HCS1，并且你的域为 corp.contoso.com，则**HostedCacheServerList**的值为**HCS1.corp.contoso.com**。

5.  如果上面列出的任何 BranchCache 设置没有正确的值，请使用本指南中的步骤来验证组策略或本地计算机策略设置以及你配置的防火墙例外，并确保它们是正确的。 此外，请重新启动计算机，或者按照此过程中的步骤刷新组策略并重新启动 BranchCache 服务。



