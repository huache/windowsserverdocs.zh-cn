---
title: 了解和配置 Azure Monitor
description: 详细设置信息 Azure Monitor 是什么，以及如何为 Windows Server 2016 和2019中的存储空间直通群集配置电子邮件和短信警报。
ms.prod: windows-server
ms.author: adagashe
ms.technology: storage-spaces
ms.topic: article
author: adagashe
ms.date: 01/10/2020
ms.openlocfilehash: 72d08b3e4461eeea07e161de1073f5320830028c
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953981"
---
# <a name="use-azure-monitor-to-send-emails-for-health-service-faults"></a>使用 Azure Monitor 发送有关运行状况服务故障的电子邮件

>适用于：Windows Server 2019、Windows Server 2016

Azure Monitor 提供用于收集、分析和处理来自云与本地环境的遥测数据的综合解决方案，可将应用程序的可用性和性能最大化。 它可以帮助你了解应用程序的性能，并主动识别影响应用程序及其所依赖资源的问题。

这对于本地超聚合群集特别有用。 通过 Azure Monitor 集成，你可以配置电子邮件、文本（SMS）和其他警报，以便在出现问题时对你的群集进行 ping 操作（或者当你想要基于收集的数据来标记其他活动时）进行 ping 操作。 下面，我们将简要说明 Azure Monitor 的工作原理、如何安装 Azure Monitor，以及如何将其配置为发送通知。

