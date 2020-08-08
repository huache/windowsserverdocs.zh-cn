---
title: 使用提供纠错功能的 RAM
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: 67eb6cef-b045-4748-90e1-406af5345d6a
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 1f89ceb20cbd58260f103b244be80c9d8c292d93
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87960330"
---
# <a name="use-ram-that-provides-error-correction"></a>使用提供纠错功能的 RAM

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|错误|
|**类别**|配置|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题

*此计算机上使用的 RAM 不 (ECC) RAM 进行错误更正。*

## <a name="impact"></a>影响

*Microsoft 不支持计算机上的 Windows Server 2016，并且不会纠正 RAM。*

## <a name="resolution"></a>解决方法

*验证服务器是否已列在 Windows Server 目录中并可用于 Hyper-v。*

若要检查是否列出了服务器，请参阅[Windows server 目录](https://www.windowsservercatalog.com/)。



