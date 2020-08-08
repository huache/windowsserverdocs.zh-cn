---
title: 向虚拟机提供所有可用的集成服务
description: 提供有关如何解决此最佳做法分析器规则报告的问题的说明。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 2c4b2043-ad81-495e-aa7a-467f813bb3d2
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: da2285bbdb19028c332e8ec886b143704493c95b
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954474"
---
# <a name="offer-all-available-integration-services-to-virtual-machines"></a>向虚拟机提供所有可用的集成服务

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*虚拟机上未启用一个或多个可用的 integration services。*

## <a name="impact"></a>影响

*某些功能将不可用于以下虚拟机：*

\<list of virtual machine names>

## <a name="resolution"></a>解决方法

*如果这是有意的，则无需执行其他操作。否则，请考虑在这些虚拟机的设置中提供所有 integration services。*

可以通过虚拟机设置来管理某些集成服务的可用性。

#### <a name="to-manage-the-availability-of-integration-services-to-a-virtual-machine"></a>管理将 integration services 用于虚拟机的可用性

1.  打开 Hyper-V 管理器。 单击 **“开始”**，指向 **“管理工具”**，然后单击 **“Hyper-V 管理器”**。

2.  在结果窗格中的 "**虚拟机**" 下，选择要配置的虚拟机。

3.  在 **“操作”** 窗格中的虚拟机名称下，单击 **“设置”**。

4.  在 "**管理**" 下，单击**Integration Services**。

5.  在 integration services 列表中，选中要提供给虚拟机的每个服务的复选框。 如果复选框不可用，则虚拟机中运行的来宾操作系统不支持该特定 integration services。



