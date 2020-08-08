---
title: 避免在配置为 Active Directory 域控制器的计算机上安装 RemoteFX
description: 此最佳做法分析器规则文本的联机版本。
manager: dongill
ms.author: kathydav
ms.topic: article
ms.assetid: da58694e-91f6-45d8-a599-18966db165f4
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 5a5c2d23794ba2328da9a2a8c668a8525f6c6322
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87960670"
---
# <a name="avoid-installing-remotefx-on-a-computer-that-is-configured-as-an-active-directory-domain-controller"></a>避免在配置为 Active Directory 域控制器的计算机上安装 RemoteFX

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
*RemoteFX 安装在域控制器上。*

## <a name="impact"></a>**影响**
*无法在这些计算机上使用为 RemoteFX 配置的虚拟机。*

## <a name="resolution"></a>**解决方法**
*决定是要将此服务器配置为使用 RemoteFX 作为 Hyper-v 还是 Active Directory 域控制器，然后根据需要重新配置服务器。*



