---
title: 配置希望副本虚拟机在故障转移时使用的故障转移 TCP/IP 设置
description: 此最佳做法分析器规则文本的联机版本。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.date: 8/16/2016
ms.openlocfilehash: a84d7e6c4e5366642ac559e397af4a267bf19be5
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745832"
---
# <a name="configure-the-failover-tcpip-settings-that-you-want-the-replica-virtual-machine-to-use-in-the-event-of-a-failover"></a>配置希望副本虚拟机在故障转移时使用的故障转移 TCP/IP 设置

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
*应将配置有静态 IP 地址的副本虚拟机配置为在故障转移时使用与主虚拟机副本不同的 IP 地址。*

## <a name="impact"></a>影响
*使用主虚拟机所支持的工作负荷的客户端可能无法在故障转移后连接到副本虚拟机。此外，主虚拟机的原始 IP 地址将在副本虚拟机网络拓扑中无效。这会影响以下虚拟机：*

\<list of virtual machines>

## <a name="resolution"></a>解决方法
*使用 Hyper-v 管理器配置副本虚拟机在故障转移时应使用的 IP 地址。*



