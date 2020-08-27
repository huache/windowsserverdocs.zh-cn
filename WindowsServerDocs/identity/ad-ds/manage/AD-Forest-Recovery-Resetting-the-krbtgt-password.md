---
title: AD 林恢复-正在重置 krbtgt 密码
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 3bd6c1d0-d316-4b03-b7b4-557d4537635c
ms.openlocfilehash: 1b2183d9a695da274d0f51e46b70a0cfe002a020
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938177"
---
# <a name="ad-forest-recovery---resetting-the-krbtgt-password"></a>AD 林恢复-正在重置 krbtgt 密码

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

使用以下过程为域重置 krbtgt 密码。 下面的过程适用于只读域控制器 (Rodc) 。

> [!IMPORTANT]
> 如果计划在林恢复期间联机恢复 Rodc，请不要删除 Rodc 的 krbtgt 帐户。 RODC 的 krbtgt 帐户以格式 krbtgt_*号*列出。
>
> 如果在 DC 上使用自定义的密码筛选器 (例如 passfilt.dll) ，则在尝试重置 krbtgt 密码时可能会收到错误。 有关详细信息，包括解决方法，请参阅 Microsoft 知识库 [文章 2549833](https://support.microsoft.com/kb/2549833) (https://support.microsoft.com/kb/2549833) 。

## <a name="to-reset-the-krbtgt-password"></a>重置 krbtgt 密码

1. 单击 " **开始**"，指向 **"控制面板**"，指向 " **管理工具**"，然后单击 " **Active Directory 用户和计算机**"。
2. 单击“查看” ****，然后单击“高级功能” ****。
3. 在控制台树中，双击域容器，然后单击 " **用户**"。
4. 在详细信息窗格中，右键单击 **krbtgt** 用户帐户，然后单击 " **重置密码**"。
   ![重置密码](media/AD-Forest-Recovery-Resetting-the-krbtgt-password/resetpass1.png)
5. 在 " **新密码**" 中，键入新密码，在 " **确认密码**" 中再次键入密码，然后单击 **"确定"**。 指定的密码不是很重要，因为系统将自动独立于指定的密码生成强密码。

> [!NOTE]
> 你应执行两次此操作。 Krbtgt 帐户的密码历史记录是两个，这意味着它包含两个最新的密码。 通过重置密码两次，可以有效地清除历史记录中的任何旧密码，因此无法使用旧密码将其他 DC 与此 DC 进行复制。

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
