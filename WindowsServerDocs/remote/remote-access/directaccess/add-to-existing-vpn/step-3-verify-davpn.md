---
title: 步骤3验证 (VPN) 部署的远程访问
description: 本主题是有关 Windows Server 2016 的将 DirectAccess 添加到现有远程访问 (VPN) 部署的指南的一部分
manager: brianlic
ms.topic: article
ms.assetid: 43ac612e-2e77-418c-8171-ebb2086b7cb6
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 9da14f076f177e7e819c1529f9de647b5dde0500
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969214"
---
# <a name="step-3-verify-the-remote-access-vpn-deployment"></a>步骤3验证 (VPN) 部署的远程访问

>适用于：Windows Server（半年频道）、Windows Server 2016

本主题介绍如何验证是否已正确配置 DirectAccess 部署。

### <a name="to-verify-access-to-internal-resources-through-directaccess"></a>验证通过 DirectAccess 对内部资源进行的访问

1.  将 DirectAccess 客户端计算机连接到公司网络并获取组策略。

2.  单击通知区域中的“网络连接”**** 图标以访问 DA 媒体管理器。

3.  单击“DirectAccess 连接”****，你会看到状态是“本地连接”****。

4.  将客户端计算机连接到外部网络并尝试访问内部资源。

    你应能够访问所有公司资源。



