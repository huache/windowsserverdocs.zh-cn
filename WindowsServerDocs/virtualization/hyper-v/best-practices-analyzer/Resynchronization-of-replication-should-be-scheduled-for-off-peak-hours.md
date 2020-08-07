---
title: 应将复制的重新同步安排在非高峰时段
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 093a7bb7-8e0a-486b-b42b-04edd8809710
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: dad983e19df328946f3bd7ec59f68ee3e9f8bfcc
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939003"
---
# <a name="resynchronization-of-replication-should-be-scheduled-for-off-peak-hours"></a>应将复制的重新同步安排在非高峰时段

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|操作|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*不会将主虚拟机的复制重新同步安排在非高峰时段。*

## <a name="impact"></a>影响
*虚拟机处于需要重新同步的状态的时间越长，复制日志文件增长的时间越长，主虚拟机上发生的复制更改越多。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*使用 Hyper-v 管理器修改虚拟机的复制设置，以便在非高峰时段自动执行重新同步。*



