---
title: 用于实时迁移通信的所有网络应具有至少 1 Gbps 的链接速度
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 89411b63-bec8-463d-b486-107548ed440e
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: aa341f1e1aed05684020fa1028902839bc1e412d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87948610"
---
# <a name="all-networks-for-live-migration-traffic-should-have-a-link-speed-of-at-least-1-gbps"></a>用于实时迁移通信的所有网络应具有至少 1 Gbps 的链接速度

>适用于：Windows Server 2016



|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*用于实时迁移通信的网络没有至少有 1 Gbps 的链接速度。*

## <a name="impact"></a>影响
*实时迁移可能会慢慢地发生，这可能会因为 TCP 连接超时而中断网络连接。*

## <a name="resolution"></a>解决方法
*至少配置一个速度为 1 Gbps 或更快的实时迁移网络。*

请参阅网络硬件供应商提供的文档，以了解你的现有网络适配器是否可以支持至少 1 Gbps 的链接速度。



