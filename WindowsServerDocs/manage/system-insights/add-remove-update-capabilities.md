---
title: 添加、删除和更新功能
description: 使用系统见解，你可以创建利用现有数据收集和管理功能的新功能。 还必须具备平台支持来管理这些功能的添加、删除和更新，这一点很重要。 本主题介绍在系统见解中添加、删除和更新功能的高级功能。
ms.prod: windows-server
ms.technology: system-insights
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 7/31/2018
ms.openlocfilehash: 217cb528896e3b09ce81821bb0201388fab28701
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85475274"
---
# <a name="adding-removing-and-updating-capabilities"></a>添加、删除和更新功能

>适用于：Windows Server 2019

使用系统见解，你可以创建利用现有数据收集和管理功能的新功能。 但是，一旦创建了这些功能，就同样重要的是，您还可以使用平台支持来管理这些功能的添加、删除和更新。

本主题介绍在系统见解中添加、删除和更新功能的高级功能。

## <a name="adding-a-capability"></a>添加功能
使用 System Insights，你可以随时使用**InsightsCapability** cmdlet 添加新功能。 **InsightsCapability**要求你指定功能名称和功能库。 功能库包含功能说明、数据源和预测逻辑。

```PowerShell
Add-InsightsCapability -Name Sample capability -Library C:\SampleCapability.dll
```

向系统见解添加功能后，可以使用 PowerShell 或 Windows 管理中心立即调用和管理此功能。

## <a name="updating-a-capability"></a>更新功能
使用 System Insights，还可以使用**InsightsCapability** cmdlet 更新功能。

```PowerShell
Update-InsightsCapability -Name Sample capability -Library C:\SampleCapabilityv2.dll
```

通过更新功能，您可以指定新的功能库，这允许您更改功能说明、数据源以及与该功能关联的预测逻辑。 重要的是，更新功能将保留有关该功能的所有配置和历史信息，包括自定义计划、操作和历史预测结果。

## <a name="removing-a-capability"></a>删除功能
还可以使用**InsightsCapability** Cmdlet 删除 System Insights 中的功能。

```PowerShell
Remove-InsightsCapability -Name Sample capability
```
>[!NOTE]
>不能删除默认预测功能。

删除功能将永久删除功能和所有关联的信息，包括计划、任何更正操作和过去的预测结果。

>[!TIP]
>如果你担心永久删除与功能相关的所有信息，请考虑禁用功能，而不是将其删除。

## <a name="additional-references"></a>其他参考
若要了解有关系统见解的详细信息，请使用以下资源：

- [系统见解概述](overview.md)
- [了解功能](understanding-capabilities.md)
- [管理功能](managing-capabilities.md)
- [添加和开发功能](adding-and-developing-capabilities.md)
- [系统见解常见问题解答](faq.md)