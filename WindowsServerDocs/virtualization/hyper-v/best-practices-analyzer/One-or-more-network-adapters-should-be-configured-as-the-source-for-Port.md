---
title: 应将一个或多个网络适配器配置为端口镜像的源
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 147fd00f-1440-44d1-94e3-3a8af63aa7ed
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 1d5f355e4553d5d775152ed405729fa32c829acf
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954454"
---
# <a name="one-or-more-network-adapters-should-be-configured-as-the-source-for-port-mirroring"></a>应将一个或多个网络适配器配置为端口镜像的源

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
*一台或多台虚拟机的网络适配器配置为端口镜像的目标，但虚拟交换机上没有相应的源。*

## <a name="impact"></a>**影响**
*端口镜像不适用于以下虚拟交换机和虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>**解决方法**
*使用 Windows PowerShell 或 Hyper-v 管理器完成或更正端口镜像配置。*



