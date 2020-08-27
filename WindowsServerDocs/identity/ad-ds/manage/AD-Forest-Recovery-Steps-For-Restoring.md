---
title: AD 林恢复-用于还原林的步骤
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 5a291f65-794e-4fc3-996e-094c5845a383
ms.openlocfilehash: b6dbd22eb34578013f90dda937ec1c26fe8fbf4e
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938857"
---
# <a name="ad-forest-recovery---steps-for-restoring-the-forest"></a>AD 林恢复-用于还原林的步骤

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

本部分概述了用于恢复林的推荐路径。 稍后将详细介绍林恢复步骤。

以下列表汇总了高级别的恢复步骤：

1. [识别问题](AD-Forest-Recovery-Identify-the-Problem.md)

   使用它和 Microsoft 支持部门来确定问题的范围和可能的原因，并评估所有业务利益干系人可能的补救措施。 在许多情况下，林完全恢复总计应为最后一个选项。

2. [决定如何恢复林](AD-Forest-Recovery-Determine-how-to-Recover.md)

   确定林恢复是必需的后，请完成准备工作的预备步骤：确定当前林结构，确定每个 DC 执行的功能，确定要为每个域还原哪个 DC，并确保所有可写 Dc 都处于脱机状态。

3. [执行初始恢复](AD-Forest-Recovery-Perform-initial-recovery.md)

   隔离时，为每个域恢复一个 DC，对其进行清理，然后重新连接到域。 重置特权帐户，并纠正此阶段的安全漏洞导致的问题。

4. [重新部署剩余 Dc](AD-Forest-Recovery-Restore-Additional-DCs.md)

   重新部署林，使其返回到失败之前的状态。 需要根据具体的设计和要求调整此步骤。 虚拟化域控制器克隆有助于加速此过程。

5. [清理](AD-Forest-Recovery-Cleanup.md)

   还原功能后，根据需要重新配置名称解析，并使 LOB 应用程序正常工作。

本指南中的步骤旨在最大程度地减少将危险数据重新引入到已恢复的林中。 可能需要修改这些步骤，以考虑以下因素：

- 可伸缩性
- 远程管理
- 恢复速度
