---
title: 监视用于活动和状态的连接的远程客户端
description: 本主题是 Windows Server 2016 中的远程访问监视和记帐指南的一部分。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: beb94475-b21f-46a9-ac51-bf2bb28ca94e
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 949a8b4da7c85c82c247c638df09768c5d0790e7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860540"
---
# <a name="monitor-connected-remote-clients-for-activity-and-status"></a>监视用于活动和状态的连接的远程客户端

>适用于：Windows Server（半年频道）、Windows Server 2016

**注意：** Windows Server 2012 将 DirectAccess 和远程访问服务（RAS）合并到单个远程访问角色中。  
  
你可以使用远程访问服务器上的管理控制台来监视远程客户端活动和状态。  
  
> [!NOTE]  
> 您必须以 Domain Admins 组成员或每台计算机上 Administrators 组的成员身份登录才能完成本主题中所述的任务。 如果你在使用作为 Administrators 组成员的帐户登录时无法完成任务，请尝试在使用域管理员组的成员帐户登录时执行此任务。  
  
#### <a name="to-monitor-remote-client-activity-and-status"></a>监视远程客户端活动和状态  
  
1.  在“服务器管理器”中，单击“工具”，然后单击“远程访问管理”。  
  
2.  单击 "**报告**"，导航到**远程访问管理控制台**中的**远程访问报告**。  
  
3.  单击 "**远程客户端状态**"，导航到**远程访问管理控制台**中的远程客户端活动和状态用户界面。  
  
4.  你将看到连接到远程访问服务器的用户的列表以及有关这些用户的详细统计信息。 单击该列表中与客户端对应的第一行。 选择行时，"远程用户" 活动将显示在预览窗格中。  
  
![Windows PowerShell](../../../media/Monitor-connected-remote-clients-for-activity-and-status/PowerShellLogoSmall.gif)***<em>windows powershell 等效命令</em>***  
  
下面的 Windows PowerShell cmdlet 将执行与前面的过程相同的功能。 每行输入一个 cmdlet，即使此处由于格式设置约束导致它们换行而显示在多行中。  
  
```  
PS> Get-RemoteAccessConnectionStatistics  
```  
  
可以通过使用下表中的字段，根据选择的条件筛选用户统计信息。  
  
|字段名称|值|  
|-------|-----|  
|Username|远程用户的用户名或别名。 通配符可用于选择一组用户，例如 contoso\\* 或 \*\administrator。|  
|Hostname|远程用户的计算机帐户名称。 也可以指定 IPv4 或 IPv6 地址。|  
|类型|DirectAccess 或 VPN。 如果选择了 DirectAccess，则会列出使用 DirectAccess 连接的所有远程用户。 如果选择了 VPN，则会列出使用 VPN 连接的所有远程用户。|  
|ISP 地址|远程用户的 IPv4 或 IPv6 地址。|  
|IPv4 地址|将远程用户连接到企业网络的隧道的内部 IPv4 地址。|  
|IPv6 地址|将远程用户连接到企业网络的隧道的内部 IPv6 地址。|  
|协议/隧道|远程客户端使用的转换技术。 这是 Teredo、6to4 或 ip-https，适用于 DirectAccess 用户，它是适用于 VPN 用户的 PPTP、L2TP、SSTP 或 IKEv2。|  
|访问的资源|所有访问特定企业资源或终结点的用户。 对应于此字段的值是服务器的主机名/IP 地址。|  
|Server|客户端所连接到的远程访问服务器。 这仅与群集和多站点部署相关。|  
  
  
  


