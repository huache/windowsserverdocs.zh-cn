---
title: AD 林恢复-删除全局编录
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 60087a62-11e6-4750-a70e-510f35315688
ms.openlocfilehash: e24449f2debdeeaf1e0ccdaf51a44d041c7dcc61
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941577"
---
# <a name="ad-forest-recovery---removing-the-global-catalog"></a>AD 林恢复-删除全局编录

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

 使用以下过程从 DC 中删除全局编录。

 从备份中还原全局编录服务器可能导致全局编录包含其部分副本（而不是该部分副本的权威域）的更新数据。 在这种情况下，将不会从全局编录中删除较新的数据，甚至可以将其复制到其他全局编录服务器。 因此，即使你确实还原了作为全局编录服务器的 DC，不管是由你信任的孤立备份，还是在还原操作完成后，你都应该立即删除全局编录服务器。 删除全局编录后，计算机会删除其所有部分副本。

## <a name="to-remove-the-global-catalog-using-active-directory-sites-and-services"></a>使用 Active Directory 站点和服务删除全局编录

1. 打开服务器管理器，单击 " **工具** "，然后单击 " **Active Directory 站点和服务**"。
2. 在控制台树中，展开 " **站点** " 容器，然后选择包含目标服务器的相应站点。
3. 展开 " **服务器** " 容器，然后展开要从中删除全局编录的 DC 的 *服务器* 对象。
4. 右键单击 " **NTDS 设置**"，然后单击 " **属性**"。
5. 清除 " **全局编录** " 复选框。
   ![删除 GC](media/AD-Forest-Recovery-Remove-GC/removegc1.png)
6. 单击“应用”。

## <a name="to-remove-the-global-catalog-using-repadmin"></a>使用 Repadmin 删除全局编录

打开提升的命令提示符，键入以下命令，然后按 ENTER：

   ```
   repadmin.exe /options DC_NAME –IS_GC
   ```

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
