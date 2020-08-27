---
ms.assetid: c8597cc8-bdcb-4e59-a09e-128ef5ebeaf8
title: 命令行进程审核
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 12bf07aa5fb60f18cdd5b04b7d7f91c00388ed42
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88939567"
---
# <a name="command-line-process-auditing"></a>命令行进程审核

>适用于： Windows Server 2016、Windows Server 2012 R2

**作者**： Justin Turner，具有 Windows 组的高级支持升级工程师

> [!NOTE]
> 本内容由 Microsoft 客户支持工程师编写，适用于正在查找比 TechNet 主题通常提供的内容更深入的有关 Windows Server 2012 R2 中的功能和解决方案的技术说明的有经验管理员和系统架构师。 但是，它未经过相同的编辑审批，因此某些语言可能看起来不如通常在 TechNet 上找到的内容那么精练。

## <a name="overview"></a>概述

-   预先存在的进程创建审核事件 ID 4688 现在包含命令行进程的审核信息。

-   它还将在 Applocker 事件日志中记录可执行文件的 SHA1/2 哈希

    -   应用程序和服务 Logs\Microsoft\Windows\AppLocker

-   通过 GPO 启用，但默认情况下禁用

    -   "在进程创建事件中包含命令行"

![命令行审核](media/Command-line-process-auditing/GTR_ADDS_Event4688.gif)

**图 SEQ 图 \\ \* 阿拉伯16事件4688**

在 REF _Ref366427278 \h 图16中查看更新的事件 ID 4688。  在此更新之前，将不会记录 **处理命令行** 的任何信息。  由于这种附加日志记录，我们现在可以看到，不仅 wscript.exe 进程已启动，而且还用于执行 VB 脚本。

## <a name="configuration"></a>配置
若要查看此更新的效果，你将需要启用两个策略设置。

### <a name="you-must-have-audit-process-creation-auditing-enabled-to-see-event-id-4688"></a>您必须启用审核过程创建审核才能看到事件 ID 4688。
若要启用审核过程创建策略，请编辑以下组策略：

**策略位置：** > 策略 > Windows 设置的计算机配置 > 安全设置 > 高级审核配置 > 详细跟踪

**策略名称：** 审核进程创建

**支持：** Windows 7 及更高版本

**Description/Help：**

此安全策略设置确定在创建进程时操作系统是否生成审核事件 (启动) 和创建该进程的程序或用户的名称。

这些审核事件有助于您了解计算机的使用方式和跟踪用户活动的方式。

事件量：从低到低，具体取决于系统使用情况

**默认值：** 未配置

### <a name="in-order-to-see-the-additions-to-event-id-4688-you-must-enable-the-new-policy-setting-include-command-line-in-process-creation-events"></a>若要查看对事件 ID 4688 的添加操作，必须启用新策略设置：在进程创建事件中包括命令行
**表 SEQ 表 \\ \* 阿拉伯语19命令行进程策略设置**

|策略配置|详细信息|
|------------------------|-----------|
|**路径**|管理 Templates\System\Audit 进程创建|
|**设置**|**在进程创建事件中包含命令行**|
|**默认设置**|未配置 (未启用) |
|**在以下设备上受支持：**|?|
|**说明**|此策略设置确定在创建新进程时安全审核事件中记录的信息。<p>仅当启用了审核过程创建策略时，此设置才适用。 如果启用此策略设置，则在应用此策略设置的工作站和服务器上，将在安全事件日志中以纯文本形式记录每个进程的命令行信息，作为审核过程创建事件4688的一部分。<p>如果禁用或未配置此策略设置，则将不会在审核过程创建事件中包括进程的命令行信息。<p>默认：未配置<p>注意：如果启用此策略设置，则具有 "读取安全事件" 权限的任何用户都可以读取任何成功创建的进程的命令行参数。 命令行参数可能包含敏感信息或私有信息，如密码或用户数据。|

![命令行审核](media/Command-line-process-auditing/GTR_ADDS_IncludeCLISetting.gif)

当使用“高级审核策略配置”设置时，您需要确认这些设置不会被基本审核策略设置覆盖。  当覆盖设置时，将记录事件4719。

![命令行审核](media/Command-line-process-auditing/GTR_ADDS_Event4719.gif)

以下过程显示了如何通过阻止应用任何基本审核策略设置来避免冲突。

### <a name="to-ensure-that-advanced-audit-policy-configuration-settings-are-not-overwritten"></a>确保“高级审核策略配置”设置不被覆盖
![命令行审核](media/Command-line-process-auditing/GTR_ADDS_AdvAuditPolicy.gif)

1.  打开组策略管理控制台

2.  右键单击“默认域策略”，然后单击“编辑”。

3.  依次双击 “计算机配置”、 “策略”和 “Windows 设置”。

4.  双击 "安全设置"，双击 "本地策略"，然后单击 "安全选项"。

5.  双击“审核: 强制审核策略子类别设置(Windows Vista 或更高版本)替代审核策略类别设置”，然后单击“定义此策略设置”。

6.  单击 “启用”，然后单击 “确定”。

## <a name="additional-resources"></a>其他资源
[审核进程创建](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd941613(v=ws.10))

[高级安全审核策略循序渐进指南](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd408940(v=ws.10))

[AppLocker：常见问题](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee619725(v=ws.10))

## <a name="try-this-explore-command-line-process-auditing"></a>请尝试执行以下操作：浏览命令行进程审核

1.  启用 **审核进程创建** 事件，并确保未覆盖高级审核策略配置

2.  创建一个脚本，该脚本将生成一些相关事件并执行该脚本。  观察事件。  本课程中用于生成事件的脚本如下所示：

    ```
    mkdir c:\systemfiles\temp\commandandcontrol\zone\fifthward
    copy \\192.168.1.254\c$\hidden c:\systemfiles\temp\hidden\commandandcontrol\zone\fifthward
    start C:\systemfiles\temp\hidden\commandandcontrol\zone\fifthward\ntuserrights.vbs
    del c:\systemfiles\temp\*.* /Q
    ```

3.  启用命令行进程审核

4.  执行与之前相同的脚本并观察事件

