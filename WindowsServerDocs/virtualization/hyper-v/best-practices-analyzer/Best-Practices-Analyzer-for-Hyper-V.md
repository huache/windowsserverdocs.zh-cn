---
title: Hyper-v 最佳做法分析器
description: 此最佳做法分析器规则文本的联机版本。
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 3747faa5-6e9f-499e-8a79-3fb9d73b6b92
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: d4a2fb889aa13bc945a38a3d879ee013769fabca
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857690"
---
# <a name="best-practices-analyzer-for-hyper-v"></a>Hyper-v 最佳做法分析器

>适用于：Windows Server 2016
  
在 Windows 管理中，*最佳做法*是在通常情况下由专家定义为配置服务器的理想方式的指南。 最佳做法违规，甚至是关键违规，可能不会导致问题。 但是，它们可以表示服务器配置，这可能会导致性能不佳、可靠性差、意外冲突、安全风险增加或其他潜在问题。  
  
最佳做法分析器使用基于这些最佳实践的规则扫描计算机，并报告结果。 每个最佳实践规则都包含有关如何符合规则的详细信息。 本部分介绍了这些规则，这些规则可帮助你了解适用于 Hyper-v 的最佳做法，并在扫描发现不符合最佳做法的条件时解释结果。  
  
有关最佳做法分析器和扫描的详细信息，请参阅[最佳做法分析器](https://go.microsoft.com/fwlink/?LinkId=122786)。  
  
## <a name="about-hyper-v"></a>关于 Hyper-V  
Hyper-v 允许你在一台物理计算机上同时运行多个操作系统，方法是在虚拟机中运行每个操作系统。 虚拟机有助于更有效、更灵活地使用计算资源。 有关 Hyper-v 的详细信息，请参阅[Windows Server 2016 上的 hyper-v](../Hyper-V-on-Windows-Server.md)。  
  


