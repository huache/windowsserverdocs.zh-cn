---
title: 为基于 VSS 的备份配置来宾操作系统，以便为 Hyper-v 副本启用应用程序一致性快照
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 7638e996-d42d-47b8-a670-1e09e7183850
ms.date: 8/16/2016
ms.openlocfilehash: b6a7eec504282e63e0cb24efbd2cdc5f66849005
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746882"
---
# <a name="configure-guest-operating-systems-for-vss-based-backups-to-enable-application-consistent-snapshots-for-hyper-v-replica"></a>为基于 VSS 的备份配置来宾操作系统，以便为 Hyper-v 副本启用应用程序一致性快照

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*与应用程序一致的快照要求在参与复制的虚拟机的来宾操作系统中启用并配置卷影复制服务 (VSS) 。*

## <a name="impact"></a>影响
*即使在复制配置中指定了应用程序一致的快照，Hyper-v 也不会使用它们，除非已配置 VSS。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*使用虚拟机连接在虚拟机中安装 integration services。*



