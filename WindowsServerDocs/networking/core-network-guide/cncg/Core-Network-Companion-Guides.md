---
title: 核心网络助理指南
description: 本主题概述了 Windows Server 2016 Core 网络指南的助理指南
manager: brianlic
ms.technology: networking
ms.prod: windows-server
ms.topic: article
ms.assetid: d57af0bd-9301-4f62-9888-f528cd10451d
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 5f3ae4f9c22e61a8428a257d9324fe164eeaa04b
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319103"
---
# <a name="core-network-companion-guidance"></a>核心网络助理指南

>适用于：Windows Server（半年频道）、Windows Server 2016

Windows Server 2016 [Core 网络指南](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/core-network-guide)提供了有关如何使用新的根域和支持的网络基础结构部署新的 Active Directory&reg; 林的说明，但助理指南提供了向网络添加功能的能力。

在你部署完核心网络之后，每个助理指南都允许你完成一个具体的目标。 有些情况下，有多个助理指南，当它们一起部署并且顺序正确的时候，你可以用量化、合算、合理的方式实现非常复杂的目标。

如果你在见到“核心网络指南”之前部署你的 Active Directory 域和核心网络，你仍然可以使用“助理指南”向网络添加功能。 简单地使用“核心网络指南”作为先决条件列表，并且知道，要使用“助理指南”部署附加功能，你的网络必须满足“核心网络指南”提供的先决条件。

## <a name="core-network-companion-guide-deploy-server-certificates-for-8021x-wired-and-wireless-deployments"></a>核心网络助理指南：部署用于 802.1 X 有线和无线部署的服务器证书 

本助理指南介绍了如何通过为运行网络策略服务器 \(NPS\)、远程访问服务 \(RAS\)或这两者的计算机部署服务器证书，在核心网络上进行构建。

使用可扩展的身份验证协议部署基于证书的身份验证方法时需要服务器证书 \(EAP\) 和受保护的 EAP \(PEAP\) 用于网络访问身份验证。 为基于 EAP 和 PEAP 证书的身份验证方法 \(AD CS\) Active Directory 证书服务部署服务器证书具有以下优点：

- 将 NPS 或 RAS 服务器的标识绑定到私钥
- 向域成员 NPS 和 RAS 服务器自动注册证书的经济高效、安全的方法
- 是管理证书和证书颁发机构的有效方法
- 基于证书的身份验证所提供的安全性
- 为其他目的扩展证书用途的功能
  
有关如何部署服务器证书的说明，请参阅为[802.1 x 有线和无线部署部署服务器证书](server-certs/Deploy-Server-Certificates-for-802.1X-Wired-and-Wireless-Deployments.md)。  
## <a name="core-network-companion-guide-deploy-password-based-8021x-authenticated-wireless-access"></a>核心网络助理指南：部署基于密码的 802.1 X 身份验证无线访问

本助理指南介绍了如何通过提供有关如何使用受保护的可扩展身份验证协议 \ – Microsoft 质询握手身份验证协议版本 2 \(PEAP\-MS\-CHAP v2\)部署电气和电子工程师协会 \(IEEE\) 802.1 X\-身份验证 IEEE 802.11 无线访问的说明，在核心网络上进行构建。

身份验证方法 PEAP\-MS\-CHAP v2 要求对运行网络策略服务器 \(\) NPS 的服务器进行身份验证，并使用服务器证书提供了无线客户端，以便向客户端证明 NPS 标识，但用户身份验证不是通过使用证书来执行，而是用户提供其域用户名和密码。

由于 PEAP\-MS\-CHAP v2 要求用户在身份验证过程中提供基于密码的凭据（而不是证书），因此部署比 EAP\-TLS 或 PEAP\-TLS 更简单、更便宜。

使用 PEAP\-MS\-CHAP v2 身份验证方法部署无线访问之前，必须执行以下操作：

1. 按照核心网络指南中的说明部署核心网络基础结构，或已在网络上部署了该指南中提供的技术。
2. 按照核心网络助理指南部署用于 802.1 X 有线和无线部署的服务器证书中的说明，或已在网络上部署了该指南中提供的技术。

有关如何使用 PEAP\-MS\-CHAP v2 部署无线访问的说明，请参阅[部署基于密码 802.1 x 身份验证的无线访问](wireless/a-deploy-8021X-wireless-access.md)。

## <a name="core-network-companion-guide-deploy-branchcache-hosted-cache-mode"></a>核心网络助理指南：部署 BranchCache 托管缓存模式

本助理指南介绍了如何在一个或多个分支机构中的托管缓存模式下部署 BranchCache。

BranchCache 是一种广域网络（WAN）带宽优化技术，包含在某些版本的 Windows Server 2016 和 Windows 10 操作系统以及更早版本的 Windows 和 Windows Server 中。

当你在托管缓存模式中部署 BranchCache 时，分支机构的内容缓存会托管在一个或多个称为托管缓存服务器的服务器计算机上。 托管缓存服务器除了托管缓存外，还可以运行工作负荷，这允许你将服务器用于分支机构中的多个目的。

BranchCache 托管缓存模式提高了缓存效率，因为即使最初请求和缓存数据的客户端脱机，内容也可用。 由于托管缓存服务器始终可用，更多内容得到缓存，从而节省更多 WAN 带宽，并提高 BranchCache 效率。

当你部署托管缓存模式时，多子网分支机构中的所有客户端都可以访问一个存储在托管缓存服务器上的缓存，即使客户端位于不同的子网中。

有关如何在托管缓存模式下部署 BranchCache 的说明，请参阅[部署 Branchcache 托管缓存模式](bc-hcm/1-Deploy-Bc-Hcm.md)。
