---
title: 部署网络策略服务器
description: 本主题提供指向 Windows Server 2016 的网络策略服务器部署内容的链接，并包含指向有关 NPS 的其他指南的链接。
manager: brianlic
ms.topic: article
ms.assetid: 6cfb50e0-7088-4295-97c5-14ff8776cbf8
ms.author: lizross
author: eross-msft
ms.openlocfilehash: b4f80d18b2facba7bb706bb566aed698c2a85c8d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87937408"
---
# <a name="deploy-network-policy-server"></a>部署网络策略服务器

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题获取有关部署网络策略服务器的信息。

>[!NOTE]
>有关其他网络策略服务器文档，可以使用以下库部分。
>- [网络策略服务器入门](nps-getstart-top.md)
>- [规划网络策略服务器](nps-plan-top.md)
>- [管理网络策略服务器](nps-manage-top.md)

Windows Server 2016 核心网络指南包含一个有关规划和安装网络策略服务器 NPS 的 \( 部分 \) ，指南中介绍的技术在 Active Directory 域中作为部署 NPS 的先决条件。 有关详细信息，请参阅 Windows Server 2016 [Core 网络指南](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/core-network-guide#BKMK_deployNPS1)中的 "部署 NPS1" 一节。

## <a name="deploy-nps-certificates-for-vpn-and-8021x-access"></a>为 VPN 和 802.1 X Access 部署 NPS 证书

如果要部署需要在 NPS 上使用服务器证书的身份验证方法（如可扩展身份验证协议 \( \) ） Eap 和受保护的 eap，则可以使用指南[为 802.1 x 有线和无线部署部署服务器证书](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments)来部署 NPS 证书。

## <a name="deploy-nps-for-8021x-wireless-access"></a>部署用于 802.1 X 无线访问的 NPS

若要部署 NPS 以实现无线访问，可以使用指南 "[部署基于密码的 802.1 x 身份验证无线访问](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/wireless/a-deploy-8021x-wireless-access)"。

## <a name="deploy-nps-for-windows-10-vpn-access"></a>部署适用于 Windows 10 VPN 访问的 NPS

\( \) 对于使用运行 Windows 10 的计算机和设备的远程员工，可以使用 NPS 处理 Always On 虚拟专用网络 VPN 连接的连接请求。

有关详细信息，请参阅[远程访问 Always On 适用于 Windows Server 2016 和 windows 10 的 VPN 部署指南](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy)。

