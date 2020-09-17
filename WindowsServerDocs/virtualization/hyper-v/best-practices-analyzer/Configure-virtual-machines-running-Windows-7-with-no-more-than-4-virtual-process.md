---
title: 配置运行 Windows 7 且不超过4个虚拟处理器的虚拟机
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 8fcf0868-b543-4f94-aee7-35324346da55
ms.date: 8/16/2016
ms.openlocfilehash: 09388f843e963252dfcaca1eb587778658b48039
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745762"
---
# <a name="configure-virtual-machines-running-windows-7-with-no-more-than-4-virtual-processors"></a>配置运行 Windows 7 且不超过4个虚拟处理器的虚拟机

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>**问题**
*为运行 Windows 7 的虚拟机配置了超过4个虚拟处理器。*

## <a name="impact"></a>**影响**
*Microsoft 不支持以下虚拟机的配置：*

\<list of virtual machines>

## <a name="resolution"></a>**解决方法**
*关闭虚拟机，并删除一个或多个虚拟处理器。*

#### <a name="to-remove-virtual-processors"></a>删除虚拟处理器

1.  打开 Hyper-V 管理器。 单击 **“开始”**，指向 **“管理工具”**，然后单击 **“Hyper-V 管理器”**。

2.  在结果窗格中的 " **虚拟机**" 下，选择要配置的虚拟机。 虚拟机的状态应列为 " **关**"。 如果不是，请右键单击该虚拟机，然后单击 " **关闭**"。

3.  在 **“操作”** 窗格中的虚拟机名称下，单击 **“设置”**。

4.  在导航窗格中，单击 " **处理器**"。

5.  在 " **处理器** " 页上，将处理器数设置为 **3** 或更少，然后单击 **"确定"**。



