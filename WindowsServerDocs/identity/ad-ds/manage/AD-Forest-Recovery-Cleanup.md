---
title: AD 林恢复-清理
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 5a291f65-794e-4fc3-996e-094c5845a383
ms.openlocfilehash: 831f83d75ef7c5f866a499943a94940027cda67d
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938917"
---
# <a name="ad-forest-recovery---cleanup"></a>AD 林恢复-清理

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

 根据需要执行以下恢复后步骤：

- 恢复整个林后，可以恢复到原始 DNS 配置，包括每个 Dc 上首选和备用 DNS 服务器的配置。 将 DNS 服务器配置为在出现故障之前，将还原以前的名称解析功能。 删除未恢复的 Dc 的任何 DNS 记录。
- 删除 Windows Internet 名称服务 () 尚未恢复的所有 Dc 的 WINS 记录。
- 你可以将操作主机角色转移到域或林中的其他 Dc，并基于故障之前的配置添加更多的全局编录服务器。
- 由于整个林将还原到以前的状态，因此 (的任何对象（如用户和计算机) 已添加）和所有更新 (如在此点后对现有对象所做的密码更改) 。 因此，您应该重新创建这些缺少的对象并根据需要重新应用缺少的更新。
- 你可能还需要通过外部域和林还原传出信任，因为这些外部信任关系不会从备份中自动还原。

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
