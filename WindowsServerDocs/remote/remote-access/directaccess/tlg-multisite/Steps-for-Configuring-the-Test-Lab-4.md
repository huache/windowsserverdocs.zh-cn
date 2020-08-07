---
title: 配置测试实验室的步骤
description: 本主题是测试实验室指南-演示适用于 Windows Server 2016 的 DirectAccess 多站点部署的一部分
manager: brianlic
ms.topic: article
ms.assetid: dc7205b4-a822-4038-ab67-ec0a870737f2
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 7fc886d8b4f68c86885cbe5c032247722d88e269
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87955199"
---
# <a name="steps-for-configuring-the-test-lab"></a>配置测试实验室的步骤

>适用于：Windows Server（半年频道）、Windows Server 2016

以下步骤介绍如何配置远程访问基础结构、配置远程访问服务器和客户端以及通过 Internet 和 Homenet 子网测试 DirectAccess 连接。

在此测试实验室指南中，你将通过执行以下步骤来生成多站点远程访问部署：

-   [步骤1：完成基本配置](assetId:///9eb4a9ba-9118-4ea3-8963-e643ec81c3ed)。 完成[测试实验室指南：演示带有混合 IPv4 和 IPv6 的 DirectAccess 单服务器安装程序](https://go.microsoft.com/fwlink/p/?LinkId=237004)中的所有步骤。

-   [步骤2：安装和配置 ROUTER1](assetId:///e4b1a298-d5b0-410e-970b-c5358a9378f9)。 ROUTER1 提供了公司网络和2公司网络子网之间的路由和转发功能。

-   [步骤3：安装和配置 CLIENT2](assetId:///6cbee1b5-f6f6-443f-8fa9-31cc5c05a0ee)。 CLIENT2 是一台 Windows 7 客户端计算机，用于演示 Windows Server 2016、Windows Server 2012 R2 或 Windows Server 2012 远程访问部署的向后兼容性。

-   [步骤4：配置 APP1](assetId:///a0ee655e-c01e-4bf3-a7b3-064e9614f810)。 将 APP1 配置为 ROUTER1 作为默认网关，并将 2-DC1 配置为备用 DNS 服务器。

-   [步骤5：配置 DC1](assetId:///205ca795-93ce-4e53-aa6b-b44c87f0e14a)。 使用其他 Active Directory 站点和其他安全组为 DC1 配置 Windows 7 客户端计算机。

-   [步骤6：安装并配置 2-DC1](assetId:///16752f61-edbf-4ff4-9d7a-e2077b66a127)。 在多站点部署中，你有两个或多个域和站点。 2-DC1 为 corp2.corp.contoso.com 域提供域控制器和 DNS 服务。

-   [步骤7：安装和配置 APP1](assetId:///7d04b54e-590a-4d33-9766-415789859f29)。 2-APP1 是2公司网络中的 web 和文件服务器。

-   [步骤8：配置 INET1](assetId:///8ecc0b63-8626-4939-8d26-3d51d051d231)。 本测试实验室指南中的 INET1 模拟 Internet。 必须配置可解析为 EDGE1 的公共 IP 地址的 DNS 条目。

-   [步骤9：配置 EDGE1](assetId:///562744dc-30f6-42fa-bd5f-60a013b2179e)。 在 EDGE1 上配置2公司网络 DNS 服务器和路由。

-   [步骤10：安装并配置 EDGE1](assetId:///1938c4f3-ca96-475d-9f2e-6bea3b7a4130)。 多站点部署中需要两个远程访问服务器。 2-EDGE1 为第二个域提供远程访问服务。

-   [步骤11：配置多站点部署](assetId:///537e4b68-043f-49c9-94d8-15ce8c4b18e2)。 配置两个远程访问服务器后，可以配置多站点部署。

-   [步骤12：测试 DirectAccess 连接](assetId:///aa293b5d-4b6f-4004-95f3-0ab54804b15c)。 通过 EDGE1 和 2-EDGE1 从 Internet 子网测试两个客户端计算机的 DirectAccess 连接。

-   [步骤13：从 NAT 设备后面测试 DirectAccess 连接](assetId:///41f8195b-00a1-4991-9db8-3703514dbe0c)。 从 NAT 设备后面测试 DirectAccess 连接。

-   [步骤14：快照配置](assetId:///7b56d5c9-c334-463e-9e29-d652ca110d84)。 完成测试实验室后，拍摄工作远程访问多站点部署的快照，以便稍后可以返回到测试其他方案。



