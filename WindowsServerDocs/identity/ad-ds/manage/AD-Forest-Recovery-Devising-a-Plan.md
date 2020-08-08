---
title: AD 林恢复-设计 AD 林恢复计划
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 17381f30-55f2-4e00-977a-b701675fa4ff
ms.openlocfilehash: d6637f92dff1542837b42a1406a17555a753bf86
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972314"
---
# <a name="ad-forest-recovery---devising-an-ad-forest-recovery-plan"></a>AD 林恢复-设计 AD 林恢复计划

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

根据你的环境和业务要求，你可能需要也可能不需要执行本指南中所述的所有步骤来执行成功的林恢复。 由于本指南仅用作林恢复模板，因此必须设计适合你的环境并满足你的业务需求的自定义林恢复计划。

例如，在林恢复计划中，你应该有一个林详细的拓扑图。 该映射应列出 Dc 的所有信息，例如其名称、其角色和备份状态以及它们之间的信任关系。 有关可用于创建拓扑图的工具，请参阅[Microsoft Active Directory 拓扑 Diagrammer](https://www.microsoft.com/download/details.aspx?id=13380)。

你应每年至少使用一次林恢复计划。 此外，当企业管理员组或域管理员组的成员身份发生变化时，最好执行林恢复演练。 这有助于确保信息技术) 的人员充分了解林恢复计划 (。

## <a name="next-steps"></a>后续步骤

- [AD 林恢复 - 先决条件](AD-Forest-Recovery-Prerequisties.md)
- [AD 林恢复-设计自定义林恢复计划](AD-Forest-Recovery-Devising-a-Plan.md)
- [AD 林恢复-识别问题](AD-Forest-Recovery-Identify-the-Problem.md)
- [AD 林恢复-确定如何恢复](AD-Forest-Recovery-Determine-how-to-Recover.md)
- [AD 林恢复-执行初始恢复](AD-Forest-Recovery-Perform-initial-recovery.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
- [AD 林恢复-常见问题](AD-Forest-Recovery-FAQ.md)
- [AD 林恢复-恢复多域林中的单个域](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)
- [AD 林恢复-通过 Windows Server 2003 域控制器恢复林](AD-Forest-Recovery-Windows-Server-2003.md)
