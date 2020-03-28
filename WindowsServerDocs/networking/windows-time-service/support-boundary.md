---
ms.assetid: ''
title: 高精度时间的支持边界
description: 本文介绍用于需要高度准确和稳定系统时间的环境中的 Windows 时间 (W32Time) 服务的支持边界。
author: eross-msft
ms.author: dacuo
manager: dougkim
ms.date: 10/17/2018
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: 5748d598272c8f096876bab0d24142d38c2fd64b
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314966"
---
# <a name="support-boundary-for-high-accuracy-time"></a>高精度时间的支持边界

>适用于：Windows Server 2016 和 Windows 10 版本 1607 或更高版本

本文介绍 Windows 时间服务 (W32Time) 在需要高度准确和稳定系统时间的环境中的支持边界。

## <a name="high-accuracy-support-for-windows-81-and-2012-r2-or-prior"></a>面向 Windows 8.1 和 2012 R2（或更早版本）的高精度支持

Windows 的早期版本（Windows 10 1607 或 Windows Server 2016 1607 之前的版本）无法保证时间的高度精确。 这些系统上的 Windows 时间服务：

-   提供了满足 Kerberos 版本 5 身份验证要求所需的时间精度

-   为加入到公共 Active Directory 林的 Windows 客户端和服务器提供了大致准确的时间

在这些操作系统上，更严格的精度要求超出了 Windows 时间服务的设计规范，因此不受支持。

## <a name="windows-10-and-windows-server-2016"></a>Windows 10 和 Windows Server 2016

Windows 10 和 Windows Server 2016 中的时间精度已显著改善，同时保持早期 Windows 版本的完全后向 NTP 兼容性。 在正确的操作条件下，运行 Windows 10 或 Windows Server 2016 及更高版本的系统可以提供 1 秒、50 ms（毫秒）或 1 ms 的精度。

>[!IMPORTANT]
>**高度准确的时间源**<br>
>拓扑中的生成时间精度在很大程度上取决于使用准确、稳定的根（层次 1）时间源。 有第三方供应商出售基于 Windows 和非基于 Windows 的高精度且与 Windows 兼容的 NTP 时间源硬件。 请向供应商核实其产品的时间精度。

>[!IMPORTANT]
>**时间精度**<br>
>时间精度需要准确时间从高度准确的权威时间源到终端设备进行端到端分布。 引入网络不对称性的任何因素都将对精度产生负面影响，例如物理网络设备或目标系统上的高 CPU 负载。

## <a name="high-accuracy-requirements"></a>高精度要求

本文档的其余部分概述了支持相应的高精度目标所必须满足的环境要求。

### <a name="target-accuracy-1-second-1s"></a>目标精度：1 秒 (1 s)

若要相较于高度精确的时间源使特定目标计算机的达到 1 s 精度：

-   目标系统必须运行 Windows 10、Windows Server 2016。

-   目标系统必须从时间服务器的 NTP 层次结构同步时间，最终形成高度精确的、与 Windows 兼容的 NTP 时间源。

-   上述 NTP 层次结构中的所有 Windows 操作系统都必须按照[配置系统以实现高精度](configuring-systems-for-high-accuracy.md)文档中所述进行配置。

-   目标和源之间的累积单向网络延迟不能超过 100 ms。 累计网络延迟的计算方法为：将层次结构（从目标开始，到源结束）中的 NTP 客户端 - 服务器节点对之间的各个单向延迟进行相加。 有关详细信息，请查看高精度时间同步文档。

### <a name="target-accuracy-50-milliseconds"></a>目标精度：50 毫秒

“目标精度：1 秒”部分中概述的所有要求均适用，  但此部分中概述的更严格的控制部分除外。

特定目标系统达到 50 ms 精度的其他要求包括：

-   目标计算机的时间源之间的网络延迟必须优于 5 ms。

-   目标系统距高度准确的时间源不得超过层次 5

    >[!Note]
    >从命令行运行“w32tm /query /status”以查看层次。

-   目标系统必须在距高度准确的时间源的 6 个或更少网络跃点范围内

-   所有层次的一天平均 CPU 使用率不得超过 90%

-   对于虚拟化系统，主机的一天平均 CPU 使用率不得超过 90%

### <a name="target-accuracy-1-millisecond"></a>目标精度：1 毫秒

“目标精度：1 秒”和“目标精度：50 毫秒”部分  中概述的所有要求均适用，  但本部分中概述的更严格的控制部分除外。

特定目标系统实现 1 ms 精度的其他要求包括：

-   目标计算机的时间源之间的网络延迟必须优于 0.1 ms

-   目标系统距高度准确的时间源不得超过层次 5

    >[!Note]
    >从命令行运行 `w32tm /query /status' 查看层次

-   目标系统必须在距高度准确的时间源的 4 个或更少网络跃点范围内

-   每个层次的一天平均 CPU 使用率不得超过 80%

-   对于虚拟化系统，主机的一天平均 CPU 使用率不得超过 80%
