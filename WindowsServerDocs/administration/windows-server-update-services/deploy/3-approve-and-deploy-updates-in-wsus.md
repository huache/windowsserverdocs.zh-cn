---
title: 步骤 3 - 在 WSUS 中批准和部署更新
description: Windows Server Update Service (WSUS) 主题 - 在 WSUS 中批准和部署更新是部署 WSUS 的四步流程中的第三步
ms.topic: article
ms.assetid: 8d728ff9-170f-47e6-aefe-52be93315a75
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9dbeebf6add9bcd81d8aa6066fb166a35937a692
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637568"
---
# <a name="step-3-approve-and-deploy-updates-in-wsus"></a>步骤 3:在 WSUS 中批准和部署更新

>适用于：Windows Server 2019、Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在计算机组中的计算机每隔 24 个小时就自动联系 WSUS 服务器以获取更新。 你可使用 WSUS 报告功能来确定是否将那些更新部署到测试计算机中。 当测试顺利完成时，你可为组织中的相关计算机组批准更新。 以下清单描述了使用 WSUS 管理控制台批准和部署更新的步骤。

|任务|说明|
|----|--------|
|[3.1.批准和部署 WSUS 更新](3-approve-and-deploy-updates-in-wsus.md#BKM_3.1.)|使用 WSUS 管理控制台批准和部署 WSUS 更新。|
|[3.2.配置自动审批规则](3-approve-and-deploy-updates-in-wsus.md#BKM_3.2.a.)|配置 WSUS 以自动为所选组审批更新的安装以及如何审批对现有更新的修订。|
|[3.3.使用 WSUS 报告查看安装的更新](3-approve-and-deploy-updates-in-wsus.md#BKM_3.3.)|使用 WSUS 报告功能，查看安装的更新、收到那些更新的计算机及其他详细信息。|

## <a name="31-approve-and-deploy-wsus-updates"></a><a name=BKM_3.1.></a>3.1. 批准和部署 WSUS 更新
使用以下过程批准和部署更新。

#### <a name="to-approve-and-deploy-wsus-updates"></a>批准和部署 WSUS 更新的步骤

1.  在 WSUS 管理控制台上，单击 **“更新”** 。 在右窗格中，显示 **“所有更新”** 、 **“关键更新”** 、 **“安全更新”** 和 **“WSUS 更新”** 的更新状态摘要。

2.  在 **“所有更新”** 部分，单击 **“计算机需要的更新”** 。

3.  在更新列表中，选择你希望批准以便安装在测试计算机组中的更新。 有关所选更新的信息可在 **“更新”** 面板的下窗格中找到。 若要选择多个连续更新，请在单击更新名称的同时按住 **Shift** 键。 若要选择多个非连续更新，请在单击更新名称的同时按住 **CTRL** 键。

4.  右键单击该选项，然后单击 **“批准”** 。

5.  在 **“批准更新”** 对话框中，选择你的测试组，然后单击向下箭头。

6.  单击 **“批准安装”** ，然后单击 **“确定”** 。

7.  此时 **“批准进度”** 窗口出现，它显示了影响批准更新的任务进度。 完成批准进度时，单击 **“关闭”** 。

## <a name="32-configure-auto-approval-rules"></a><a name=BKM_3.2.a.></a>3.2. 配置自动审批规则
自动审批使你可以指定如何自动为所选组审批更新的安装以及如何审批对现有更新的修订。

#### <a name="to-configure-automatic-approvals"></a>配置自动审批

1.  在 WSUS 管理控制台中的“更新服务”  下，展开 WSUS 服务器，然后单击“选项”  。 “选项”  窗口随即打开。

2.  在“选项”  中，单击“自动审批”  。 “自动审批”对话框随即打开。

3.  在“更新规则”  中，单击“新规则”  。 “添加规则”  对话框随即打开。

4.  在“添加规则”  中，在“步骤1：选择属性”  中，从以下各项选择任何单个选项或选项组合：

    -   **当更新属于特定分类时**

    -   **当更新属于特定产品时**

    -   设置审批期限 

5.  在“步骤 2：编辑属性”  中，单击列出的每个选项，然后为每个选项选择合适的选项。

6.  在“步骤 3：  指定名称”中，为你的规则键入名称，然后单击“确定”  。

7.  单击“确定”  以关闭“自动审批”对话框。

## <a name="33-review-installed-updates-with-wsus-reports"></a><a name=BKM_3.3.></a>3.3. 使用 WSUS 报告查看安装的更新
你批准更新后 24 小时，可使用 WSUS 报告功能来确定是否将更新部署到测试计算机组中。 若要检查更新的状态，你可按以下方式使用 WSUS 报告功能。

#### <a name="to-review-updates"></a>查看更新的步骤

1.  在 WSUS 管理控制台的导航窗格中，单击 **“报告”** 。

2.  在 **“报告”** 页上，单击 **“更新状态摘要”** 报告。 将会出现 **“更新报告”** 窗口。

3.  如果你希望过滤更新列表，请选择你想使用的标准，例如 **“包含这些类别中的更新”** ，然后单击 **“运行报告”** 。

4.  你将看到 **“更新报告”** 窗格。 在窗格左部分中选择更新，可检查个别更新的状态。 报告窗格的最后部分显示更新的状态摘要。

5.  单击工具栏上的适用图标，可保存或打印此报告。

6.  测试更新之后，你可批准在组织的适当计算机组中安装更新。
