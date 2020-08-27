---
ms.assetid: 7dd905ea-4235-4519-8400-31b4fa0ed1bf
title: 启用客户端查找下一个最近的域控制器
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/08/2018
ms.topic: article
ms.openlocfilehash: 1a6b3fcd5b790546539adfa2c46ad6f826984984
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88939227"
---
# <a name="enabling-clients-to-locate-the-next-closest-domain-controller"></a>启用客户端查找下一个最近的域控制器

> 适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

如果你有运行 Windows Server 2008 或更高版本的域控制器，则可以通过启用 " **尝试下一个最近的站点** " 组策略设置，使运行 windows Vista 或更高版本或 Windows Server 2008 或更高版本的客户端计算机更有效地查找域控制器。 此设置可帮助简化网络流量，尤其是在具有很多分支机构和站点的大型企业中，此设置可改善域控制器定位器 (DC 定位程序) 。

此新设置可能会影响站点链接开销的配置方式，因为它会影响域控制器的位置顺序。 对于具有多个中心站点和分支机构的企业，你可以通过确保客户端在最近的中心站点中找不到域控制器时故障转移到下一个最近的中心站点来大幅减少网络上的 Active Directory 流量。

一般来说，如果启用 " **尝试下一个最近的站点** " 设置，应尽可能简化站点拓扑和站点链接成本。 在具有多个中心站点的企业中，这可以简化在处理情况（其中一个站点中的客户端需要故障转移到另一个站点中的域控制器）时所做的任何计划。

默认情况下，" **尝试下一个最近的站点** " 设置未启用。 如果未启用该设置，DC 定位符将使用以下算法查找域控制器：

- 尝试在同一站点中查找域控制器。
- 如果同一站点中没有可用的域控制器，请尝试在域中查找任何域控制器。

> [!NOTE]
> 这是在早期版本的 Active Directory 中使用 DC 定位符的算法。 有关详细信息，请参阅文章 [DNS 支持 Active Directory 的工作原理](/previous-versions/windows/it-pro/windows-server-2003/cc759550(v=ws.10))。

如果启用 " **尝试下一个最近的站点** " 设置，DC 定位符将使用以下算法查找域控制器：

- 尝试在同一站点中查找域控制器。
- 如果同一站点中没有可用的域控制器，请尝试在下一个最近的站点中查找域控制器。 如果站点的站点链接开销低于站点链接开销较高的其他站点，则站点会更接近。
- 如果下一个最近的站点中没有可用的域控制器，请尝试在域中查找任何域控制器。

" **尝试下一个最近的站点** " 设置与自动站点覆盖协调工作。 例如，如果下一个最近的站点没有域控制器，DC 定位程序将尝试查找为该站点执行自动站点覆盖的域控制器。

默认情况下，DC 定位程序不会将任何包含只读域控制器的站点视为 (RODC) 确定下一个最近的站点。 此外，当客户端从运行早于 Windows Server 2008 的版本的域控制器获得响应时，DC 定位器行为与 "未启用时" 设置相同。

例如，假设站点拓扑具有四个站点，下图中的站点链接值为。 在此示例中，所有域控制器都是运行 Windows Server 2008 或更高版本的可写域控制器。

![允许客户端查找 dc](media/Enabling-Clients-to-Locate-the-Next-Closest-Domain-Controller/beff4087-fb2a-463b-96ac-d440a9e29b75.gif)

在此示例中，如果 " **尝试下一个最近的站点** 组策略设置已启用，则在 Site_B 中的客户端计算机尝试查找域控制器时，它将首先尝试在其自己的 Site_B 中查找域控制器。 如果 Site_B 中没有可用的，它会尝试查找 Site_A 中的域控制器。

如果未启用该设置，则在 Site_B 中没有域控制器的情况下，客户端会尝试查找 Site_A、Site_C 或 Site_D 中的域控制器。

> [!NOTE]
> " **尝试下一个最近的站点** " 设置与自动站点覆盖协调工作。 例如，如果下一个最近的站点没有域控制器，DC 定位程序将尝试查找为该站点执行自动站点覆盖的域控制器。

若要应用 " **尝试下一个最近的站点** " 设置，你可以创建一个组策略对象 (GPO) ，并将其链接到你的组织的适当对象，或者，你可以修改默认域策略，使其影响域中运行 windows Vista 或更高版本以及 windows Server 2008 或更高版本的所有客户端。 有关如何设置 " **尝试下一个最近的站点** " 设置的详细信息，请参阅 [使客户端能够在下一个最近的站点中找到域控制器](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc772592(v=ws.10))。
