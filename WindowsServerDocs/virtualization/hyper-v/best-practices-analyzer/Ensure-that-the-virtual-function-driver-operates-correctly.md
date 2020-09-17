---
title: 在将虚拟机配置为使用 SR-IOV 时，请确保虚拟函数驱动程序正常运行
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: d21e4b93-29bf-423a-a635-71c6d48dc49e
ms.date: 8/16/2016
ms.openlocfilehash: 3be2f616ab8981e887688404f2907524f5f53e49
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746842"
---
# <a name="ensure-that-the-virtual-function-driver-operates-correctly-when-a-virtual-machine-is-configured-to-use-sr-iov"></a>在将虚拟机配置为使用 SR-IOV 时，请确保虚拟函数驱动程序正常运行

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*虚拟功能驱动程序在一个或多个虚拟机的来宾操作系统中运行不正常。*

## <a name="impact"></a>影响
*网络性能在以下虚拟机上不是最佳的：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*在来宾操作系统中，执行以下操作：验证是否安装了相应的驱动程序并启用了所有网络设备，并检查事件日志中是否存在错误或警告。*