如果使用的是 System Center，请查看监视 Windows Server 2019 和 Windows Server 2016 存储空间直通群集的[存储空间直通管理包](https://www.microsoft.com/download/details.aspx?id=100782)。

此管理包包括：

* 物理磁盘运行状况和性能监视
* 存储节点运行状况和性能监视
* 存储池运行状况和性能监视
* 卷复原类型和重复数据删除状态

## <a name="understanding-azure-monitor"></a>了解 Azure Monitor

Azure Monitor 收集的所有数据属于以下两种基本类型之一：指标和日志。

1. [指标](/azure/azure-monitor/platform/data-collection#metrics)是数字值，用于描述系统某些方面在特定时间点的情况。 指标是轻型数据，可以支持近实时方案。 你将在 Azure 门户的 "概述" 页中看到 Azure Monitor 收集的数据。

![在指标资源管理器中引入指标的图像](media/configure-azure-monitor/metrics.png)

2. [日志](/azure/azure-monitor/platform/data-collection#logs)包含不同类型的已经整理成记录的数据，每种类型都有不同的属性集。 与性能数据一样，事件和跟踪等遥测数据也作为日志存储，因此，可将它们合并以进行分析。 可以使用[查询](/azure/azure-monitor/log-query/log-query-overview)来分析 Azure Monitor 收集的日志数据，这些查询可以快速检索、合并和分析所收集的数据。 可以使用 Azure 门户中的 [Log Analytics](/azure/azure-monitor/log-query/portals) 创建和测试查询，然后可以直接使用这些工具分析数据，或者保存查询以便与[可视化效果](/azure/azure-monitor/visualizations)或[警报规则](/azure/azure-monitor/platform/alerts-overview)配合使用。

![在 Log Analytics 中引入日志的图像](media/configure-azure-monitor/logs.png)

下面将详细介绍如何配置这些警报。

## <a name="onboarding-your-cluster-using-windows-admin-center"></a>使用 Windows 管理中心加入群集

使用 Windows 管理中心，你可以将群集加入到 Azure Monitor。

![要 Azure Monitor 的载入群集的 Gif](media/configure-azure-monitor/onboarding.gif)

在此加入流程中，将在幕后执行以下步骤。 如果要手动设置群集，我们将详细介绍如何配置它们。

### <a name="configuring-health-service"></a>配置运行状况服务

首先要做的就是配置群集。 你可能也知道，[运行状况服务](../../failover-clustering/health-service-overview.md)改进了运行存储空间直通的群集的日常监视和操作体验。

如上所述，Azure Monitor 从群集中运行的每个节点收集日志。 因此，我们必须将运行状况服务配置为写入事件通道，这恰好是：

```
Event Channel: Microsoft-Windows-Health/Operational
Event ID: 8465
```

若要配置运行状况服务，请运行：

```PowerShell
get-storagesubsystem clus* | Set-StorageHealthSetting -Name "Platform.ETW.MasTypes" -Value "Microsoft.Health.EntityType.Subsystem,Microsoft.Health.EntityType.Server,Microsoft.Health.EntityType.PhysicalDisk,Microsoft.Health.EntityType.StoragePool,Microsoft.Health.EntityType.Volume,Microsoft.Health.EntityType.Cluster"
```

当你运行上述 cmdlet 来设置运行状况设置时，将导致我们要开始向*Microsoft Windows 运行状况/操作*事件通道中写入事件。

### <a name="configuring-log-analytics"></a>配置 Log Analytics

在群集上设置正确的日志记录后，下一步就是正确配置 log analytics。

为了进行概述， [Azure Log Analytics](/azure/azure-monitor/platform/agent-windows)可以将数据从数据中心或其他云环境中的物理或虚拟 Windows 计算机直接收集到单个存储库中，以便进行详细的分析和关联。

若要了解支持的配置，请查看[支持的 Windows 操作系统](/azure/azure-monitor/platform/log-analytics-agent#supported-windows-operating-systems)和[网络防火墙配置](/azure/azure-monitor/platform/log-analytics-agent#network-firewall-requirements)。

如果没有 Azure 订阅，请在开始之前创建一个[免费帐户](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)。

#### <a name="login-in-to-azure-portal"></a>登录到 Azure 门户

通过 [https://portal.azure.com](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) 登录到 Azure 门户。

#### <a name="create-a-workspace"></a>创建工作区

有关下面列出的步骤的详细信息，请参阅 [Azure Monitor 文档](/azure/azure-monitor/learn/quick-collect-windows-computer)。

1. 在 Azure 门户中，单击“所有服务”****。 在资源列表中，键入“Log Analytics”。 开始键入时，会根据输入筛选该列表。 选择“Log Analytics”****。<br><br>

   ![Azure 门户](media/configure-azure-monitor/azure-portal-01.png)<br><br>

2. 单击“创建”****，然后为以下各项选择选项：

   * 为新的 Log Analytics 工作区**** 提供名称，如 DefaultLAWorkspace**。
   * 如果选择的默认值不合适，请从下拉列表中选择要链接到的**订阅**。
   * 对于“资源组”，选择包含一个或多个 Azure 虚拟机的现有资源组。 <br><br>

      ![创建 Log Analytics 资源边栏选项卡](media/configure-azure-monitor/create-loganalytics-workspace-02.png) <br><br>

3. 在“Log Analytics 工作区”窗格上提供所需信息后，单击“确定” 。

在验证信息和创建工作区时，可以在菜单中的“通知”下面跟踪操作进度。

#### <a name="obtain-workspace-id-and-key"></a>获取工作区 ID 和密钥
在安装适用于 Windows 的 Microsoft Monitoring Agent 之前，需要先获得 Log Analytics 工作区的工作区 ID 和密钥。  安装向导需要使用此信息来正确配备代理，并确保它能与 Log Analytics 成功通信。

1. 在 Azure 门户中，单击左上角的“所有服务”****。 在资源列表中，键入“Log Analytics”。 开始键入时，会根据输入筛选该列表。 选择“Log Analytics”****。
2. 在 Log Analytics 工作区列表中，选择之前创建的 DefaultLAWorkspace**。
3. 选择“高级设置”。<br><br> ![Log Analytics 高级设置](media/configure-azure-monitor/log-analytics-advanced-settings-01.png)<br><br>
4. 选择“已连接的源”，然后选择“Windows 服务器” 。
5. “工作区 ID”和“主密钥”右侧的值**** ****。 暂时保存两者 - 暂时将两者复制粘贴到你最喜欢的编辑器中。

### <a name="installing-the-agent-on-windows"></a>在 Windows 上安装代理
请按照下面的步骤安装和配置 Microsoft Monitoring Agent。 **请确保在群集中的每个服务器上安装此代理，并指示你希望在 Windows 启动时运行代理。**

1. 在“Windows 服务器”页上，选择“下载 Windows 代理”，根据 Windows 操作系统的处理器体系结构下载相应的版本。**** ****
2. 运行安装程序在计算机上安装该代理。
2. 在“欢迎”页面上，单击“下一步”。 
3. 在“许可条款”页面上阅读许可协议，然后单击“我接受” 。
4. 在“目标文件夹”页面上更改或保留默认安装文件夹，然后单击“下一步” 。
5. 在“代理安装选项”页上，选择将代理连接到 Azure Log Analytics，单击“下一步”。 
6. 在“Azure Log Analytics”页上执行以下操作：
   1. 粘贴前面复制的“工作区 ID”和“工作区密钥(主密钥)”。 
    a. 如果计算机需要通过代理服务器来与 Log Analytics 通信，请单击“高级”并提供代理服务器的 URL 和端口号。  如果代理服务器要求身份验证，请键入用于在代理服务器上进行身份验证的用户名和密码，并单击“下一步”。
7. 提供所需的配置设置后，单击“下一步”。<br><br> ![粘贴工作区 ID 和主键](media/configure-azure-monitor/log-analytics-mma-setup-laworkspace.png)<br><br>
8. 在“准备安装”页上检查所做的选择，并单击“安装”。 
9. 在“配置已成功完成”页上，单击“完成”。 

完成后，**Microsoft Monitoring Agent** 将显示在“**控制面板**”中。 可以检查配置，并验证代理是否已连接到 Log Analytics。 处于已连接状态时，在“Azure Log Analytics”选项卡上，代理会显示一条消息****：Microsoft Monitoring Agent 已成功连接到 Microsoft Log Analytics 服务。****

![MMA 与 Log Analytics 的连接状态](media/configure-azure-monitor/log-analytics-mma-laworkspace-status.png)

若要了解支持的配置，请查看[支持的 Windows 操作系统](/azure/azure-monitor/platform/log-analytics-agent#supported-windows-operating-systems)和[网络防火墙配置](/azure/azure-monitor/platform/log-analytics-agent#network-firewall-requirements)。

## <a name="setting-up-alerts-using-windows-admin-center"></a>使用 Windows 管理中心设置警报

在 Windows 管理中心，可以配置将应用于 Log Analytics 工作区中所有服务器的默认警报。

![设置警报的 Gif](media/configure-azure-monitor/setup1.gif)

下面列出了可选择加入的警报及其默认条件：

| 警报名称                | 默认条件                                  |
|---------------------------|----------------------------------------------------|
| CPU 使用率           | 持续 10 分钟超过 85%                            |
| 磁盘容量利用率 | 持续 10 分钟超过 85%                            |
| 内存利用率        | 持续 10 分钟可用内存小于 100 MB   |
| 检测信号                 | 持续 5 分钟少于 2 个信号                   |
| 系统严重错误     | 群集系统事件日志中的任何严重警报 |
| 运行状况服务警报      | 群集上的任何运行状况服务故障            |

在 Windows 管理中心中配置警报后，你可以在 Azure 中的 log analytics 工作区中查看警报。

![设置警报的 Gif](media/configure-azure-monitor/setup2.gif)

在此加入流程中，将在幕后执行以下步骤。 如果要手动设置群集，我们将详细介绍如何配置它们。

### <a name="collecting-event-and-performance-data"></a>收集事件和性能数据

Log Analytics 可从 Windows 事件日志以及指定用于长期分析的性能计数器中收集事件，并在检测到特定条件时采取措施。  首先，请按照下列步骤操作，配置 Windows 事件日志以及几个常见性能计数器中收集事件。

1. 在 Azure 门户中，单击左下角的“更多服务”****。 在资源列表中，键入“Log Analytics”。 开始键入时，会根据输入筛选该列表。 选择“Log Analytics”****。
2. 选择“高级设置”。<br><br> ![Log Analytics 高级设置](media/configure-azure-monitor/log-analytics-advanced-settings-01.png)<br><br>
3. 选择“数据”，然后选择“Windows 事件日志”。
4. 在此处，通过键入下面的名称并单击加号“+”来添加运行状况服务事件通道****。
   ```
   Event Channel: Microsoft-Windows-Health/Operational
   ```
5. 在表中，选中严重性“错误”和“警告”。
6. 单击页面顶部的“保存”来保存配置。****
7. 选择“Windows 性能计数器”，在 Windows 计算机上启用性能计数器收集。
8. 首次为新的 Log Analytics 工作区配置 Windows 性能计数器时，可以选择快速创建几个通用的计数器。 将这些计数器在一个复选框中依次列出。<br> ![选中的默认 Windows 性能计数器](media/configure-azure-monitor/windows-perfcounters-default.png)<br> 单击“添加所选性能计数器”****。  随即会添加它们，并且通过 10 秒收集示例间隔进行预设。
9. 单击页面顶部的“保存”来保存配置。****

## <a name="creating-alerts-based-on-log-data"></a>基于日志数据创建警报

如果已完成此项，群集应向 Log Analytics 发送日志和性能计数器。 下一步是创建警报规则，以定期自动运行日志搜索。 如果日志搜索的结果与特定条件匹配，则会触发警报，向你发送电子邮件或文本通知。 下面我们来探讨这个问题。

### <a name="create-a-query"></a>创建查询

首先打开日志搜索门户。

1. 在 Azure 门户中，单击“所有服务”****。 在资源列表中，键入“监视器”****。 开始键入时，会根据输入筛选该列表。 选择“监视器”****。
2. 在 "监视" 导航菜单上，选择 " **Log Analytics** "，然后选择一个工作区。

用于检索某些要使用的数据的最快方法是使用一个简单查询，它可返回表中的所有记录。 在搜索框中键入以下查询，然后单击“搜索”按钮。

```
Event
```

数据会返回到默认列表视图中，并可看到返回的总记录条数。

![简单查询](media/configure-azure-monitor/log-analytics-portal-eventlist-01.png)

屏幕左侧是“筛选器”窗格，可用于向查询添加筛选而无需直接修改查询。  该记录类型显示有多个记录属性，可选择一个或多个属性值来缩小搜索结果范围。

选中“EVENTLEVELNAME”下“错误”旁边的复选框，或键入以下内容将结果限制为错误事件**** ****。

```
Event | where (EventLevelName == "Error")
```

![筛选器](media/configure-azure-monitor/log-analytics-portal-eventlist-02.png)

对所关注的事件进行 approriate 查询后，请将其保存为下一步。

### <a name="create-alerts"></a>创建警报
现在，让我们看一看创建警报的示例。

1. 在 Azure 门户中，单击“所有服务”****。 在资源列表中，键入“Log Analytics”。 开始键入时，会根据输入筛选该列表。 选择“Log Analytics”****。
2. 在左窗格中选择“警报”，然后单击页面顶部的“新建警报规则”，以便创建新的警报。**** ****<br><br> ![创建新的警报规则](media/configure-azure-monitor/alert-rule-02.png)<br>
3. 第一步是在“创建警报”部分选择充当资源的 Log Analytics 工作区，**** 因为这是基于日志的警报信号。  对结果进行筛选，方法是：从下拉列表中选择特定的“订阅”（如果有多个），其中包含此前创建的 Log Analytics 工作区****。  从下拉列表中选择“Log Analytics”，对“资源类型”进行筛选。**** ****  最后，选择**资源** **DefaultLAWorkspace**，然后单击“完成”。****<br><br> ![创建警报步骤 1 任务](media/configure-azure-monitor/alert-rule-03.png)<br>
4. 在“警报条件”部分下，单击“添加条件”，选择保存的查询，然后指定警报规则遵循的逻辑**** ****。
5. 使用以下信息配置警报：a. 从“基于”下拉列表中选择“指标度量”**** ****。  指标度量将为查询中其值超出指定阈值的每个对象创建一个警报。
   b. 对于 "**条件**"，选择 "**大于**" 并指定 thershold。
   c. 然后定义触发警报的时间。 例如，可以选择“连续违规”，然后从下拉列表中选择“大于”值 3**** ****。
   d. 在“评估条件”部分下，将“期间”值修改为“30”分钟，频率改为“5”**** **** ****。 此规则将每五分钟运行一次，返回从当前时间算起过去 30 分钟内创建的记录。  将时间段设置为更宽的时间窗口可以解决数据延迟的可能性，并确保查询返回数据以避免警报永远不会触发的漏报。
6. 单击“完成”，完成警报规则。****<br><br> ![配置警报信号](media/configure-azure-monitor/alert-signal-logic-02.png)<br>
7. 现在转到第二步，在“警报规则名称”字段中提供警报的名称，例如“所有错误事件的警报”**** ****。  指定“说明”，详细描述该警报的具体信息，并从提供的选项中选择“关键(严重性 0)”作为“严重性”值。**** **** ****
8. 若要在创建后立即激活警报规则，请接受“创建后启用规则”选项的默认值。****
9. 第三步也是最后一步，指定“操作组”****，确保每次触发警报时都执行相同的操作，而且这些操作可以用于定义的每项规则。 使用以下信息配置新操作组：a. 选择“新建操作组”，此时会显示“添加操作组”窗格。**** ****
   b. 对于“操作组名称”****，请指定一个长名称，例如“IT 操作 - 通知”，以及一个“短名称”，例如“itops-n”。**** **** ****
   c. 验证“订阅”和“资源组”的默认值是否正确**** ****。 如果否，请从下拉列表中选择正确的值。
   d. 在“操作”部分指定操作的名称，例如“发送电子邮件”，然后在“操作类型”下的下拉列表中选择“电子邮件/短信/推送/语音”。**** **** **** “电子邮件/短信/推送/语音”属性窗格会在右侧打开，其中包含更多的信息。****
   e. 在**电子邮件/SMS/推送/语音**窗格上，选择并设置你的首选项。 例如，启用“电子邮件”，并提供有效的可以接收邮件的电子邮件 SMTP 地址****。
   f. **** 单击“确定”以保存你的更改。<br><br>

    ![创建新的操作组](media/configure-azure-monitor/action-group-properties-01.png)

10. 单击“确定”****，完成操作组。
11. 单击“创建警报规则”，完成警报规则。**** 该警报会立即开始运行。<br><br> ![完成新警报规则的创建](media/configure-azure-monitor/alert-rule-01.png)<br>

### <a name="example-alert"></a>示例警报

作为参考，下面提供 Azure 中的示例警报。

![Azure 中的警报 Gif](media/configure-azure-monitor/alert.gif)

下面是 Azure Monitor 发送的电子邮件的示例：

![警报电子邮件示例](media/configure-azure-monitor/warning.png)

## <a name="additional-references"></a>其他参考

- [存储空间直通概述](storage-spaces-direct-overview.md)
- 有关更多详细信息，请阅读[Azure Monitor 文档](/azure/azure-monitor/learn/tutorial-viewdata)。
- 阅读此概述，了解有关如何[连接到其他 Azure 混合服务](../../manage/windows-admin-center/azure/index.md)的概述。
