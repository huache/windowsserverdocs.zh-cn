---
title: 向虚拟机提供所有可用的集成服务
description: 提供有关如何解决此最佳做法分析器规则报告的问题的说明。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 2c4b2043-ad81-495e-aa7a-467f813bb3d2
ms.date: 8/16/2016
ms.openlocfilehash: 1343761ae9e0982d25133bd429218c8fe31aadbc
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746252"
---
# <a name="offer-all-available-integration-services-to-virtual-machines"></a>向虚拟机提供所有可用的集成服务

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

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

2.  在结果窗格中的 " **虚拟机**" 下，选择要配置的虚拟机。

3.  在 **“操作”** 窗格中的虚拟机名称下，单击 **“设置”**。

4.  在 " **管理**" 下，单击 **Integration Services**。

5.  在 integration services 列表中，选中要提供给虚拟机的每个服务的复选框。 如果复选框不可用，则虚拟机中运行的来宾操作系统不支持该特定 integration services。



