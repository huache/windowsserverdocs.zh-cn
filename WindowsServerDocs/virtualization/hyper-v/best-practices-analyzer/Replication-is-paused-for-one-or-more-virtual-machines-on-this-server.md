---
title: 此服务器上的一个或多个虚拟机的复制已暂停
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: e1119a40-eda3-4058-8648-7df81cbc6c29
ms.date: 8/16/2016
ms.openlocfilehash: 3a2bf07e1f93aed3966dd98ce608af53168bdf9e
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746512"
---
# <a name="replication-is-paused-for-one-or-more-virtual-machines-on-this-server"></a>此服务器上的一个或多个虚拟机的复制已暂停

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
*一个或多个虚拟机的复制已暂停。在主虚拟机暂停的情况下，发生的任何更改都将累计，并将在恢复复制后发送到副本虚拟机。*

## <a name="impact"></a>影响
*只要复制已暂停，主虚拟机中发生的累积更改就会占用主服务器上的可用磁盘空间。在恢复复制后，可能会向副本服务器突发大量的网络流量。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*确认正在暂停复制。如果复制已暂停，无法处理磁盘空间不足或网络连接问题，请在解决这些问题后立即恢复复制。*



