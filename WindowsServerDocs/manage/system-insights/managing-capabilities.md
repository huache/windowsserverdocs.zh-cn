---
title: 管理功能
description: 系统见解公开了可为每个功能配置的各种设置，可以对这些设置进行调整以满足部署的特定需求。 本主题介绍如何通过 Windows 管理中心或 PowerShell 管理每项功能的各种设置，提供基本 PowerShell 示例和 Windows 管理中心屏幕截图，演示如何调整这些设置。
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 6/05/2018
ms.openlocfilehash: e82b27d2d746592b29b86a66ee34b21f8605a0d8
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87940158"
---
# <a name="managing-capabilities"></a>管理功能

>适用于：Windows Server 2019

在 Windows Server 2019 中，系统见解公开了可以为每个功能配置的各种设置，并且这些设置可以进行调整以满足你的部署的特定需要。 本主题介绍如何通过 Windows 管理中心或 PowerShell 管理每项功能的各种设置，提供基本 PowerShell 示例和 Windows 管理中心屏幕截图，演示如何调整这些设置。

>[!TIP]
>你还可以使用这些简短视频来帮助你开始使用并自信地管理系统见解：[在10分钟内开始使用系统见解](https://blogs.technet.microsoft.com/filecab/2018/07/24/getting-started-with-system-insights-in-10-minutes/)

虽然本部分提供了 PowerShell 示例，但你可以使用[系统见解 PowerShell 文档](https://aka.ms/systeminsightspowershell)来查看系统见解中的所有 cmdlet、参数和参数集。

## <a name="viewing-capabilities"></a>查看功能

若要开始，可以使用**InsightsCapability** cmdlet 列出所有可用的功能：

```PowerShell
Get-InsightsCapability
```
这些功能也可以在系统见解扩展中看到：

![列出可用功能的系统见解概述页](media/overview-page-contoso.png)

## <a name="enabling-and-disabling-a-capability"></a>启用和禁用功能
每个功能都可以启用或禁用。 禁用某项功能可防止调用此功能; 对于非默认功能，禁用该功能将停止对该功能的所有数据收集。 默认情况下，所有功能均已启用，你可以使用**InsightsCapability** cmdlet 检查功能的状态。

若要启用或禁用功能，请使用**InsightsCapability**和**InsightsCapability** cmdlet：

```PowerShell
Enable-InsightsCapability -Name "CPU capacity forecasting"
Disable-InsightsCapability -Name "Networking capacity forecasting"
```
还可以通过在 Windows 管理中心中选择一项功能，单击 "**启用**" 或 "**禁用**" 按钮来切换这些设置。

### <a name="invoking-a-capability"></a>调用功能
调用功能可立即运行检索预测的功能，管理员可以随时通过单击 Windows 管理中心中的 "**调用**" 按钮或使用**InsightsCapability** cmdlet 来调用功能：

```PowerShell
Invoke-InsightsCapability -Name "CPU capacity forecasting"
```

>[!TIP]
>若要确保调用某个功能不与计算机上的关键操作冲突，请考虑在非工作时间计划预测。

## <a name="retrieving-capability-results"></a>检索功能结果
一旦调用功能，最新结果就会使用**InsightsCapability**或**InsightsCapabilityResult**。 这些 cmdlet 输出每个功能的最新**状态**和**状态说明**，这些说明描述每个预测的结果。 "**状态**" 和 "**状态说明**" 字段将在 "[了解功能" 文档](understanding-capabilities.md)中进一步说明。

此外，还可以使用**InsightsCapabilityResult** cmdlet 查看最后30个预测结果，并检索与预测关联的数据：

```PowerShell
# Specify the History parameter to see the last 30 prediction results.
Get-InsightsCapabilityResult -Name "CPU capacity forecasting" -History

# Use the Output field to locate and then show the results of "CPU capacity forecasting."
# Specify the encoding as UTF8, so that Get-Content correctly parses non-English characters.
$Output = Get-Content (Get-InsightsCapabilityResult -Name "CPU capacity forecasting").Output -Encoding UTF8 | ConvertFrom-Json
$Output.ForecastingResults
```
系统见解扩展会自动显示预测历史记录并分析 JSON 结果的结果，从而为您提供每个预测的直观、高保真的图形：

![显示预测关系图和预测历史记录的单一功能页](media/cpu-forecast-2.png)

### <a name="using-the-event-log-to-retrieve-capability-results"></a>使用事件日志检索功能结果
每次功能完成预测时，系统见解都会记录一个事件。 这些事件显示在**Microsoft-Windows 系统-Insights/管理**通道中，而 System Insights 针对每种状态发布了不同的事件 ID：

| 预测状态 | 事件 ID |
| --------------- | --------------- |
| 正常 | 151 |
| 警告 | 148 |
| 严重 | 150 |
| 错误 | 149 |
| None | 132 |

>[!TIP]
>使用[Azure Monitor](https://azure.microsoft.com/services/monitor/)或[System Center Operations Manager](https://docs.microsoft.com/system-center/scom/welcome?view=sc-om-1807)来聚合这些事件，并查看一组计算机中的预测结果。


## <a name="setting-a-capability-schedule"></a>设置功能计划
除了按需预测外，还可以为每个功能配置定期预测，以便按照预定义的计划自动调用指定的功能。 使用**InsightsCapabilitySchedule** cmdlet 查看功能计划：

>[!TIP]
>使用 PowerShell 中的管道运算符查看**InsightsCapability** cmdlet 返回的所有功能的信息。

```PowerShell
Get-InsightsCapability | Get-InsightsCapabilitySchedule
```

默认情况下会启用定期预测，不过，使用**InsightsCapabilitySchedule**和**InsightsCapabilitySchedule** cmdlet 可随时禁用定期预测：

```PowerShell
Enable-InsightsCapabilitySchedule -Name "Total storage consumption forecasting"
Disable-InsightsCapabilitySchedule -Name "Volume consumption forecasting"
```

每个默认功能都计划在每天的3am 运行。 但是，你可以为每个功能创建自定义计划，而系统见解支持多种计划类型，可以使用**InsightsCapabilitySchedule** cmdlet 进行配置：

```PowerShell
Set-InsightsCapabilitySchedule -Name "CPU capacity forecasting" -Daily -DaysInterval 2 -At 4:00PM
Set-InsightsCapabilitySchedule -Name "Networking capacity forecasting" -Daily -DaysOfWeek Saturday, Sunday -At 2:30AM
Set-InsightsCapabilitySchedule -Name "Total storage consumption forecasting" -Hourly -HoursInterval 2 -DaysOfWeek Monday, Wednesday, Friday
Set-InsightsCapabilitySchedule -Name "Volume consumption forecasting" -Minute -MinutesInterval 30
```
>[!NOTE]
>因为默认功能分析每日数据，所以建议将每日计划用于这些功能。 在[此处](understanding-capabilities.md)了解有关默认功能的详细信息。

通过单击 "**设置**"，还可以使用 Windows 管理中心来查看和设置每项功能的计划。 当前计划显示在 "**计划**" 选项卡上，你可以使用 GUI 工具创建新计划：

![显示当前计划的 "设置" 页](media/schedule-page-contoso.png)

## <a name="creating-remediation-actions"></a>正在创建更正操作
使用系统见解，你可以基于功能的结果开始自定义修正脚本。 对于每个功能，你可以为每个预测状态配置自定义 PowerShell 脚本，从而允许管理员自动采取纠正措施，而无需手动干预。

示例更正操作包括运行磁盘清理、扩展卷、运行重复数据删除、实时迁移 Vm 以及设置 Azure 文件同步。

可以使用**InsightsCapabilityAction** cmdlet 查看每个功能的操作：

```PowerShell
Get-InsightsCapability | Get-InsightsCapabilityAction
```

你可以使用**InsightsCapabilityAction**和 InsightsCapabilityAction cmdlet 创建新操作或删除现有**的**操作。 每个操作都使用**ActionCredential**参数中指定的凭据运行。

>[!NOTE]
>在初始系统 Insights 版本中，你必须在用户目录之外指定修正脚本。 将在即将发布的版本中修复此问题。

```PowerShell
$Cred = Get-Credential
Set-InsightsCapabilityAction -Name "CPU capacity forecasting" -Type Warning -Action "C:\Users\Public\WarningScript.ps1" -ActionCredential $Cred
Set-InsightsCapabilityAction -Name "CPU capacity forecasting" -Type Critical -Action "C:\Users\Public\CriticalScript.ps1" -ActionCredential $Cred

Remove-InsightsCapabilityAction -Name "CPU capacity forecasting" -Type Warning
```

你还可以使用 "**设置**" 页中的 "**操作**" 选项卡，使用 Windows 管理中心来设置更正操作：

![用户可以在其中指定更正操作的 "设置" 页](media/actions-page-contoso.png)


## <a name="additional-references"></a>其他参考
若要了解有关系统见解的详细信息，请使用以下资源：

- [系统见解概述](overview.md)
- [了解功能](understanding-capabilities.md)
- [添加和开发功能](adding-and-developing-capabilities.md)
- [系统见解常见问题解答](faq.md)