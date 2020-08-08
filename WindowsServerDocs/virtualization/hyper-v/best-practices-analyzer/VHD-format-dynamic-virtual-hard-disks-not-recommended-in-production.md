---
title: 对于在生产环境中运行服务器工作负荷的虚拟机，不建议使用 VHD 格式的动态虚拟硬盘
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 324a60a0-1d15-4ef2-9f17-23cbd2eb42ce
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 4865fcbc75ac135a6fe04622692aaf1ce2893a3a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87960250"
---
# <a name="vhd-format-dynamic-virtual-hard-disks-are-not-recommended-for-virtual-machines-that-run-server-workloads-in-a-production-environment"></a>对于在生产环境中运行服务器工作负荷的虚拟机，不建议使用 VHD 格式的动态虚拟硬盘

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>**问题**
*一台或多台虚拟机使用 VHD 格式动态扩展虚拟硬盘。*

## <a name="impact"></a>**影响**
*如果出现电源故障，则 VHD 格式的动态虚拟硬盘可能会出现一致性问题。如果物理磁盘在发生电源故障时要修改的 .vhd 文件中的扇区执行不完整或不正确的更新，则会发生一致性问题。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>**解决方法**
*关闭虚拟机并将 VHD 格式的动态虚拟硬盘转换为 VHDX 格式的虚拟硬盘或固定的虚拟硬盘。 (VHDX 格式具有可靠性机制，可帮助防止磁盘因系统电源故障而损坏 ) 。但是，如果在某个时间点可能将虚拟硬盘附加到早期版本的 Windows，请不要转换虚拟硬盘。Windows Server 2012 之前的 windows 版本不支持 VHDX 格式。*



