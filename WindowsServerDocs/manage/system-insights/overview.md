---
title: 系统见解概述
description: 系统见解是 Windows Server 2019 中的一种新的预测分析功能。 System Insights 预测功能-每个由机器学习模型提供支持的功能-在本地分析 Windows Server 系统数据（如性能计数器和事件），提供对服务器功能的见解，帮助你减少与被动相关的运营费用，从而管理部署中的问题。
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 5/23/2018
ms.openlocfilehash: 9bedd593cdd26b67e6e16ddea73955bb926a87a5
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87996679"
---
# <a name="system-insights-overview"></a>系统见解概述

>适用于：Windows Server 2019

系统见解是 Windows Server 2019 中的一种新的预测分析功能。 System Insights 预测功能-每个由机器学习模型提供支持的功能-在本地分析 Windows Server 系统数据（如性能计数器和事件），提供对服务器功能的见解，帮助你减少与被动相关的运营费用，从而管理部署中的问题。

在 Windows Server 2019 中，系统见解附带了四项默认功能，重点介绍容量预测，根据以前的使用模式预测计算、网络和存储的未来资源。 系统见解还附带了一个[可扩展的基础结构](adding-and-developing-capabilities.md)，因此，Microsoft 和第三方可以向系统见解添加新的预测功能，而无需更新操作系统。

你可以通过直观的[Windows 管理中心](../windows-admin-center/overview.md)扩展或[直接通过 PowerShell](https://aka.ms/SystemInsightsPowerShell)管理系统见解，使用 System Insights 可以根据部署的需求，单独配置每个预测功能。 所有预测结果都将发布到事件日志，这样您就可以使用[Azure Monitor](https://azure.microsoft.com/services/monitor/)或[System Center Operations Manager](/system-center/scom/welcome?view=sc-om-1807)轻松地聚合和查看一组计算机的预测。

![Windows 管理中心中的系统见解扩展，显示 CPU 容量预测功能，图形绘制了预测](media/cpu-forecast-2.png)

## <a name="local-functionality"></a>本地功能
系统见解完全在 Windows Server 上以本地方式运行。 使用 Windows Server 2019 中引入的新功能，可在计算机上直接收集、持久保存和分析所有数据，从而无需任何云连接即可实现预测分析功能。

系统数据存储在您的计算机上，这些数据由不需要在云中重新训练的预测功能进行分析。 通过系统见解，你可以将数据保留在计算机上，并且仍可以从预测分析功能中获益。

## <a name="get-started"></a>入门

<iframe src=https://www.youtube-nocookie.com/embed/AJxQkx5WSaA width=560 height=315 allowfullscreen></iframe>

>[!TIP]
>观看这些简短视频，了解入门和自信地管理系统见解所需的信息： [10 分钟内的系统见解](https://blogs.technet.microsoft.com/filecab/2018/07/24/getting-started-with-system-insights-in-10-minutes/)入门

### <a name="requirements"></a>要求
系统见解在任何 Windows Server 2019 实例上都可用。 它运行在主机和来宾计算机上、任何虚拟机监控程序和任何云中。

### <a name="install-system-insights"></a>安装系统见解
>[!IMPORTANT]
>系统见解在本地收集并存储一年的数据。 如果要在升级操作系统时保留数据，请**确保使用就地升级**。

#### <a name="install-the-feature"></a>安装此功能
可以使用 Windows 管理中心中的扩展安装系统见解：

![System Insights 扩展的第0天体验。](media/day-0-2.png)

还可以通过添加**System insights**功能，或使用 PowerShell 直接通过服务器管理器安装系统见解：

```PowerShell
Add-WindowsFeature System-Insights -IncludeManagementTools
```

## <a name="provide-feedback"></a>提供反馈
我们非常乐意听取你的反馈，帮助我们改进此功能。 你可以使用以下通道提交反馈：
- **反馈中心**：在 Windows 10 中使用反馈中心工具来提交 bug 或反馈。 执行此操作时，请指定：
    - **类别**：服务器
    - **子类别**：系统见解
- **Uservoice**：通过我们的[UserVoice 页面](https://windowsserver.uservoice.com/forums/295071-management-tools)提交功能请求。 与你的同事共享，投票赞成你对你很重要的项目。
- **电子邮件**：如果你想要私下向功能团队提交反馈，请向发送电子邮件 system-insights-feed@microsoft.com 。 请记住，我们仍可能会请求你使用反馈中心或 UserVoice。

## <a name="additional-references"></a>其他参考
若要了解有关系统见解的详细信息，请使用以下资源：

- [了解功能](understanding-capabilities.md)
- [管理功能](managing-capabilities.md)
- [添加和开发功能](adding-and-developing-capabilities.md)
- [系统见解常见问题解答](faq.md)