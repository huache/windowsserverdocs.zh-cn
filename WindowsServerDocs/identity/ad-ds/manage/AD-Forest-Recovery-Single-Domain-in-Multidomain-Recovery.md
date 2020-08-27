---
title: AD 林恢复-恢复多域林中的单个域
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 267541be-2ea7-4af6-ab34-8b5a3fedee2d
ms.openlocfilehash: 90ff4003373c422797ed7629ba87435efcdfb686
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938877"
---
# <a name="ad-forest-recovery---recovering-a-single-domain-in-a-multidomain-forest"></a>AD 林恢复-恢复多域林中的单个域

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

有时需要仅恢复林中具有多个域的单个域，而不是完全林恢复。 本主题介绍了有关恢复单个域和可能的恢复策略的注意事项。

单域恢复为重建全局编录 (GC) 服务器带来了独特的挑战。 例如，如果从之前创建的备份中还原域的第一个域控制器 (DC) ，则林中的所有其他 Gc 将具有该域的最新数据，而不是还原的 DC。 若要重新建立 GC 数据一致性，有几个选项可供选择：

- Unhost，然后 rehost 已恢复域分区，该分区来自林中的所有 Gc，同时恢复域中的所有 Gc 除外。
- 按照林恢复过程恢复域，然后从其他域的 Gc 中删除延迟对象。

以下各节提供了有关每个选项的一般注意事项。 对于不同 Active Directory 环境，需要执行的完整步骤集将有所不同。

## <a name="rehost-all-gcs"></a>Rehost 所有 Gc

> [!WARNING]
> 所有域的域管理员帐户的密码必须可供使用，以防出现问题，导致无法访问 GC 进行登录。

重新承载可以使用 repadmin/unhost 和 repadmin/rehost 命令来完成所有 Gc， (repadmin/experthelp) 的一部分。 你将在每个未恢复的域中的每个 GC 上运行 repadmin 命令。 需要确保所有 Gc 不再持有已恢复域的副本。 若要实现此目的，请首先从林的所有无恢复域中的所有域控制器 unhost 域分区。 在所有 Gc 不再包含分区后，可以 rehost 它。 在重新承载时，请考虑林的站点和复制结构，例如，在重新承载该站点的其他 Dc 之前，先完成每个站点的一个 DC 的 rehost。

对于每个域只有几个域控制器的小型组织而言，此选项非常有利。 所有 Gc 可以在星期五晚上重建，如有必要，还可以在星期一早上之前完成所有只读域分区的复制。 但是，如果你需要恢复涵盖全球各地站点的大型域，则在其他域的所有 Gc 上重新承载只读域分区会明显影响操作，并且可能需要停机时间。

## <a name="remove-lingering-objects"></a>删除延迟对象

与林恢复过程类似，你可以从需要恢复的域中的备份还原一个 DC，执行剩余 Dc 的元数据清除，然后重新安装 AD DS 来构建域。 在林中所有其他域的 Gc 上，删除已恢复域的只读分区的延迟对象。

延迟对象清理的源必须是已恢复域中的 DC。 若要确保源 DC 没有任何域分区的延迟对象，可以删除全局编录（如果它是 GC）。

对于较大的组织，删除延迟对象非常有利，这些组织不会面临与其他选项相关联的停机时间。

有关详细信息，请参阅 [使用 Repadmin 删除延迟对象](/previous-versions/windows/it-pro/windows-server-2003/cc785298(v=ws.10))。

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
