---
ms.assetid: c87dc32d-ab33-44d2-a46f-f9f878b4e5b4
title: 规划部署 AD FS
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 079cf63ba6dcc3b5df08c234ff3ddc5191c6ae75
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938316"
---
# <a name="planning-to-deploy-ad-fs"></a>规划部署 AD FS


收集有关环境的信息并按照 \( \) [Windows Server 2012 中的 AD FS 设计指南](../design/ad-fs-design-guide-in-windows-server-2012.md)中的指南决定 Active Directory 联合身份验证服务 AD FS 设计后，就可以开始规划组织 AD FS 设计的部署。 通过本主题中的完整设计和信息，你可以确定要执行哪些任务来在你的组织中部署 AD FS。

## <a name="reviewing-your-ad-fs-design"></a>审查你的 AD FS 设计
如果为你的组织构造原始 AD FS 设计的设计团队与将实际实现部署的部署团队不同，请确保部署团队与设计团队一起审查最终设计。 请查看有关设计的以下几点：

-   设计团队的策略，用来确定在企业网络或外围网络中的联合服务器位置的最佳物理拓扑。 部署团队可以通过查看 AD FS 设计指南中的下列主题来参考有关该主题的文档：

    -   [AD FS 配置数据库的角色](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)

    -   [规划联合服务器的位置](../design/planning-federation-server-placement.md)

    -   [规划联合服务器代理的位置](../design/planning-federation-server-proxy-placement.md)

    设计团队很可能将联合服务器或联合服务器代理位置的主题留给部署团队。 然后，部署团队将负责编写文档并实现服务器的物理拓扑。

-   你组织的任命（作为声明提供方、信赖方或两者兼具）的业务原因，在记录的 AD FS 设计范围之内。 确保部署团队成员了解部署 AD FS 的原因，以及联合合作关系中涉及的其他公司或组织。 确保部署团队成员还了解对其他公司或组织的 \( 有限硬件、没有 extranet 环境等的约束， \) 可能会以某种方式限制设计的范围。 有关伙伴组织的详细信息，请参阅[规划部署](../design/planning-your-deployment.md)。

设计团队和部署团队在这些问题上达成一致后，他们可以继续部署 AD FS 的设计。 有关详细信息，请参阅[实现你的 AD FS 设计规划](Implementing-Your-AD-FS-Design-Plan.md)。
