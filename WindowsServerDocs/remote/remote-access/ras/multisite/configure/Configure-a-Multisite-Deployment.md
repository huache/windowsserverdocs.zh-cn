---
title: 配置多站点部署
description: 本主题是在 Windows Server 2016 中的多站点部署中部署多台远程访问服务器指南的一部分。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb84920e-7cf5-4266-b071-d09e3d5e1f10
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 4a0229d5605271876f89e8e0ae75f8612e3f5762
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314009"
---
# <a name="configure-a-multisite-deployment"></a>配置多站点部署

>适用于：Windows Server（半年频道）、Windows Server 2016

 Windows Server 2016 将 DirectAccess 和远程访问服务（RAS） VPN 合并到了单个远程访问角色中。 本概述介绍了部署单个 Windows Server 2016 或 Windows Server 2012 远程访问多站点部署所需的配置步骤。  
  
-   步骤1：[使用高级设置部署单个 DirectAccess 服务器](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings)。 安装并配置单个远程访问服务器。 多站点部署要求在配置多站点部署之前安装单个服务器。  
  
-   [步骤2：配置多站点基础结构](Step-2-Configure-the-Multisite-Infrastructure.md)。 对于多站点部署，你必须配置其他 Active Directory 站点和域控制器。 如果未使用自动配置的 Gpo，还需要其他安全组和组策略对象（Gpo）。  
  
-   [步骤3：配置多站点部署](Step-3-Configure-the-Multisite-Deployment.md)-在额外的远程访问服务器上安装远程访问角色，启用多站点部署，并将其他服务器配置为部署的入口点。  
  
-   [步骤4：验证多站点部署](Step-4-Verify-the-Multisite-Deployment.md) 
  


