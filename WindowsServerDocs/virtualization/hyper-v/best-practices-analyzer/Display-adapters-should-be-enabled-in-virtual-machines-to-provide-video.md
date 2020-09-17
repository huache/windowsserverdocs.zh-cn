---
title: 应在虚拟机中启用显示适配器以提供视频功能
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: ac5992e6-3c0b-46c2-a48e-6ef37b679228
ms.date: 8/16/2016
ms.openlocfilehash: 0c51100a55ab6780c83dc95404e92275a1898da6
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90744022"
---
# <a name="display-adapters-should-be-enabled-in-virtual-machines-to-provide-video-capabilities"></a>应在虚拟机中启用显示适配器以提供视频功能

>适用于：Windows Server 2016



有关*最佳做法和扫描的详细信息，请参阅*[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*Microsoft 虚拟机总线视频设备可能在虚拟机中处于禁用状态。*

Microsoft 虚拟机总线视频设备是一种优化了用于 Hyper-v 虚拟机的虚拟视频适配器。 如果未将虚拟机配置为使用 Microsoft 虚拟机总线视频设备，将使用旧的视频适配器。 Microsoft 虚拟机总线视频设备的性能优于传统的视频适配器。

## <a name="impact"></a>影响

*以下虚拟机的视频性能将会降级：*

\<list of virtual machine names>

## <a name="resolution"></a>解决方法

*使用来宾操作系统中的设备管理器来启用 Microsoft 虚拟机总线视频设备。*

使用设备管理器所需的步骤因操作系统而异。 有关说明，请参阅来宾操作系统中的帮助。



