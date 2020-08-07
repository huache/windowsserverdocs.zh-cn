---
title: 虚拟交换机上的 PVLAN 配置必须一致
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 4db63bcc-7a54-4f19-98a6-c274c3956d51
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 63780266fa23187e12bfd5d503a1f3c0306bc364
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939024"
---
# <a name="pvlan-configuration-on-a-virtual-switch-must-be-consistent"></a>虚拟交换机上的 PVLAN 配置必须一致

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>**问题**
*在一个或多个虚拟网络适配器上未正确配置专用虚拟局域网 (PVLAN) 。*

## <a name="impact"></a>**影响**
*PVLAN 可能无法正确隔离虚拟机之间的网络流量。*

## <a name="resolution"></a>**解决方法**
*使用 Windows PowerShell cmdlet Set-vmnetworkadaptervlan 来正确配置 PVLAN。*



