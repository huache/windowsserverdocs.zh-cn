---
title: 系统见解常见问题解答
description: 系统见解常见问题解答
ms.prod: windows-server
ms.technology: system-insights
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 5/23/2018
ms.openlocfilehash: 9d6ddd682def579796089266065be7d39ce361d1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856250"
---
# <a name="system-insights-faq"></a>系统见解常见问题解答

>适用于：Windows Server 2019

## <a name="how-can-you-use-system-insights-with-azure-monitor-or-system-center-operations-manager"></a>如何将系统见解用于 Azure Monitor 或 System Center Operations Manager？

[Azure Monitor](https://azure.microsoft.com/services/monitor/)和[System Center Operations Manager](https://docs.microsoft.com/system-center/scom/welcome?view=sc-om-1807)提供跨部署的操作信息，以帮助你管理基础结构。 与此相反，系统见解是一项 Windows Server 功能，它介绍了本地预测分析功能。 同时，系统见解和 Azure Monitor 或 SCOM 可帮助在整个设备中显示预测：

 Azure Monitor 或 SCOM 可以关闭由系统见解创建的事件，因为系统见解会将每个预测的结果输出到事件日志。 它们可在一组 Windows server 中显示这些特定于计算机的预测，使你能够在一组服务器实例中统一查看这些预测。 
 
 请参阅[此处](https://docs.microsoft.com/windows-server/manage/system-insights/managing-capabilities#retrieving-capability-results)每个预测的通道和事件 id。

## <a name="how-does-system-insights-relate-to-windows-ml"></a>系统见解如何与 Windows ML 关联？

[WINDOWS ML](https://docs.microsoft.com/windows/uwp/machine-learning/)是一种平台，使开发人员能够在 Windows 设备上导入和评分预先训练的机器学习模型。 这些模型受益于硬件加速，可在本地进行评分。 

系统见解是 Windows Server 2019 中的一项功能，它提供本地预测功能，同时提供完整的管理体验，包括 PowerShell 和 Windows 管理中心集成。 

## <a name="can-i-use-system-insights-for-my-cluster"></a>是否可以对群集使用系统见解？ 

可以。 系统见解可以独立运行在每个故障转移群集节点上，并且可以在本地存储、卷、CPU 和网络之间独立使用系统 Insights 预测的默认行为。 **你还可以启用群集存储的预测**，以便预测群集卷和存储的使用情况。 

你可以在 Windows 管理中心或 PowerShell 中管理这些设置，[此处](https://blogs.technet.microsoft.com/filecab/2018/10/03/using-system-insights-to-forecast-clustered-storage-usage/)提供了有关此功能的更多详细信息。
 

## <a name="how-expensive-is-it-to-run-the-default-capabilities"></a>运行默认功能的成本是多少？

每个默认功能的运行成本都很低。 收集更多数据时，每个功能运行所需的时间更长，但通常只需几秒钟即可完成。 

## <a name="see-also"></a>另请参阅
若要了解有关系统见解的详细信息，请使用以下资源：

- [系统见解概述](overview.md)
- [了解功能](understanding-capabilities.md)
- [管理功能](managing-capabilities.md)
- [添加和开发功能](adding-and-developing-capabilities.md)
