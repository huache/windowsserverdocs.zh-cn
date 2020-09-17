---
title: 应至少每月执行一次测试故障转移，以验证故障转移是否成功，以及虚拟机工作负荷在故障转移后是否按预期运行
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 57a8aa50-e59e-4a4b-8571-1099d5a8eee4
ms.date: 8/16/2016
ms.openlocfilehash: 4ec97d55f1a6caf33b1b46d0a6bdb4e99005c971
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90744090"
---
# <a name="test-failovers-should-be-carried-out-at-least-monthly-to-verify-that-failover-will-succeed-and-that-virtual-machine-workloads-will-operate-as-expected-after-failover"></a>应至少每月执行一次测试故障转移，以验证故障转移是否成功，以及虚拟机工作负荷在故障转移后是否按预期运行

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
*至少一个月内没有任何测试性故障转移。*

## <a name="impact"></a>影响
*未确认计划内或计划外故障转移将成功，或在故障转移后工作负荷操作将正确继续。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*使用 Hyper-v 管理器进行测试故障转移。*



