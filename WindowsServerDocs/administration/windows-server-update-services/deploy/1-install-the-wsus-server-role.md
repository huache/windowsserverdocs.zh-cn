---
title: 步骤 1 - 安装 WSUS 服务器角色
description: Windows Server Update Service (WSUS) 主题 - 介绍了如何使用服务器管理器安装服务器角色
ms.topic: article
ms.assetid: fabc8619-350e-403b-96f8-116424931300
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c311ecb5c3d00e09fd1b7443a3a8ef9f82003902
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640715"
---
# <a name="step-1-install-the-wsus-server-role"></a>步骤 1：安装 WSUS 服务器角色

>适用于：Windows Server 2019、Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

部署 WSUS 服务器的下一步是安装 WSUS 服务器角色。 以下过程描述了使用服务器管理器安装 WSUS 服务器角色的步骤。

> [!IMPORTANT]
> 该安装过程仅包含使用 Windows 内部数据库 (WID) 安装 WSUS 的步骤。 使用 Microsoft SQL Server 安装 WSUS 的过程记录在 [WSUS 论坛](/answers/topics/windows-server-update-services.html)中。

### <a name="to-install-the-wsus-server-role"></a>安装 WSUS 服务器角色的步骤

1.  使用作为本地 Administrators 组成员的帐户登录到你计划安装 WSUS 服务器角色的服务器。

2.  在“服务器管理器”  中，单击“管理”  ，然后单击“添加角色和功能”  。

3.  在“开始之前”  页上，单击“下一步”  。

4.  在“选择安装类型”  页上，确认已选择了“基于角色或基于功能的安装”  选项，然后单击“下一步”  。

5.  在“选择目标服务器”  页上，选择服务器所在的位置（从服务器池或虚拟硬盘中）。 选择位置后，选择你想安装 WSUS 服务器角色的服务器，然后单击“下一步”  。

6.  在“选择服务器角色”  页上，选择“Windows Server Update Services”  。  此时将打开“添加 Windows Server Update Services 所需的功能”  。 单击“添加功能”  ，然后单击“下一步”  。

7.  在“选择功能”  页上， 保留默认选择，然后单击“下一步”  。

    > [!IMPORTANT]
    > WSUS 仅需要默认的 Web Server 角色配置。 如果你在设置 WSUS 时收到有关额外 Web Server 角色配置的提示，你可安全接受默认值并继续设置 WSUS。

8.  在 **“Windows Server Update Services”** 页上，单击 **“下一步”** 。

9. 在 **“选择角色服务”** 页上，保留默认选择，然后单击 **“下一步”** 。

    > [!TIP]
    > 必须选择一种数据库类型。 如果数据库选项已全部清除（未选择），安装后任务将失败。

10. 在“内容位置选择”  页上，键入有效的位置以存储更新。 例如，可以在 K 盘的根目录下专门为此创建一个名为 WSUS_database 的文件夹，并键入“k:\WSUS_database”  作为有效的位置。

11. 单击 **下一步**。 此时将打开“Web 服务器角色(IIS)”  页。 查看信息，然后单击“下一步”  。 在“为 Web 服务器(IIS)选择要安装的角色服务”  中，保留默认值，然后单击“下一步”  。

12. 在 **“确认安装选择”** 页上，查看所选的选项，然后单击 **“安装”** 。 WSUS 安装向导将运行。 这可能需要几分钟才能完成。

13. 等 WSUS 安装完成后，在“安装进度”  页上的摘要窗口中，单击“启动安装后任务”  。 文本发生变化，请求：**正在配置服务器，请稍候**。 任务完成后，文本更改为：**已成功完成配置**。 单击 **“关闭”** 。

14. 在 **服务器管理器**中，验证是否出现提醒你需要重新启动的通知。 根据安装的服务器角色，这可能有所变化。 如果需要重新启动，请务必重新启动服务器以完成安装。

> [!IMPORTANT]
> 此时，安装过程已结束，但是若要 WSUS 正常工作，你必须继续执行[步骤 2：配置 WSUS](2-configure-wsus.md)。