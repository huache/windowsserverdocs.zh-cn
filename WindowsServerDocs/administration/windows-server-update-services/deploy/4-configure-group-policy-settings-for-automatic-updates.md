---
title: 步骤 4 - 为自动更新配置组策略设置
description: Windows Server Update Service (WSUS) 主题 -“为自动更新配置组策略设置”是部署 WSUS 的四步流程中的第四个步骤
ms.topic: article
ms.assetid: 62177d05-d832-4ea8-bca4-47a8cd34a19c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ca59369cda4c38af111b9ccd3141219b1516cbd7
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87991102"
---
# <a name="step-4-configure-group-policy-settings-for-automatic-updates"></a>步骤 4：为自动更新配置组策略设置

>适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在 Active Directory 环境中，可以使用组策略来定义计算机和用户（在本文档中称为 WSUS 客户端）如何与 Windows 更新交互，以从 Windows Server Update Services (WSUS) 获取自动更新。

本主题包含两个主要部分：

[WSUS 客户端更新的组策略设置](#group-policy-settings-for-wsus-client-updates)：提供有关 Windows 更新和组策略维护计划程序设置（控制 WSUS 客户端如何与 Windows 更新交互以获取自动更新）的规范性指导和行为详细信息。

[补充信息](#supplemental-information)包括以下部分：

-   [访问组策略中的 Windows 更新设置](#accessing-the-windows-update-settings-in-group-policy)：提供有关使用组策略管理编辑器的一般指导，以及有关如何访问更新服务策略扩展和组策略中的维护计划程序设置的信息。

-   [与本指南相关的 WSUS 更改](#changes-to-wsus-relevant-to-this-guide)：对于熟悉 WSUS 3.2 和更低版本的管理员，此部分概要地汇总了与本指南相关的 WSUS 当前版本与以前版本之间的主要差异。

-   [术语和定义](#terms-and-definitions)：本指南中使用的有关 WSUS 和更新服务的各个术语的定义。

## <a name="group-policy-settings-for-wsus-client-updates"></a>WSUS 客户端更新的组策略设置
本部分提供有关组策略的三个扩展的信息。 在这些扩展中，可以找到一些可用来配置 WSUS 客户端如何与 Windows 更新交互以接收自动更新的设置。

-   [计算机配置 &gt; Windows 更新策略设置](#computer-configuration--windows-update-policy-settings)

-   [计算机配置 &gt; 维护计划程序策略设置](#computer-configuration--maintenance-scheduler-policy-settings)

-   [用户配置 &gt; Windows 更新策略设置](#user-configuration--windows-update-policy-settings)

> [!NOTE]
> 本主题假设你用过并熟悉组策略。 如果你不熟悉组策略，我们建议先查看本文档的[补充信息](#supplemental-information)部分，然后再尝试为 WSUS 配置策略设置。

### <a name="computer-configuration--windows-update-policy-settings"></a>计算机配置 > Windows 更新策略设置
本部分提供有关以下基于计算机的策略设置的详细信息：

-   [允许自动更新立即安装](#allow-automatic-updates-immediate-installation)

-   [允许非管理员接收更新通知](#allow-non-administrators-to-receive-update-notifications)

-   [允许使用来自 Intranet Microsoft 更新服务位置的签名更新](#allow-signed-updates-from-an-intranet-microsoft-update-service-location)

-   [自动更新检测频率](#automatic-updates-detection-frequency)

-   [配置自动更新](#configure-automatic-updates)

-   [对计划的安装延迟重启](#delay-restart-for-scheduled-installations)

-   [不要调整“关闭 Windows”对话框中的默认选项“安装更新并关机”](#do-not-adjust-default-option-to-install-updates-and-shut-down-in-shut-down-windows-dialog)

-   [不要在“关闭 Windows”对话框中显示“安装更新并关机”选项](#do-not-display-install-updates-and-shut-down-option-in-shut-down-windows-dialog)

-   [启用客户端定位](#enable-client-side-targeting)

-   [启用 Windows 更新电源管理以自动唤醒计算机来安装计划的更新](#enabling-windows-update-power-management-to-automatically-wake-up-the-computer-to-install-scheduled-updates)

-   [对于有已登录用户的计算机，计划的自动更新安装不执行自动重启](#no-auto-restart-with-logged-on-users-for-scheduled-automatic-updates-installations)

-   [对计划的安装再次提示重启](#re-prompt-for-restart-with-scheduled-installations)

-   [重新计划自动更新计划的安装](#reschedule-automatic-updates-scheduled-installations)

-   [指定 Intranet Microsoft 更新服务位置](#specify-intranet-microsoft-update-service-location)

-   [通过自动更新启用建议的更新](#turn-on-recommended-updates-via-automatic-updates)

-   [启用软件通知](#turn-on-software-notifications)

在 GPME 中，基于计算机的配置的 Windows 更新策略位于以下路径：<策略名称>   > **计算机配置** > **策略** > **管理模板** > **Windows 组件** > **Windows 更新**。

> [!NOTE]
> 默认不会配置这些设置。

#### <a name="allow-automatic-updates-immediate-installation"></a>允许自动更新立即安装
指定自动更新是否自动安装不会中断 Windows 服务或重启 Windows 的更新。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 如果“配置自动更新”策略设置为“已禁用”，则此策略不起作用。 

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定不立即安装更新。 本地管理员可以使用本地组策略编辑器来更改此设置。|
|**Enabled**|指定自动更新在更新已下载并准备好安装后立即安装更新。|
|**已禁用**|指定不立即安装更新。|

**选项：** 此设置没有选项。

#### <a name="allow-non-administrators-to-receive-update-notifications"></a>允许非管理员接收更新通知
指定非管理用户是否基于“配置自动更新”策略设置接收更新通知。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|请参阅下表中的详细信息。|

> [!NOTE]
> 如果“配置自动更新”策略设置已禁用或未配置，则此策略设置不起作用。

> [!IMPORTANT]
> 从 Windows 8 和 Windows RT 开始，默认会启用此策略设置。 在所有以前版本的 Windows 中，默认会禁用此策略设置。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定用户始终会看到“帐户控制”窗口，并需要提升的权限来执行这些任务。 本地管理员可以使用本地组策略编辑器来更改此设置。|
|**Enabled**|指定 Windows 自动更新和 Microsoft 更新在确定哪些登录用户接收更新通知时要包括非管理员。 非管理用户可以安装他们收到了相关通知的所有可选、建议和重要的更新内容。 这些用户将看不到“用户帐户控制”窗口，并且他们不需要提升的权限即可安装这些更新，但无法安装包含用户界面、最终用户许可协议或 Windows 更新设置更改的更新。<p>在以下两种情况下，此设置的影响取决于操作系统：<p>1.**隐藏**或**还原**更新<br />2.**取消**更新安装<p>在 Windows Vista 或 Windows XP 中，如果启用此策略设置，则用户将看不到“用户帐户控制”窗口，并且他们不需要提升的权限即可隐藏、还原或取消更新。<p>在 Windows Vista 中，如果启用此策略设置，则用户将看不到“用户帐户控制”窗口，并且他们不需要提升的权限即可隐藏、还原或取消更新。 如果不启用此策略设置，则用户始终会看到“帐户控制”窗口，并且需要提升的权限才能隐藏、还原或取消更新。<p>在 Windows 7 中，此策略设置不起作用。 用户始终会看到“帐户控制”窗口，并需要提升的权限来执行这些任务。<p>在 Windows 8 和 Windows RT 中，此策略设置不起作用。|
|**已禁用**|指定只有已登录的管理员才能接收更新通知。 **注意：** 在 Windows 8 和 Windows RT 中，默认会启用此策略设置。 在所有以前版本的 Windows 中，默认会禁用此策略设置。|

**选项：** 此设置没有选项。

#### <a name="allow-signed-updates-from-an-intranet-microsoft-update-service-location"></a>允许使用来自 Intranet Microsoft 更新服务位置的签名更新
指定在 Intranet Microsoft 更新服务位置找到更新时，自动更新是否接受 Microsoft 以外的实体签名的更新。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|RT Windows|

> [!NOTE]
> 来自 Intranet Microsoft 更新服务以外的服务的更新必须始终由 Microsoft 签名，且不受此策略设置的影响。

> [!NOTE]
> Windows RT 不支持此策略。 启用此策略不会对运行 Windows RT 的计算机造成任何影响。

**选项：** 此设置没有选项。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定来自 Intranet Microsoft 更新服务位置的更新必须由 Microsoft 签名。|
|**Enabled**|指定如果自动更新通过 Intranet Microsoft 更新服务位置收到的更新已由本地计算机的“受信任发行者”证书存储中的证书签名，则自动更新将接受这些更新。|
|**已禁用**|指定来自 Intranet Microsoft 更新服务位置的更新必须由 Microsoft 签名。|

**选项：** 此设置没有选项。

#### <a name="always-automatically-restart-at-the-scheduled-time"></a>始终在计划的时间自动重启
指定重启计时器是否始终在 Windows 更新安装重要更新后立即开始，而不是先在登录屏幕上通知用户至少两天。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 如果启用了“对于有已登录用户的计算机，计划的自动更新安装不执行自动重启”策略设置，则此策略不起作用。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定 Windows 更新不会改变计算机的重启行为。|
|**Enabled**|指定重启计时器始终在 Windows 更新安装重要更新后立即开始，而不是先在登录屏幕上通知用户至少两天。<p>可将重启计时器配置为使用 15 到 180 分钟的任意值开始。 当计时器运行结束时，即使计算机中包含已登录的用户，重启也仍会继续。|
|**已禁用**|指定 Windows 更新不会改变计算机的重启行为。|

**选项：** 如果启用此设置，可以指定在安装更新之后、发生计算机强制重启之前所要经过的时间。

#### <a name="automatic-updates-detection-frequency"></a>自动更新检测频率
指定 Windows 将用于确定在检查可用更新前等待的时长的小时数。 使用此处指定的小时数减去指定小时数的 0% 到 20% 来确定准确的等待时间。 例如，如果此策略用于指定 20 小时检测频率，那么此策略应用到的所有客户端都将检查 16 与 20 小时之间的任意时间点的更新。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|RT Windows|

> [!NOTE]
> 必须启用“指定 Intranet Microsoft 更新服务位置”设置才能使此策略发挥作用。
>
> 如果“配置自动更新”策略设置已禁用，则此策略不起作用。

> [!NOTE]
> Windows RT 不支持此策略。 启用此策略不会对运行 Windows RT 的计算机造成任何影响。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定 Windows 将按 22 小时的默认间隔检查可用更新。|
|**Enabled**|指定 Windows 将按指定的间隔检查可用更新。|
|**已禁用**|指定 Windows 将按 22 小时的默认间隔检查可用更新。|

**选项：** 如果启用此设置，可以指定 Windows 更新在检查更新之前等待的时间间隔（小时）。

#### <a name="configure-automatic-updates"></a>配置自动更新
指定是否在此计算机上启用自动更新。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|RT Windows|

如果启用，则必须选择此组策略设置中提供的四个选项之一。

若要使用此设置，请选择“已启用”，然后在“配置自动更新”下的“选项”中选择某个选项（2、3、4 或 5）。   

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定未在组策略级别指定使用自动更新。 但是，计算机管理员仍可以在控制面板中配置自动更新。|
|**Enabled**|指定 Windows 可以识别到计算机处于联机状态，并使用其 Internet 连接在 Windows 更新中搜索可用更新。<p>启用后，将允许本地管理员使用 Windows 更新控制面板来选择所需的配置选项。 但是，不允许本地管理员禁用自动更新的配置。<p>-   **2 - 通知下载并通知安装**<br />    当 Windows 更新查找适用于计算机的更新时，系统会通知用户更新已准备就绪，可供下载。 然后，用户可以运行 Windows 更新来下载和安装任何可用更新。<br />-   **3 - 自动下载并通知安装**（默认设置）<br />    Windows 更新查找适用的更新，并在后台下载更新；在此过程中，用户不会收到通知或受到干扰。 下载完成后，系统会通知用户有可安装的更新。 然后，用户可以运行 Windows 更新来安装已下载的更新。<br />-   **4 - 自动下载并计划安装**<br />    可以使用此组策略设置中的选项来指定计划。 如果未指定计划，所有安装的默认计划是每天的凌晨 3:00。 如果任何更新需要重启才能完成安装，则 Windows 将自动重启计算机。 （如果 Windows 准备好重启时某个用户已登录到计算机，则系统会通知用户，并提供延迟重启的选项。）**注意：** 从 Windows 8 开始，可将更新设置为在自动维护期间安装，而不使与绑定到 Windows 更新的特定计划。 自动维护将在计算机未使用时安装更新，并避免在计算机使用电池运行时安装更新。 如果自动维护在几天内都无法安装更新，Windows 更新会立即安装更新。 然后，系统会通知用户等待重启。 仅当不存在数据丢失的可能性时，才会出现等待重启的情况。    可以在“GPME 维护计划程序”设置中指定计划选项，路径为“<策略名称>” > “计算机配置” > “策略” > “管理模板” > “Windows 组件” > “维护计划程序” > “自动维护激活边界”。        请参阅本参考教程的以下部分：[维护计划程序设置](#computer-configuration--maintenance-scheduler-policy-settings)，了解设置详细信息。    **5 - 允许本地管理员选择设置**<br />- 指定是否允许本地管理员使用自动更新控制面板来选择所需的配置选项，例如，本地管理员是否可以选择计划的安装时间。<br />    不允许本地管理员禁用自动更新配置。|
|**已禁用**|指定必须从 Internet 手动下载并安装公共 Windows 更新服务提供的任何客户端更新。|

#### <a name="delay-restart-for-scheduled-installations"></a>对计划的安装延迟重启
指定在继续按计划重启之前自动更新所要等待的时间。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 仅当自动更新配置为执行更新的计划安装时，此策略才适用。 如果“配置自动更新”策略设置已禁用，则此策略不起作用。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定在安装更新之后，发生任何计划的重启之前，将要经历 15 分钟默认等待时间。|
|**Enabled**|指定在完成安装并已经过指定的分钟数之后，将会发生计划的重启。|
|**已禁用**|指定在安装更新之后，发生任何计划的重启之前，将要经历 15 分钟默认等待时间。|

**选项：** 如果启用此设置，可以使用此选项来指定在继续按计划重启之前自动更新所要等待的时间（分钟）。

#### <a name="do-not-adjust-default-option-to-install-updates-and-shut-down-in-shut-down-windows-dialog"></a>不要调整“关闭 Windows”对话框中的默认选项“安装更新并关机”
使用此策略设置可以指定是否允许将“安装更新并关机”选项用作“关闭 Windows”对话框中的默认选项。  

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 如果启用了“PolicyName”   >  **“计算机配置”**  > “策略”   >   “管理模板” >   “Windows 组件” >   “Windows 更新” >   “在‘关闭 Windows’对话框中不显示‘安装更新并关机’选项”策略设置，则此策略设置不会产生任何影响。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定如果在用户选择“关机”选项来关闭计算机时更新可供安装，则“安装更新并关机”将是“关闭 Windows”对话框中的默认选项。  |
|**Enabled**|如果启用此策略设置，则用户上次选择的关机选项（例如，“休眠”或“重启”）将是“关闭 Windows”对话框中的默认选项，而不管“希望计算机做什么?”菜单中是否提供了“安装更新并关机”选项。   |
|**已禁用**|指定如果在用户选择“关机”选项来关闭计算机时更新可供安装，则“安装更新并关机”将是“关闭 Windows”对话框中的默认选项。  |

**选项：** 此设置没有选项。

#### <a name="do-not-connect-to-any-windows-update-internet-locations"></a>不要连接任何 Windows 更新 Internet 位置
即使 Windows 更新被配置为从 Intranet 更新服务接收更新，它也将定期从公共的 Windows 更新服务检索信息，以支持与 Windows 更新及其他服务（例如 Microsoft 更新或 Microsoft Store）的未来连接。

启用此策略会禁用从公共 Windows Server Update Service 定期检索信息的功能，并可能导致与 Microsoft Store 等公共服务的连接停止工作。

|支持的操作系统：|不包括：|
|---------|-------|
|从 Windows Server 2012 R2、Windows 8.1 或 Windows RT 8.1 开始，仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 仅当计算机配置为使用“指定 Intranet Microsoft 更新服务位置”策略设置连接到 Intranet 更新服务时，此策略才适用。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|从公共 Windows Server Update Service 检索信息的默认行为将保持不变。|
|**Enabled**|指定计算机不会从公共 Windows Server Update Service 检索信息。|
|**已禁用**|从公共 Windows Server Update Service 检索信息的默认行为将保持不变。|

**选项：** 此设置没有选项。

#### <a name="do-not-display-install-updates-and-shut-down-option-in-shut-down-windows-dialog"></a>不要在“关闭 Windows”对话框中显示“安装更新并关机”选项
指定是否在“关闭 Windows”对话框中显示“安装更新并关机”选项。  

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定如果在用户选择“关机”选项来关闭计算机时更新可用，则会在“关闭 Windows”对话框中显示“安装更新并关机”选项。   本地管理员可以使用本地策略来更改此设置。|
|**Enabled**|指定即使在用户选择“关机”选项来关闭计算机时更新可供安装，“安装更新并关机”也不会显示为“关闭 Windows”对话框中的选项。  |
|**已禁用**|指定如果在用户选择“关机”选项来关闭计算机时更新可供安装，则“安装更新并关机”选项将是“关闭 Windows”对话框中的默认选项。  |

**选项：** 此设置没有选项。

#### <a name="enable-client-side-targeting"></a>启用客户端定位
指定在 WSUS 控制台中配置的用于从 WSUS 接收更新的一个或多个目标组名称。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|RT Windows|

> [!NOTE]
> 仅当此计算机配置为支持 WSUS 中指定的目标组名称时，此策略才适用。 如果目标组名称在 WSUS 中不存在，则在创建该名称之前会将其忽略。 如果“指定 Intranet Microsoft 更新服务位置”策略设置已禁用或未配置，此策略将不起作用。

> [!NOTE]
> Windows RT 不支持此策略。 启用此策略不会对运行 Windows RT 的计算机造成任何影响。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定不向 WSUS 发送目标组信息。 本地管理员可以使用本地策略来更改此设置。|
|**Enabled**|指定将指定的目标组信息发送到 WSUS，后者使用这些信息来确定要将哪些更新部署到此计算机。 如果 WSUS 支持多个目标组，则你可以使用此策略来指定多个组名称（以分号分隔），前提是已在 WSUS 的计算机组列表中添加目标组名称。 否则，必须指定单个组。|
|**已禁用**|指定不向 WSUS 发送目标组信息。|

**选项：** 使用此空间可以指定一个或多个目标组名称。

#### <a name="enabling-windows-update-power-management-to-automatically-wake-up-the-computer-to-install-scheduled-updates"></a>启用 Windows 更新电源管理以自动唤醒计算机来安装计划的更新
指定如果有计划安装的更新，Windows 更新是否使用“Windows 电源管理”或“电源选项”功能自动将计算机从休眠状态唤醒。

仅当 Windows 更新配置为自动安装更新时，计算机才会自动唤醒。 如果计算机在发生计划的安装时处于休眠状态，并且有更新等待应用，则 Windows 更新将使用“Windows 电源管理”或“电源选项”功能自动唤醒计算机，以安装更新。 如果达到了安装截止时间，Windows 更新也会唤醒计算机并安装更新。

除非有等待安装的更新，否则计算机不会唤醒。 如果计算机使用电池运行，则在 Windows 更新唤醒计算机时，将不会安装更新，并且计算机会在两分钟后自动恢复休眠状态。

|支持的操作系统：|不包括：|
|---------|-------|
|从 Windows Vista 和 Windows Server 2008 (Windows 7) 开始，仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|Windows 更新不会将计算机从休眠状态唤醒来安装更新。 本地管理员可以使用本地策略来更改此设置。|
|**Enabled**|在符合前面所列的条件时，Windows 更新会将计算机从休眠状态唤醒，以安装更新。|
|**已禁用**|Windows 更新不会将计算机从休眠状态唤醒来安装更新。|

**选项：** 此设置没有选项。

#### <a name="no-auto-restart-with-logged-on-users-for-scheduled-automatic-updates-installations"></a>对于有已登录用户的计算机，计划的自动更新安装不执行自动重启
指定为了完成计划的安装，自动更新将等待任何已登录的用户重启计算机，而不是使计算机自动重启。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 仅当自动更新配置为执行更新的计划安装时，此策略才适用。 如果“配置自动更新”策略设置已禁用，则此策略不起作用。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定自动更新会通知用户，计算机将在五分钟后自动重启以完成安装。|
|**Enabled**|某些更新需要重启计算机才能生效。 如果状态设置为“已启用”，并且用户已登录到计算机，则自动更新在计划的安装期间不会自动重启计算机， 而是通知用户重启计算机。|
|**已禁用**|指定自动更新会通知用户，计算机将在五分钟后自动重启以完成安装。|

**选项：** 此设置没有选项。

#### <a name="re-prompt-for-restart-with-scheduled-installations"></a>对计划的安装再次提示重启
指定在再次提示执行计划的重启之前自动更新所要等待的时间。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|RT Windows|

> [!IMPORTANT]
> 仅当自动更新配置为执行更新的计划安装时，此策略才适用。 如果“配置自动更新”策略设置已禁用，则此策略不起作用。

> [!NOTE]
> 此策略对运行 Windows RT 的计算机不起作用。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|在重启消息提示消失后的十分钟，将发生计划的重启。 本地管理员可以使用本地策略来更改此设置。|
|**Enabled**|指定在上次重启提示延迟后，计划的重启将在指定的分钟数后发生。|
|**已禁用**|在重启消息提示消失后的十分钟，将发生计划的重启。|

**选项：** 如果启用，可以使用此设置选项来指定再次提示用户将要发生计划的重启之前所要经过的时间（分钟）。

#### <a name="reschedule-automatic-updates-scheduled-installations"></a>重新计划自动更新计划的安装
指定在计算机启动之后、继续执行先前已错过的计划安装之前，自动更新所要等待的时间。

如果状态设置为“未配置”，则在下一次启动计算机并经过一分钟之后，将执行已错过的计划安装。 

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 仅当自动更新配置为执行更新的计划安装时，此策略才适用。 如果“配置自动更新”策略设置已禁用，则此策略不起作用。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定在下一次启动计算机并经过一分钟之后，将执行已错过的计划安装。|
|**Enabled**|指定在下一次启动计算机并经过指定的分钟数之后，将执行先前尚未执行的计划安装。|
|**已禁用**|指定在下一次计划的安装时执行已错过的计划安装。|

**选项：** 如果已启用此策略设置，可以使用它来指定在下一次启动计算机并经过多少分钟之后，执行先前尚未执行的计划安装。

#### <a name="specify-intranet-microsoft-update-service-location"></a>指定 Intranet Microsoft 更新服务位置
指定用于托管来自 Microsoft 更新的更新的 Intranet 服务器。 然后，可以使用 WSUS 自动更新网络上的计算机。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|Windows RT。|

使用此设置可以指定网络上充当内部更新服务的 WSUS 服务器。 WSUS 客户端将在此服务中搜索适用的更新，而不是使用 Internet 上的 Microsoft 更新。

若要使用此设置，必须设置两个服务器名称值：客户端从中检测和下载更新的服务器，以及更新后的工作站要将统计信息上传到的服务器。 如果在同一台服务器上配置这两个服务，则值不需要是不同的。

> [!NOTE]
> 如果“配置自动更新”策略设置已禁用，则此策略不起作用。

> [!NOTE]
> Windows RT 不支持此策略。 启用此策略不会对运行 Windows RT 的计算机造成任何影响。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|如果未按策略或用户首选项禁用自动更新，则此策略将指定客户端直接连接到 Internet 上的 Windows 更新站点。|
|**Enabled**|指定客户端连接到指定的 WSUS 服务器（而不是 Windows 更新）来搜索和下载更新。 启用此设置意味着组织中的最终用户不必穿过防火墙来获取更新，而且可让你先测试更新，再部署更新。|
|**已禁用**|如果未按策略或用户首选项禁用自动更新，则此策略将指定客户端直接连接到 Internet 上的 Windows 更新站点。|

**选项：** 如果启用此策略设置，则必须指定 WSUS 客户端在检测更新时要使用的 Intranet 更新服务，以及更新后的 WSUS 客户端要将统计信息上传到的 Internet 统计服务器。 示例值：


|                    设置选项：                    |    示例值：    |
|-------------------------------------------------------|----------------------|
| 设置用于检测更新的 Intranet 更新服务 |  http://wsus01:8530  |
|          设置 Intranet 统计服务器           | http://IntranetUpd01 |

#### <a name="turn-on-recommended-updates-via-automatic-updates"></a>通过自动更新启用建议的更新
指定自动更新是否传送 WSUS 中的重要更新和建议的更新。

|支持的操作系统：|不包括：|
|---------|-------|
|从 Windows Vista 开始，仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定自动更新继续传送重要更新（如果已采用这种配置）。|
|**Enabled**|指定自动更新将安装 WSUS 中建议的更新和重要更新。|
|**已禁用**|指定自动更新继续传送重要更新（如果已采用这种配置）。|

**选项：** 此设置没有选项。

#### <a name="turn-on-software-notifications"></a>启用软件通知
使用此策略设置可以控制用户是否会看到有关 Microsoft 更新服务提供的特色软件的详细增强型通知消息。 增强型通知消息会传递价值，并推广可选软件的安装和使用。 此策略设置适合在松散管理的环境中使用，这种环境允许最终用户访问 Microsoft 更新服务。

如果未使用 Microsoft 更新服务，则“软件通知”策略设置不起作用。

如果“配置自动更新”策略设置已禁用或未配置，则“软件通知”策略设置不起作用。

|支持的操作系统：|不包括：|
|---------|-------|
|从 Windows Server 2008 (Windows Vista) 和 Windows 7 开始，仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 默认会禁用此策略设置。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|不会向 Windows 7 计算机上的用户提供有关可选应用程序的消息。 不会向 Windows Vista 计算机上的用户提供有关可选应用程序或更新的消息。 本地管理员可以使用控制面板或本地策略来更改此设置。|
|**Enabled**|如果启用此策略设置，则有特色软件可用时，用户的计算机上会显示一条通知消息。 用户可以单击该通知打开 Windows 更新，并获取有关该软件的详细信息或安装该软件。 用户还可以视需要单击“关闭此消息”，或“稍后显示”以推迟通知的显示。  <p>在 Windows 7 中，此策略设置只会控制可选应用程序的详细通知。 在 Windows Vista 中，此策略设置控制有关可选应用程序和更新的详细通知。|
|**已禁用**|指定不向运行 Windows 7 的用户提供有关可选应用程序的详细通知消息，且不向运行 Windows Vista 的用户提供有关可选应用程序或可选更新的详细通知消息。|

**选项：** 此设置没有选项。

### <a name="computer-configuration--maintenance-scheduler-policy-settings"></a>计算机配置 > 维护计划程序策略设置
在“配置自动更新”设置中，你已选择“4 - 自动下载并计划安装”选项，现在可以在 GPMC 中为运行 Windows 8 和 Windows RT 的计算机指定“维护计划程序”设置。  如果未在“配置自动更新”设置中选择选项 4，则无需为自动更新的目的配置这些设置。 “维护计划程序”设置位于以下路径：“PolicyName” >  计算机配置  > “策略” > “管理模板” > “Windows 组件” > “维护计划程序”。       组策略的“维护计划程序”扩展包含以下设置：

-   [自动维护激活边界](#automatic-maintenance-activation-boundary)

-   [自动维护随机延迟](#automatic-maintenance-random-delay)

-   [自动唤醒策略](#automatic-wakeup-policy)

#### <a name="automatic-maintenance-activation-boundary"></a>自动维护激活边界
使用此策略可以配置“自动维护激活边界”设置。

维护激活边界是启动自动维护的每日计划时间。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 此设置与“配置自动更新”中的选项 4 相关。  如果在“配置自动更新”中未选择选项 4，则无需配置此设置。 

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|如果未配置此策略设置，将应用在客户端计算机上的“控制面板”>“操作中心” > “自动维护”中指定的每日计划时间。  |
|**Enabled**|启用此策略设置会替代任何默认设置，或客户端计算机上的“控制面板” > “操作中心” > “自动维护”（在某些客户端版本中为“维护”）中配置的已修改设置。    |
|**已禁用**|如果将此策略设置指定为“已禁用”，将应用“控制面板”上“操作中心” > “自动维护”中指定的每日计划时间。   |

#### <a name="automatic-maintenance-random-delay"></a>自动维护随机延迟
使用此策略设置可以配置自动维护激活随机延迟。

维护随机延迟是指自动维护从其激活边界开始延迟的时间长短。 此设置可用于随机维护可能是一项性能要求的虚拟机。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 此设置与“配置自动更新”中的选项 4 相关。  如果在“配置自动更新”中未选择选项 4，则无需配置此设置。 

如果启用此策略，定期维护随机延迟默认将设置为 **PT4H**。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|对“自动”维护应用四小时随机延迟。 |
|**Enabled**|自动维护将从其激活边界开始最多延迟指定的时间。|
|**已禁用**|不向自动维护应用随机延迟。|

#### <a name="automatic-wakeup-policy"></a>自动唤醒策略
使用此策略设置可以配置自动维护唤醒策略。

维护唤醒策略指定自动维护是否应向运行中的计算机发出唤醒请求，以进行日常的计划维护。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 如果显式禁用了运行中计算机的电源唤醒策略，则此设置不起作用。

> [!NOTE]
> 此设置与“配置自动更新”中的选项 4 相关。  如果在“配置自动更新”中未选择选项 4，则无需配置此设置。 

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|如果不配置此策略设置，将应用“控制面板”>“操作中心” > “自动维护”中指定的唤醒设置。  |
|**Enabled**|如果启用此策略设置，则自动维护将根据需要尝试设置操作系统唤醒策略，并在每日计划时间发出唤醒请求。|
|**已禁用**|如果禁用此策略设置，将应用“控制面板”>“操作中心” > “自动维护”中指定的唤醒设置。  |

### <a name="user-configuration--windows-update-policy-settings"></a>用户配置 > Windows 更新策略设置
本部分提供有关以下基于用户的策略设置的详细信息：

-   [不要在“关闭 Windows”对话框中显示“安装更新并关机”选项](#do-not-display-install-updates-and-shut-down-option-in-shut-down-windows-dialog)

-   [不要调整“关闭 Windows”对话框中的默认选项“安装更新并关机”](#do-not-adjust-default-option-to-install-updates-and-shut-down-in-shut-down-windows-dialog)

-   [删除使用所有 Windows 更新功能的访问权限](#remove-access-to-use-all-windows-update-features)

在 GPMC 中，自动计算机更新的用户设置位于以下路径：<策略名称>   > **用户配置** > **策略** > **管理模板** > **Windows 组件** > **Windows 更新**。 这些设置的列出顺序与选择 Windows 更新策略的“设置”选项卡来按字母顺序对设置进行排序时，它们在组策略的“计算机配置”和“用户配置”扩展中的显示顺序相同。 

> [!NOTE]
> 默认情况下，除非另有说明，否则不会配置这些设置。

> [!TIP]
> 可以使用以下步骤来启用、禁用或浏览其中的每项设置：

#### <a name="do-not-display-install-updates-and-shut-down-option-in-shut-down-windows-dialog-box"></a>不要在“关闭 Windows”对话框中显示“安装更新并关机”选项
指定是否在“关闭 Windows”对话框中显示“安装更新并关机”选项。  

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定如果在用户选择“关机”选项来关闭计算机时更新可用，则会在“关闭 Windows”对话框中显示“安装更新并关机”选项。  |
|**Enabled**|如果启用此策略设置，则即使在用户选择“关机”选项来关闭计算机时更新可供安装，“安装更新并关机”也不会显示为“关闭 Windows”对话框中的选项。  |
|**已禁用**|指定如果在用户选择“关机”选项来关闭计算机时更新可用，则会在“关闭 Windows”对话框中显示“安装更新并关机”选项。  |

**选项：** 此设置没有选项。

#### <a name="do-not-adjust-default-option-to-install-updates-and-shut-down-in-shut-down-windows-dialog-box"></a>不要调整“关闭 Windows”对话框中的默认选项“安装更新并关机”
指定是否允许在“关闭 Windows”对话框中显示“安装更新并关机”选项作为默认选项。  

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

> [!NOTE]
> 如果启用了“PolicyName”   >  **“用户配置”**  > “策略”   >   “管理模板” >   “Windows 组件” >   “Windows 更新” >   “在‘关闭 Windows’对话框中不显示‘安装更新并关机’选项”，则此策略设置不会产生任何影响。

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|指定如果在用户选择“关机”选项来关闭计算机时更新可供安装，“安装更新并关机”选项是否为“关闭 Windows”对话框中的默认选项。  |
|**Enabled**|指定用户上次选择的关机选项（例如，“休眠”或“重启”）是否为“关闭 Windows”对话框中的默认选项，而不管“希望计算机做什么?”菜单中是否提供了“安装更新并关机”选项。   |
|**已禁用**|指定如果在用户选择“关机”选项来关闭计算机时更新可供安装，“安装更新并关机”选项是否为“关闭 Windows”对话框中的默认选项。  |

**选项：** 此设置没有选项。

#### <a name="remove-access-to-use-all-windows-update-features"></a>删除使用所有 Windows 更新功能的访问权限
使用此设置可以删除 WSUS 客户端对 Windows 更新的访问权限。

|支持的操作系统：|不包括：|
|---------|-------|
|仍处于 [Microsoft 产品支持生命周期](https://support.microsoft.com/gp/lifeselect)内的 Windows 操作系统。|空|

|||
|-|-|
|**策略设置状态**|**行为**|
|**未配置**|用户可以连接到 Windows 更新网站。|
|**Enabled**|**重要**：如果启用此设置，将删除所有 Windows 更新功能。 这包括阻止从开始菜单或开始屏幕以及 Internet Explorer 的“工具”菜单中的“Windows 更新”超链接访问 Windows 更新网站 https://windowsupdate.microsoft.com 。  Windows 自动更新也会禁用；用户不会收到 Windows 更新提供的关键更新，也不会收到相关通知。 此设置还会阻止设备管理器自动安装 Windows 更新网站中的驱动程序更新。<p>启用后，可以配置以下通知选项之一：<p>-   **0 - 不显示任何通知**<br />    此设置将删除对 Windows 更新功能的所有访问权限，且不显示任何通知。<br />-   **1 - 显示需要重启通知**<br />    此设置将显示有关需要重启才能完成安装的通知。 **注意：** 在运行 Windows 8 和 Windows RT 的计算机上，如果启用此策略，只会显示有关重启且无法检测更新的通知。 不支持通知选项。 始终显示登录屏幕上的通知。|
|**已禁用**|用户可以连接到 Windows 更新网站。|

**选项：** 对于此设置，请参阅表中的“已启用”。 

## <a name="supplemental-information"></a>补充信息
本部分提供有关使用、打开和保存组策略中的 WSUS 设置的附加信息，以及本指南中所用术语的定义。 对于熟悉旧版 WSUS（WSUS 3.2 和更低版本）的管理员，有一个表格简要汇总了 WSUS 版本之间的差异。

### <a name="accessing-the-windows-update-settings-in-group-policy"></a>访问组策略中的 Windows 更新设置
以下过程描述如何在域控制器上打开 GPMC。 然后，该过程描述如何打开现有的域级组策略对象 (GPO) 进行编辑，或创建新的域级 GPO，并将其打开以进行编辑。

> [!NOTE]
> 只有“域管理员”组的成员或类似角色才能执行此过程。 

##### <a name="to-open-or-add-and-open-a-group-policy-object"></a>打开或者添加并打开组策略对象

1.  在域控制器上，转到“服务器管理器”>“工具”>“组策略管理”。    此时会打开组策略管理控制台。

2.  在左窗格中展开你的林。 例如，双击“林: example.com”。 

3.  在左窗格中双击“域”，然后双击要管理其组策略对象的域。  例如，双击“example.com”。 

4.  执行下列操作之一：

    -  **若要打开现有的域级 GPO 进行编辑**，请双击包含所要管理的组策略对象的域，右键单击要管理的域策略，然后单击“编辑”。  此时会打开组策略管理编辑器 (GPME)。

    -  **若要创建新的组策略对象并打开进行编辑**：
        1.  右键单击要为其创建新组策略对象的域，然后单击“在此域中创建 GPO 并将其链接到此处”。 

        2.  在“新建 GPO”中的“名称”内，键入新组策略对象的名称，然后单击“确定”。   

        3.  右键单击新建的组策略对象，然后单击“编辑”。  此时会打开 GPME。

##### <a name="to-open-the-windows-update-or-maintenance-scheduler-extensions-of-group-policy"></a>打开组策略的 Windows 更新或维护计划程序扩展

1.  在组策略管理编辑器中执行以下操作之一：

    -   **打开“计算机配置”>“组策略的 Windows 更新扩展”** 。 导航到：*PolicyName* > **计算机配置** > **策略** / **管理模板** > **Windows 组件** > **Windows 更新**。

    -   **打开“用户配置”>“组策略的 Windows 更新扩展”** 。 导航到：<策略名称>   > **用户配置** > **策略** > **管理模板** > **Windows 组件** > **Windows 更新**。

    -   **打开“计算机配置”>“组策略的维护计划程序扩展”** 。 在 GPOE 中，导航到“<策略名称>” > “计算机配置” > “策略” > “管理模板” > “Windows 组件” > “维护计划程序”。      

有关组策略的详细信息，请参阅[组策略概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831791(v=ws.11))。

> [!TIP]
> 打开所需的组策略扩展后，可以使用以下步骤来启用、禁用或浏览设置：

##### <a name="to-configure-group-policy-settings"></a>配置组策略设置

1.  在“<组策略的扩展>”中，双击要查看或修改的设置。 

2.  若要配置设置，请执行以下操作之一：

    -   若要保留设置的默认未指定状态，请选择“未配置”。 

    -   若要启用设置，请选择“已启用”。 

    -   若要禁用设置，请选择“已禁用”。 

3.  在“选项”中，如果列出了任何选项，请根据需要保留默认值或进行修改。 

4.  执行下列操作之一：

    -   若要保存更改并继续配置下一项设置，请单击“应用”，然后单击“下一设置”。  

    -   若要保存更改并关闭对话框，请单击“确定”。 

    -   若要放弃所有未保存的更改并关闭对话框，请单击“取消”。 

### <a name="changes-to-wsus-relevant-to-this-guide"></a>与本指南相关的 WSUS 更改
下表汇总了与本指南相关的 WSUS 当前版本与以往版本之间的主要差异。

|Windows Server 和 WSUS 版本|说明|
|------------------|--------|
| 使用 WSUS 6.0 和后续版本的 Windows Server 2012 R2|从 Windows Server 2012 开始，WSUS 服务器角色与操作系统集成，WSUS 客户端的关联组策略设置默认包含在组策略中。|
| 使用 WSUS 3.2 和更低版本的 Windows Server 2008（及更低版本的 Windows Server）|在使用 WSUS 版本 3.2（和更低版本）的 Windows Server 2008（及更低版本的 Windows Server）中，控制 WSUS 客户端的组策略设置未包含在这些 Windows Server 操作系统中。 策略设置位于 WSUS 管理模板 **wuau.adm** 中。 在这些服务器版本中，必须先将 WSUS 管理模板添加到组策略管理控制台 (GPMC)，然后才能配置 WSUS 客户端设置。|

### <a name="terms-and-definitions"></a>术语和定义
下面是本指南中使用的术语列表。

|术语|定义|
|----|-------|
|自动更新|**在 Windows 计算机上运行的服务**（自动更新）：指内置在 Microsoft Windows Vista、Windows Server 2003、Windows XP 和 Windows 2000 SP3 操作系统中的客户端计算机组件，用于从 Microsoft 更新或 Windows 更新获取更新。<p>**随意参考**（自动更新）：用于描述 Windows 更新代理自动计划和下载更新的术语。|
|自治服务器|表示一台下游 Windows Server Update Services (WSUS) 服务器，管理员可在其上管理 WSUS 组件。|
|下游服务器|表示一台 Windows Server Update Services (WSUS) 服务器，它从另一台 WSUS 服务器（而不是 Microsoft 更新或 Windows 更新）获取更新。|
|组策略扩展（或组策略的扩展）|组策略中用于控制用户与计算机（要向其应用策略）如何配置和使用各种 Windows 服务与功能的设置集合。 管理员可以在自动更新客户端的客户端配置中结合使用 WSUS 与组策略，以帮助确保最终用户无法禁用或绕过企业的更新策略。<p>WSUS 不要求使用 Active Directory 或组策略。 还可以使用本地组策略或通过修改 Windows 注册表来应用客户端配置。|
|内部更新服务|使用一个或多个 WSUS 服务器来分发更新的网络基础结构的随意参考术语。|
|副本服务器|表示一台下游 Windows Server Update Services (WSUS) 服务器，该服务器将审批和设置镜像到它所连接到的上游服务器。 无法在副本服务器上管理 WSUS。|
|Microsoft 更新|**基于 Internet 的 Microsoft 下载站点：** 一个 Microsoft Internet 站点，用于存储和分发 Windows 计算机（设备驱动程序）、Windows 操作系统和其他 Microsoft 软件产品的更新。|
|软件更新服务 (SUS)|SUS 是 Windows Server Update Services (WSUS) 的前款产品。|
|更新|可安装在计算机上的，以扩展功能或提高性能和安全性的软件修订版、修补程序、服务包、功能包和设备驱动程序的任意集合。|
|更新文件|在计算机上安装更新时所需的文件。|
|更新信息（也称为更新元数据）|有关更新的信息，而不是更新包中的更新二进制文件。 例如，元数据提供更新属性的信息，因此可让你知道该更新的作用。 元数据还包括 Microsoft 软件许可条款。 下载的更新元数据包通常比实际的更新文件包小得多。|
|更新源|Windows Server Update Services (WSUS) 服务器为了获取更新文件而要同步到的位置。 此位置可以是 Microsoft 更新或上游 WSUS 服务器。|
|上游服务器|一台 Windows Server Update Services (WSUS) 服务器，它将更新文件提供给另一台 WSUS 服务器，后者称为下游服务器。|
|Windows 服务器更新服务 (WSUS)|在企业网络中的一台或多台 Windows Server 计算机上运行的服务器角色程序。 WSUS 基础结构允许管理要为网络中的计算机安装的更新。<p>可以使用 WSUS 在发布之前批准或拒绝更新、强制按给定的日期安装更新，并获取有关网络中的每台计算机需要哪些更新的详细报告。 可将 WSUS 配置为自动批准特定的更新种类（关键更新、安全更新、服务包、驱动程序等）。 WSUS 还允许批准仅用于检测的更新，以便可以了解哪些计算机需要特定的更新，而无需安装更新。<p>在 WSUS 实施方案中，网络中必须至少有一台 WSUS 服务器能够连接到 Microsoft 更新以获取可用的更新。 管理员可以根据网络安全性和配置，来确定还有其他多少台服务器可直接连接到 Microsoft 更新。<p>可将 WSUS 服务器配置为通过 Internet 从如下所述的位置获取更新：<p>-   公共 Microsoft 更新<br />-   公共 Windows 更新<br />-   Microsoft Store|
|Windows 更新|**基于 Internet 的 Microsoft 下载站点：** 一个 Microsoft Internet 站点，用于存储和分发 Windows 计算机（设备驱动程序）和 Windows 操作系统的更新。<p>**计算机服务：** 在计算机上运行的 Windows 更新服务的名称。 Windows 更新将在 Windows 计算机上检测、下载和安装更新。<p>根据计算机和策略配置，Windows 更新代理可从以下位置下载更新：<p>-    Microsoft 更新<br />-    Windows 更新<br />-   Microsoft Store<br />-   Internet（网络）更新服务 (WSUS)<p>不在基于 WSUS 的环境中进行管理的计算机通常使用 Windows 更新通过 Internet 直接连接到 Windows 更新、Microsoft 更新或 Microsoft Store，以获取更新。|
|WSUS 客户端|从 WSUS Intranet 更新服务接收更新的计算机。<p>在控制最终用户与自动更新之间的交互的组策略设置中，WSUS 客户端是指 WSUS 环境中的计算机用户。|