---
ms.assetid: 72a90d00-56ee-48a9-9fae-64cbad29556c
title: Windows Server 2016 精确时间
description: Windows Server 2016 中的时间同步准确度已显著提高，同时保持早期 Windows 版本的完全向后 NTP 兼容性。
author: shortpatti
ms.author: dacuo
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: 2e8e9e86f81596c85219c37c07d8fd2e95cc3a49
ms.sourcegitcommit: 10331ff4f74bac50e208ba8ec8a63d10cfa768cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953079"
---
# <a name="accurate-time-for-windows-server-2016"></a>Windows Server 2016 精确时间

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows 10 或更高版本

Windows 时间服务是一个组件，它为客户端和服务器时间同步提供程序使用插件模型。  Windows 上有两个内置的客户端提供程序，并且有可用的第三方插件。 一种提供程序使用 [NTP (RFC 1305)](https://tools.ietf.org/html/rfc1305) 或 [MS-NTP](https://msdn.microsoft.com/library/cc246877.aspx) 将本地系统时间同步到与 NTP 和/或 MS-NTP 兼容的引用服务器。 另一个提供程序用于 Hyper-V，可将虚拟机 (VM) 同步到 Hyper-V 主机。  存在多个提供程序时，Windows 将首先使用层次级别（依次为根延迟、根分散和时间偏移）选择最佳提供程序。

> [!NOTE]
> 若要快速了解 Windows 时间服务，请参阅此[高级概述视频](https://aka.ms/WS2016TimeVideo)。

在本主题中，我们将讨论这些主题，因为它们与实现准确时间相关： 

- 改进
- 度量
- 最佳方案

> [!IMPORTANT]
> 可在[此处](https://windocs.blob.core.windows.net/windocs/WindowsTimeSyncAccuracy_Addendum.pdf)下载“Windows 2016 精确确时间”一文引用的附录。  本文档提供了有关测试和度量方法的更多详细信息。

> [!NOTE] 
> Windows 时间提供程序插件模型[记录在 TechNet 上](https://msdn.microsoft.com/library/windows/desktop/ms725475%28v=vs.85%29.aspx)。

## <a name="domain-hierarchy"></a>域层次结构
域和独立配置的工作方式不同。

- 域成员使用安全 NTP 协议，该协议使用身份验证来确保时间引用的安全性和真实性。  域成员与域层次结构和评分系统所确定的主时钟同步。  在域中，存在时间层次的层次结构层，因此每个 DC 指向具有更准确时间层的父级 DC。  层次结构解析为根林中的 PDC 或 DC，或具有 GTIMESERV 域标志的 DC，后者表示域的良好时间服务器。  请参阅下面的 [使用 GTIMESERV 指定本地可靠时间服务部分。

- 独立计算机默认配置为使用 time.windows.com。  此名称由 DNS 服务器解析，该服务器应指向 Microsoft 拥有的资源。  与所有远程定位的时间引用一样，网络中断可能会阻止同步。  网络流量负载和非对称网络路径可能会降低时间同步的准确度。  若要实现 1 毫秒的准确度，不能依赖于远程时间源。

由于 Hyper-V 来宾将至少有两个 Windows 时间提供程序（主机时间和 NTP）可供选择，因此在作为来宾运行时，可能会看到域或独立的不同行为。

> [!NOTE] 
> 有关域层次结构和评分系统的详细信息，请参阅[“什么是 Windows 时间服务？”](https://blogs.msdn.microsoft.com/w32time/2007/07/07/what-is-windows-time-service/) 博客文章。

> [!NOTE]
> 层次是 NTP 和 Hyper-V 提供程序中使用的概念，其值指示层次结构中的时钟位置。  第 1 层保留给最高级别时钟，而第 0 层保留给假定为准确的硬件，并且与之相关联的延迟很少或者没有。  第 2 层与第 1 层服务器通信，第 3 层与第 2 层通信，依此类推。  虽然较低的层通常指示更准确的时钟，但仍有可能发现差异。  此外，W32time 仅接受第 15 层或以下层的时间。  若要查看客户端的层次，请使用 w32tm /query /status  。

## <a name="critical-factors-for-accurate-time"></a>准确时间的关键因素
在每种情况下，对于准确的时间，有三个关键因素：

1. **固态的源时钟** - 域中的源时钟必须稳定且准确。 这通常意味着安装 GPS 设备或指向第 1 层源，从而考虑 #3。 比如说，如果水上有两艘船，并且你尝试测量一艘船的高度，与另一艘相比较，则在源船非常稳定且不移动的情况下，准确度最高。 对于时间也是如此，并且如果源时钟不稳定，则同步时钟的整个链会受到影响，并在每个阶段进行放大。 它还必须是可访问的，因为连接中断会干扰时间同步。 最后，该方法必须是安全的。 如果未正确维护时间引用，或者可能由恶意方操作，则你的域可能会受到基于时间的攻击。
2. **稳定的客户端时钟** - 稳定的客户端时钟可确保振荡器的自然偏移为可控制的。  NTP 使用可能来自多个 NTP 服务器的多个示例，来调节和管理本地计算机时钟。  它不会执行时间更改，但是会减缓或加快本地时钟的速度，以便快速接近准确的时间，并在 NTP 请求之间保持准确。  然而，如果客户端计算机时钟的振荡器不稳定，则在调整之间可能会发生更多波动，并且 Windows 用于调节时钟的算法无法准确工作。  在某些情况下，可能需要更新固件才能获得准确的时间。
3. **对称 NTP 通信** - 用于 NTP 通信的连接是对称的，这一点非常重要。  NTP 使用计算来调整假设网络修补程序对称的时间。  如果 NTP 包进入服务器的路径需要不同的时间来返回，则准确度会受到影响。  例如，由于网络拓扑发生更改，或者通过具有不同接口速度的设备路由数据包，该路径可能会更改。

对于电池供电的设备，无论是移动的还是便携式的，都必须考虑不同的策略。  根据我们的建议，若要保持准确的时间，需要每秒管理一次时钟，这与时钟更新频率相关。 这些设置将消耗比预期更多的电池电量，并可能干扰 Windows 中为此类设备提供的省电模式。 电池供电的设备还具有特定的电源模式，这些模式会阻止所有应用程序运行，这会干扰 W32time 管理时钟和保持时间准确的能力。 此外，移动设备中的时钟在开始时可能并不太准确。  环境条件会影响时钟准确性，移动设备可以从一个环境条件转到下一个环境条件，这可能会干扰其保持时间准确的能力。  因此，Microsoft 不建议设置具有高准确度设置的电池供电的便携设备。 

## <a name="why-is-time-important"></a>为什么时间很重要？  
出于许多不同的原因，你需要准确的时间。  Windows 的典型情况是 Kerberos，其要求客户端和服务器之间精确到 5 分钟。  但是，还有许多其他区域会受到时间准确度的影响，其中包括：


- 政府法规，如：
    - 美国 FINRA 要求精确到 50 毫秒
    - 欧盟 ESMA (MiFID II) 要求精确到 1 毫秒。
- 加密算法
- 群集/SQL/Exchange 和文档数据库等分布式系统
- 比特币交易的区块链框架
- 分布式日志和威胁分析 
- AD 复制
- PCI（支付卡行业），当前准确度为 1 秒钟



[!INCLUDE [windows-server-2016-improvements](windows-server-2016-improvements.md)]
