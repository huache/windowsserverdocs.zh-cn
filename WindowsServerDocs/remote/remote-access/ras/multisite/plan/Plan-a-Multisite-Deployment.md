---
title: 规划多站点部署
description: 本主题是在 Windows Server 2016 中的多站点部署中部署多台远程访问服务器指南的一部分。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: 8387eabe-7363-4367-b5b1-03c67baa2933
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 507dae03ca13f4d485d6d1db0676f9d3c7b057bc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858330"
---
# <a name="plan-a-multisite-deployment"></a>规划多站点部署

>适用于：Windows Server（半年频道）、Windows Server 2016

 Windows Server 2016，Windows Server 2012 将 DirectAccess 和路由和远程访问服务（RRAS） VPN 合并到单个远程访问角色中。 本概述介绍了在多站点配置中部署 Windows Server 2016 或 Windows Server 2012 远程访问所需的规划步骤。  
  
1.  [使用高级设置部署单个 DirectAccess 服务器](https://technet.microsoft.com/library/hh831436(v=ws.11).aspx)。 此步骤包括规划部署单个服务器所需的基础结构。 它包括规划网络和服务器设置、证书要求、DNS 设置、网络位置服务器部署、DirectAccess 管理服务器、Active Directory 设置和组策略对象（Gpo）。  
  
2.  [步骤2：规划多站点基础结构](Step-2-Plan-the-Multisite-Infrastructure.md)。 此步骤包括 Active Directory 和 GPO 规划以及 DNS 配置。  
  
3.  [步骤3：规划多站点部署](Step-3-Plan-the-Multisite-Deployment.md)。 此步骤包括规划证书设置、网络位置服务器配置、客户端入口点设置、IPv6 前缀设置以及（可选）全局负载平衡设置。  
  
> [!NOTE]  
> 记录远程访问高级部署的规划决策。 对于完成部署步骤所涉及的每个人，此记录可用来帮助进行工作。  
  
完成这些规划步骤后，请参阅[配置多站点部署](../configure/Configure-a-Multisite-Deployment.md)。  
  


