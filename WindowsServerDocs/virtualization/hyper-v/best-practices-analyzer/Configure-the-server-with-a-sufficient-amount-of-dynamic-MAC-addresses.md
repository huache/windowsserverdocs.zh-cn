---
title: 将服务器配置为具有足够数量的动态 MAC 地址
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: a2804519-9790-4006-80b6-e990a8f505fe
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: b0416bb38e78f62bddf8a7937eb821ee0988286d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87968374"
---
# <a name="configure-the-server-with-a-sufficient-amount-of-dynamic-mac-addresses"></a>将服务器配置为具有足够数量的动态 MAC 地址

>适用于：Windows Server 2016

*本主题旨在解决最佳做法分析器扫描标识的特定问题。只应将本主题中的信息应用到运行 Hyper-v 最佳做法分析器的计算机上，并遇到本主题中所述的问题。有关最佳做法和扫描的详细信息，请参阅*[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*可用动态 MAC 地址的数目较低。*

## <a name="impact"></a>影响

*如果没有可用的动态 MAC 地址，则无法启动配置为使用动态 MAC 地址的虚拟机。*

## <a name="resolution"></a>解决方法

*使用 "虚拟交换机管理器" 查看和扩展动态地址范围。*



