---
title: AD 林恢复-清除已删除 dc 的元数据
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.assetid: e7543381-4081-407f-adad-a9de792c6616
ms.openlocfilehash: 7128df3559011f882378338c10844b062652bbb2
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87956814"
---
# <a name="ad-forest-recovery---cleaning-metadata-of-removed-writable-domain-controllers"></a>AD 林恢复-清除已删除的可写域控制器的元数据

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

元数据清除会删除将 DC 标识到复制系统的 Active Directory 数据。

使用以下过程删除你计划通过重新安装 AD DS 来重新添加到网络的 dc 的 DC 对象。

如果你使用的是 Active Directory 用户和计算机的版本，或者远程服务器管理工具 (RSAT) 中包含的 Active Directory 站点和服务，则在删除 DC 对象时将自动执行元数据清除。

## <a name="deleting-a-domain-controller-using-active-directory-users-and-computers"></a>使用 Active Directory 用户和计算机删除域控制器

在远程服务器管理工具 (RSAT) 中使用 Active Directory 用户和计算机或 Active Directory 管理中心的版本时，在删除 DC 对象时将自动执行元数据清除。 服务器对象和计算机对象也会自动删除。

作为替代方法，还可以使用 RSAT 中 Active Directory 站点和服务删除 DC 对象。 如果使用 Active Directory 站点和服务，则必须先删除关联的 "服务器对象" 和 "NTDS 设置" 对象，然后才能删除 DC 对象。

有关安装 RSAT 的信息，请参阅文章[远程服务器管理工具](../../../remote/remote-server-administration-tools.md)。

对于运行 Windows Server 2016、2012、2008 R2 或2008的 Dc，以下过程是相同的。 元数据清理操作的目标 DC 可以运行任何版本的 Windows Server。

### <a name="to-delete-a-domain-controller-object-using-active-directory-users-and-computers-in-rsat"></a>使用 RSAT 中的用户和计算机 Active Directory 删除域控制器对象

1. 依次单击 **“开始”**、**“管理工具”** 和 **“Active Directory 用户和计算机”**。
2. 在控制台树中，双击域容器，然后双击**域控制器**组织单位 (OU) 。
3. 在详细信息窗格中，右键单击要删除的 DC，然后单击 "**删除**"。
   ![删除](media/AD-Forest-Recovery-Cleaning-Metadata/delete1.png)
4. 单击“是”**** 以确认删除。 选择 "**此域控制器永久脱机，不能再使用 Active Directory 域服务安装向导 (DCPROMO) 降级**" 复选框，然后单击 "**删除**"。
5. 如果 DC 是全局编录服务器，请单击 **"是"** 确认删除。

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
