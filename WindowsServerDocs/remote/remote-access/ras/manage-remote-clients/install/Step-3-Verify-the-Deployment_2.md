---
title: 步骤3验证部署
description: 本主题是在 Windows Server 2016 中远程管理 DirectAccess 客户端的指南的一部分。
manager: brianlic
ms.topic: article
ms.assetid: 6a78a078-d2e7-4cbd-b8d5-20cfb6d1524b
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 7e8b7e037c0c98c62daf9abdf743ae4c1153f054
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87950842"
---
# <a name="step-3-verify-the-deployment"></a>步骤3验证部署

>适用于：Windows Server（半年频道）、Windows Server 2016

本主题介绍如何验证是否已正确配置部署，以便远程管理 DirectAccess 客户端。

### <a name="to-verify-proper-deployment"></a>验证部署是否正确

1.  将 DirectAccess 客户端计算机连接到公司网络并获取组策略的对象。

2.  在客户端计算机上，单击通知区域中的 "**网络连接**" 图标以访问 DirectAccess 媒体管理器。

3.  单击 " **DirectAccess 连接**"，你会看到状态为 "**本地连接**"。

4.  从公司网络中删除计算机，并将其连接到公共网络。

5.  在命令提示符下，键入 " **nltest/dsgetdc： [完全限定的域名]**"。 此命令将验证客户端是否可以访问公司网络。 如果域控制器不可访问，则以下错误消息将显示域不存在的报告： ERROR_NO_SUCH_DOMAIN。



