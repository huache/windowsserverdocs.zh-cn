---
title: 步骤3验证高级 DirectAccess 部署
description: 本主题是 "使用 Windows Server 2016 的高级设置部署单个 DirectAccess 服务器" 指南的一部分
manager: brianlic
ms.topic: article
ms.assetid: ae8bbff0-c981-4bc6-8df1-861621d0627f
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 3d5b189d70497ead26f24f43bba9dcfe2d443ce0
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87989764"
---
# <a name="step-3-verify-the-advanced-directaccess-deployment"></a>步骤3验证高级 DirectAccess 部署

>适用于：Windows Server（半年频道）、Windows Server 2016

本主题介绍如何验证是否已正确配置 DirectAccess 部署。

### <a name="to-verify-access-to-internal-resources-through-directaccess"></a>验证通过 DirectAccess 对内部资源进行的访问

1.  将 DirectAccess 客户端计算机连接到公司网络并获取组策略的对象。

2.  单击通知区域中的 "**网络连接**" 图标以访问 DirectAccess 媒体管理器。

3.  单击 " **DirectAccess 连接**"，你会看到状态为 "**本地连接**"。

4.  将客户端计算机连接到外部网络并尝试访问内部资源。

    你应能够访问所有公司资源。

## <a name="previous-step"></a><a name="BKMK_Links"></a>上一步

-   [步骤2：配置 DirectAccess 服务器](./da-adv-configure-s2-servers.md)