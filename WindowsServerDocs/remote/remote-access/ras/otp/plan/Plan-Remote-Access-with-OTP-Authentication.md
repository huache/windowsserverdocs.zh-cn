---
title: 规划带有 OTP 身份验证的远程访问
description: 本主题是指南使用 Windows Server 2016 中的 "使用 OTP 身份验证部署远程访问" 指南的一部分。
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 762bc463-eead-46ac-8b90-32355743c27c
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 69127ef86e1e14620f8cbb29322e930c6d921702
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404353"
---
# <a name="plan-remote-access-with-otp-authentication"></a>规划带有 OTP 身份验证的远程访问

>适用于：Windows Server（半年频道）、Windows Server 2016

 Windows Server 2016 和 Windows Server 2012 将 DirectAccess 和路由和远程访问服务（RRAS） VPN 合并到单个远程访问角色中。 本概述介绍了部署单个 Windows Server 2016 或 Windows Server 2012 远程访问多站点部署所需的配置步骤。  
  
  
-  步骤1：[使用高级设置部署单个 DirectAccess 服务器](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings)。 此步骤包括规划部署单个服务器所需的基础结构。 它包括规划网络和服务器设置、证书要求、DNS 设置、网络位置服务器部署、DirectAccess 管理服务器、Active Directory 设置和组策略对象（Gpo）。  
  
-   [步骤2：规划 RADIUS 服务器部署](Step-2-Plan-the-RADIUS-Server-Deployment.md)  
  
-   [步骤3：规划 OTP 证书部署](Step-3-Plan-OTP-Certificate-Deployment.md)  
  
-   [步骤4：在远程访问服务器上规划 OTP](Step-4-Plan-for-OTP-on-the-Remote-Access-Server.md)  
  
完成这些规划步骤后，请参阅[使用 OTP 身份验证配置远程访问](https://technet.microsoft.com/windows-server-docs/networking/remote-access/ras/otp/configure/configure-ra-with-otp-authentication)。 若要了解如何在实验室环境中将多站点部署配置为概念证明，请参阅[测试实验室指南：使用 OTP 身份验证和 RSA SecurID 演示 DirectAccess](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/tlg-otp-securid/test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid)。  
  


