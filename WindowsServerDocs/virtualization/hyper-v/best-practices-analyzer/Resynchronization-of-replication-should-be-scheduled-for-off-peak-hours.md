---
title: 应将复制的重新同步安排在非高峰时段
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 093a7bb7-8e0a-486b-b42b-04edd8809710
ms.date: 8/16/2016
ms.openlocfilehash: 97df7945988f117ed16d59685cc60841775737da
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746152"
---
# <a name="resynchronization-of-replication-should-be-scheduled-for-off-peak-hours"></a>应将复制的重新同步安排在非高峰时段

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Operations|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*不会将主虚拟机的复制重新同步安排在非高峰时段。*

## <a name="impact"></a>影响
*虚拟机处于需要重新同步的状态的时间越长，复制日志文件增长的时间越长，主虚拟机上发生的复制更改越多。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*使用 Hyper-v 管理器修改虚拟机的复制设置，以便在非高峰时段自动执行重新同步。*



