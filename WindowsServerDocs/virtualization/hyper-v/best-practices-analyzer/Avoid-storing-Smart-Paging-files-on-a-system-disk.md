---
title: 避免在系统磁盘上存储智能分页文件
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 9b57c9b8-76c5-43c7-bfa6-2c95b3cb6510
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 5ac7f8c9f6fb2edf2f6550cede9adfdc5be321f6
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87946070"
---
# <a name="avoid-storing-smart-paging-files-on-a-system-disk"></a>避免在系统磁盘上存储智能分页文件

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|操作|

在以下部分中，斜体表示在此问题的最佳做法分析器工具中出现的文本。

## <a name="issue"></a>问题
*如果重新启动虚拟机，并且智能分页文件的指定位置是运行 Hyper-v 的服务器的系统磁盘，则一个或多个虚拟机的内存配置可能需要使用智能分页。*

## <a name="impact"></a>影响
*使用系统磁盘进行智能分页可能会导致运行 Hyper-v 的服务器遇到问题。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*重新配置虚拟机，以在非系统磁盘上存储智能分页文件。*



