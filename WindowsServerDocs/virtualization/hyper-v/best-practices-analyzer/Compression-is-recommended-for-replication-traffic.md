---
title: 建议对复制通信使用压缩
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: cf8be6e9-2909-4e4a-bb63-d1e1ebbc6930
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 2184a2ec0441af7fdbfc7566d783bee82f6bbbb9
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954524"
---
# <a name="compression-is-recommended-for-replication-traffic"></a>建议对复制通信使用压缩

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*通过网络从主服务器发送到副本服务器的复制流量未压缩。*

## <a name="impact"></a>影响
*复制流量将使用比所需的更多的带宽。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*配置 Hyper-v 副本以压缩 hyper-v 管理器中虚拟机的设置中通过网络传输的数据。你还可以使用 Hyper-v 之外的工具来执行压缩。*



