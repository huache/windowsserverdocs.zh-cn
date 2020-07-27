---
title: 远程桌面服务 - 多重身份验证
description: 有关如何将 MFA 与 RDS 结合使用的规划信息。
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: 09ea784e-5644-417a-a3d9-bdbcebc313f9
author: lizap
ms.author: elizapo
ms.date: 09/07/2016
manager: dongill
ms.openlocfilehash: 179feca4870e62f81ed71fabb7b8fd1cb418d391
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962179"
---
# <a name="remote-desktop-services---multi-factor-authentication"></a>远程桌面服务 - 多重身份验证

>适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016

将 Active Directory 的强大功能与多重身份验证相结合，对你的业务资源实施高安全性保护。

对于连接到桌面和应用程序的最终用户，其体验类似于他们在执行第二项身份验证措施以连接到所需资源时的体验：
- 从 RDP 文件或通过远程桌面客户端应用程序启动桌面或 RemoteApp
- 连接到 RD 网关以进行安全的远程访问时，收到短信或移动应用程序 MFA 质询
- 正确验证身份并连接到他们的资源！

有关配置过程的更多详细信息，请查看[使用网络策略服务器 (NPS) 扩展和 Azure AD 集成远程桌面网关基础结构](/azure/multi-factor-authentication/nps-extension-remote-desktop-gateway)。
