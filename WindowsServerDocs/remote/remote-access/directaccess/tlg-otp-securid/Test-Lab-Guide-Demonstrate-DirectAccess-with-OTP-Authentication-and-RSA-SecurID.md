---
title: 测试实验室指南-利用 OTP 身份验证和 RSA SecurID 演示 DirectAccess
description: 本主题是测试实验室指南的一部分-演示带有 OTP 身份验证的 DirectAccess 和用于 Windows Server 2016 的 RSA SecurID
manager: brianlic
ms.topic: article
ms.assetid: 10c7a49c-5671-4bec-b562-13fdd67f4629
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 90ffbb012c927e689f1ae852fdf7704520bc098d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87958535"
---
# <a name="test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid"></a>测试实验室指南：演示带有 OTP 身份验证和 RSA SecurID 的 DirectAccess

>适用于：Windows Server（半年频道）、Windows Server 2016

远程访问是 Windows Server 2016、Windows Server 2012 R2 和 Windows Server 2012 操作系统中的一种服务器角色，使远程用户能够使用 DirectAccess 或虚拟专用网络（ (Vpn) 与路由和远程访问服务 (RRAS) 安全访问内部网络资源。 本指南包含扩展[测试实验室指南：演示使用混合 IPv4 和 IPv6 的 DirectAccess 单服务器安装程序](https://go.microsoft.com/fwlink/p/?LinkId=237004)以演示远程访问一次性密码 (OTP) 配置的分步说明。

> [!WARNING]
> 本测试实验室指南的设计包括基础结构服务器，如运行 Windows Server 2012 R2 或 Windows Server 2012 (CA) 的域控制器和证书颁发机构。 本指南中未介绍如何使用此测试实验室指南来配置运行其他操作系统的基础结构服务器，以及配置其他操作系统的说明。

## <a name="about-this-guide"></a>关于本指南
Windows server 2016 中的远程访问，Windows Server 2012 R2 和 Windows Server 2012 添加了对使用 OTP 的客户端身份验证的支持。 在此测试实验室中，仅 RSA SecurID 用于演示使用远程访问的 OTP 功能。 还支持其他基于 RADIUS 的 OTP 解决方案，但超出了本测试实验室的范围。 本指南包含使用六个服务器和两个客户端计算机配置和演示远程访问的指导。 使用 OTP 测试实验室完成的远程访问模拟 intranet、Internet 和家庭网络，并演示了不同 Internet 连接方案中的远程访问功能。

> [!IMPORTANT]
> 此实验室是一个使用最小量计算机的概述证明。 本指南中详细介绍的配置仅适用于测试实验室目的，不可用于生产环境。



