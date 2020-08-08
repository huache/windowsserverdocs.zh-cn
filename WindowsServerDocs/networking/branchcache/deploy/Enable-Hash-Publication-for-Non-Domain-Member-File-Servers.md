---
title: 启用非域成员文件服务器的哈希发布
description: 本主题是适用于 Windows Server 2016 的 BranchCache 部署指南的一部分，它演示了如何在分布式和托管缓存模式下部署 BranchCache，以优化分支机构中的 WAN 带宽使用情况
manager: brianlic
ms.topic: get-started-article
ms.assetid: 11584b73-f9e2-4530-afa5-b8df970e6b24
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 80c65b20dcbae89ecccb67af22e3f569cd0d5c31
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969654"
---
# <a name="enable-hash-publication-for-non-domain-member-file-servers"></a>启用非域成员文件服务器的哈希发布

>适用于：Windows Server（半年频道）、Windows Server 2016

使用安装了文件服务服务器角色的 "**网络文件 BranchCache** " 角色服务的文件服务器上的 "本地计算机组策略2016，你可以使用此过程配置 BranchCache 的哈希发布。

此过程适用于非域成员文件服务器。 如果在域成员文件服务器上执行此过程，并且还使用域组策略来配置 BranchCache，则域组策略设置将替代本地组策略设置。

**Administrators**中的成员身份或同等身份是执行此过程所需的最低要求。

> [!NOTE]
> 如果有一个或多个域成员文件服务器，则可以将其添加到 Active Directory 域服务中 (OU) ，然后使用组策略一次为所有文件服务器配置哈希发布，而不是单独配置每个文件服务器。 有关详细信息，请参阅[为域成员文件服务器启用哈希发布](../../branchcache/deploy/Enable-Hash-Publication-for-Domain-Member-File-Servers.md)。

### <a name="to-enable-hash-publication-for-one-file-server"></a>为一个文件服务器启用哈希发布

1.  打开 Windows PowerShell，键入 **mmc**，然后按 Enter。 Microsoft 管理控制台 (MMC) 会打开。

2.  在 MMC 的“文件”**** 菜单上，单击“添加/删除管理单元”****。 "**添加或删除管理单元**" 对话框将打开。

3.  在 "**添加或删除管理单元**" 的 "**可用管理单元**" 中，双击**组策略对象编辑器**。 此时将打开组策略向导，其中选择了 "本地计算机" 对象。 单击“完成”****，然后单击“确定”****。

4.  在本地组策略编辑器 MMC 中，展开以下路径： "**本地计算机策略**"、"**计算机配置**"、"**管理模板**"、"**网络**"、" **Lanman 服务器**"。 单击 " **Lanman 服务器**"。

5.  在详细信息窗格中，双击 " **BranchCache 的哈希发布**"。 " **BranchCache 的哈希发布**" 对话框将打开。

6.  在 " **BranchCache 的哈希发布**" 对话框中，单击 "**启用**"。

7.  在 "选项" 中，单击 "**允许对所有共享文件夹进行哈希发布**"，然后单击以下**选项**之一：

    1.  若要为此计算机上的所有共享文件夹启用哈希发布，请单击 "**允许对所有共享文件夹进行哈希发布**"。

    2.  若要仅为启用了 BranchCache 的共享文件夹启用哈希发布，请**针对启用了 branchcache 的共享文件夹单击 "仅允许哈希发布**"。

    3.  若要禁止对计算机上的所有共享文件夹进行哈希发布，即使已在文件共享上启用 BranchCache，请单击 "**禁止对所有共享文件夹进行哈希发布**"。

8.  单击“确定”。



