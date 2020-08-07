---
title: 当虚拟机使用差异虚拟硬盘时，请确保有足够的物理磁盘空间可用
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 71f99aab-f994-4022-9da0-d661965b95ac
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 9915d01408ec5d51cc70bcdf4682ebca5b4e5c32
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87950281"
---
# <a name="ensure-sufficient-physical-disk-space-is-available-when-virtual-machines-use-differencing-virtual-hard-disks"></a>当虚拟机使用差异虚拟硬盘时，请确保有足够的物理磁盘空间可用

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*一个或多个虚拟机正在使用差异虚拟硬盘。*

## <a name="impact"></a>影响
*差异虚拟硬盘需要主机卷上的可用空间，以便在写入虚拟硬盘时可以分配空间。如果可用空间已用完，则任何依赖于物理存储的虚拟机都可能会受到影响。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*监视可用磁盘空间，以确保有足够的空间可用于虚拟硬盘扩展。请考虑将差异虚拟硬盘合并到其父磁盘。在 Hyper-v 管理器中，检查差异磁盘以确定父虚拟硬盘。如果将差异磁盘合并到其他差异磁盘共享的父磁盘，则该操作将损坏其他差异磁盘和父磁盘之间的关系，使其不可用。验证父虚拟硬盘是否已共享后，可以使用 "编辑磁盘" 向导将差异磁盘合并到父虚拟硬盘。*



