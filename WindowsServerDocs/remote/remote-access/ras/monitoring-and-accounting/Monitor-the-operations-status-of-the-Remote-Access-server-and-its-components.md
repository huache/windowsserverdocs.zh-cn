---
title: 监视远程访问服务器及其组件的操作状态
description: 本主题是 Windows Server 2016 中的远程访问监视和记帐指南的一部分。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 077a3a64-2fa3-4994-9711-ec1fbdc081ba
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 64471ba81842fb91a7f6ef765e171949294102fa
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314184"
---
# <a name="monitor-the-operations-status-of-the-remote-access-server-and-its-components"></a>监视远程访问服务器及其组件的操作状态

>适用于：Windows Server（半年频道）、Windows Server 2016

**注意：** Windows Server 2012 将 DirectAccess 和路由和远程访问服务 (RRAS) 合并到了单个远程访问角色中。  
  
远程访问服务器中的管理控制台可用于监视其操作状态。  
  
> [!NOTE]  
> 您必须以 Domain Admins 组成员或每台计算机上 Administrators 组的成员身份登录才能完成本主题中所述的任务。 如果你在使用作为 Administrators 组成员的帐户登录时无法完成任务，请尝试在使用域管理员组的成员帐户登录时执行此任务。  
  
#### <a name="to-monitor-the-remote-access-server-operations-status"></a>监视远程访问服务器操作状态  
  
1.  在“服务器管理器”中，单击“工具”，然后单击“远程访问管理”。  
  
2.  单击 "**仪表板**"，导航到 "**远程访问管理" 控制台**中的 "**远程访问报告**"。  
  
3.  在监视仪表板上，请注意 "**服务器状态**" 磁贴中的 "**操作状态**" 磁贴。 此磁贴列出服务器操作状态以及服务器的所有组件的状态。  
  
4.  在右窗格中的 "**任务**" 下，单击 "**刷新**" 以重新加载操作状态。 操作状态每隔五分钟自动刷新一次，这是默认的刷新间隔。 若要更改默认刷新间隔，请单击 "**配置刷新间隔**"。  
  
![Windows PowerShell](../../../media/Monitor-the-operations-status-of-the-Remote-Access-server-and-its-components/PowerShellLogoSmall.gif)***<em>windows powershell 等效命令</em>***  
  
下面的 Windows PowerShell cmdlet 将执行与前面的过程相同的功能。 每行输入一个 cmdlet，即使此处由于格式设置约束导致它们换行而显示在多行中。  
  
> [!NOTE]  
> 包含群集操作状态的命令，以供参考。  
  
```  
PS> Get-RemoteAccessHealth  
PS> Get-RemoteAccessHealth -Cluster  
```  
  


