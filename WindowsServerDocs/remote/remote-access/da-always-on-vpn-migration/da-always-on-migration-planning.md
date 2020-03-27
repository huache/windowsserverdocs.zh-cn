---
title: 远程访问 Always On VPN 迁移规划
description: 从 DirectAccess 迁移到 Always On VPN 需要进行适当的规划，以确定迁移阶段，这有助于在问题影响到整个组织之前识别任何问题。
manager: dougkim
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: eeca4cf7-90f0-485d-843c-76c5885c54b0
ms.author: lizross
author: eross-msft
ms.date: 05/29/2018
ms.openlocfilehash: 80a7a8b3ee13a9d9cc99b81ab917f6443147565f
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314944"
---
# <a name="plan-the-directaccess-to-always-on-vpn-migration"></a>规划 DirectAccess 到始终启用 VPN 迁移

>适用于: Windows Server (半年频道)、Windows Server 2016、Windows 10

&#171;[**上一步：** DirectAccess Always On VPN 迁移的概述](da-always-on-migration-overview.md)<br>
&#187;[**下一步：** 迁移到 Always On VPN 并解除 DirectAccess](da-always-on-migration-deploy.md)


从 DirectAccess 迁移到 Always On VPN 需要进行适当的规划，以确定迁移阶段，这有助于在问题影响到整个组织之前识别任何问题。 迁移的主要目的是让用户在整个过程中保持与办公室的远程连接。 如果按顺序执行任务，可能会发生争用条件，使远程用户无法访问公司资源。 因此，Microsoft 建议执行从 DirectAccess 到 Always On VPN 的计划的并排迁移。 有关详细信息，请参阅 " [ALWAYS ON VPN 迁移部署](da-always-on-migration-deploy.md)" 部分。

本部分介绍了为迁移、标准配置注意事项和 Always On VPN 功能增强分离用户的好处。 迁移规划阶段包括：

1.  [!INCLUDE [build-migration-rings-shortdesc-include](../includes/build-migration-rings-shortdesc-include.md)]

2.  [!INCLUDE [review-feature-mapping-shortdesc-include](../includes/review-feature-mapping-shortdesc-include.md)] 

3.  [!INCLUDE [review-the-enhancements-shortdesc-include](../includes/review-the-enhancements-shortdesc-include.md)] 

4.  [!INCLUDE [review-the-technology-overview-shortdesc-include](../includes/review-the-technology-overview-shortdesc-include.md)]

## <a name="build-migration-rings"></a>构建迁移环
迁移环用于将 Always On VPN 客户端迁移工作分为多个阶段。 当你到达最后一阶段时，你的流程应经过良好测试和一致。

本部分提供一种将用户划分为迁移阶段，然后管理这些阶段的方法。 无论选择哪种用户阶段分隔方法，都要维护单个 VPN 用户组，以便在迁移完成后更轻松地进行管理。

>[!NOTE] 
>Word_阶段_并不旨在指出这是一个很长的进程。 无论你是在几个月内还是几个月内浏览每个阶段，Microsoft 都建议你充分利用并排迁移并使用分阶段方法。

### <a name="benefits-of-dividing-the-migration-effort-into-multiple-phases"></a>将迁移工作量划分为多个阶段的优点

-   **大容量中断保护。** 通过将迁移划分为多个阶段，迁移生成的问题可能会影响的人员数量大大减少。

-   **从反馈改进流程或通信。** 理想情况下，用户甚至不会注意到发生了迁移。 但是，如果他们的体验不是最佳的，则通过这些使用的反馈可以帮助你改进计划并避免将来出现的问题。

### <a name="tips-for-building-your-migration-ring"></a>构建迁移环的提示

-   **确定远程用户。** 首先，将用户分成两个存储桶：经常进入办公室的人员和不是的人。 对于这两个组，迁移过程是相同的，但远程客户端接收更新的时间可能比连接频率更高的用户需要更长时间。 理想情况下，每个迁移阶段都应包括每个存储桶中的成员。

-  **确定用户的优先级。** 领导和其他影响最大的用户通常在最后迁移的用户中。 但是，在确定用户优先级时，如果客户端计算机的迁移失败，请考虑其业务效率影响。 例如，如果你的评级为1到3，1表示员工将无法工作，3表示无立即发生工作中断，则仅远程使用内部业务线（LOB）应用的业务分析人员应为1，而销售人员则使用云应用程序应为3。

-   **按多个阶段迁移每个部门或业务单位。** Microsoft 强烈建议您不要同时迁移整个部门。 如果出现问题，则不希望它阻碍整个部门的远程工作。 相反，请在至少两个阶段中迁移每个部门或业务单位。

-   **逐渐增加用户计数。** 最常见的迁移方案是从 IT 组织的成员开始，然后移动到业务用户，并遵循领导和其他影响最大的用户。 每个迁移阶段通常都涉及越来越多的人。 例如，第一个阶段可能包含10个用户，最终组可能包括5000个用户。 若要简化部署，请创建单个 VPN 用户安全组，并将用户添加到其阶段。 通过这种方式，您最终会得到一个 VPN 用户组，您可以在以后将成员添加到该组中。

[!INCLUDE [always-on-vpn-standard-config-considerations-include](../includes/always-on-vpn-standard-config-considerations-include.md)]


## <a name="next-step"></a>下一步

|如果你需要…  |然后查看 。  |
|---------|---------|
|开始迁移到 Always On VPN     |[迁移到 ALWAYS ON VPN 并解除 DirectAccess](da-always-on-migration-deploy.md)的授权。 从 DirectAccess 迁移到 Always On VPN 需要一个特定的进程来迁移客户端，这有助于最大程度地减少执行迁移步骤时出现的争用情况。         |
|了解 Always On VPN 和 DirectAccess 的功能    |[ALWAYS ON VPN 和 DirectAccess 的功能比较](../vpn/vpn-map-da.md)。 在以前版本的 Windows VPN 体系结构中，平台限制使得难以提供替换 DirectAccess 所需的关键功能（如用户登录前启动的自动连接）。 但 Always On VPN 已减轻了这些限制或扩展了 DirectAccess 功能之外的 VPN 功能。         |



---