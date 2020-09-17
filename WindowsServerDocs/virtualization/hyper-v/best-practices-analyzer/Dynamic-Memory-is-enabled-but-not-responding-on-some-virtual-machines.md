---
title: 动态内存已启用，但在某些虚拟机上未响应
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 91b7f50f-a071-4ab6-beb1-1b29f92f52b6
ms.date: 8/16/2016
ms.openlocfilehash: c826fc39637b3a7cf0f155065945d180bce5e4cb
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90744132"
---
# <a name="dynamic-memory-is-enabled-but-not-responding-on-some-virtual-machines"></a>动态内存已启用，但在某些虚拟机上未响应

>适用于：Windows Server 2016

有关最佳做法和扫描的详细信息，请参阅[运行最佳做法分析器扫描并管理扫描结果](https://go.microsoft.com/fwlink/p/?LinkID=223177)。

|属性|详细信息|
|-|-|
|**操作系统**|Windows Server 2016|
|**产品/功能**|Hyper-V|
|**严重性**|警告|
|**类别**|Configuration|

在以下部分中，"斜体" 指示在此问题的最佳做法分析器工具中出现的 UI 文本。

## <a name="issue"></a>问题
*一个或多个虚拟机遇到来宾操作系统中动态内存所需的驱动程序问题。*

## <a name="impact"></a>影响
*以下虚拟机中的来宾操作系统可能无法运行或可能运行 unreliably，因为 Hyper-v 无法动态调整内存以响应内存需求的更改。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*如果虚拟机正在启动，则这是预期的行为。如果虚拟机未启动，请确保将 integration services 升级到最新版本，并且来宾操作系统支持动态内存。*

从 Windows Server 2016，integration services 通过 Windows 更新提供。 确保将虚拟机配置为接收更新，以获取最新版本的 integration services。

动态内存适用于受支持来宾的特定版本。 请参阅 [hyper-v 动态内存概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831766(v=ws.11)) 版本低于 windows Server 2016 和 windows 10 的版本。