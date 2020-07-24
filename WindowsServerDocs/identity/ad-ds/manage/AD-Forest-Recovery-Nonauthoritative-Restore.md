---
title: AD 林恢复-非权威还原
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: e4ce1d18-d346-492a-8bca-f85513aa3ac1
ms.technology: identity-adds
ms.openlocfilehash: 52c3e4fb20009a37a7f778907639390f9b00cfcb
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86960949"
---
# <a name="performing-a-nonauthoritative-restore-of-active-directory-domain-services"></a>执行 Active Directory 域服务的非权威还原 

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

若要执行非权威还原，请完成以下过程。  
  
以下过程使用 Wbadmin.exe 执行 Active Directory 或 Active Directory 域服务（AD DS）的非权威还原。 如果你使用的是其他备份解决方案，或者你打算稍后在林恢复过程中完成 SYSVOL 的权威还原，则可以使用以下替代方法执行 SYSVOL 的权威还原：  
  
- 如果你使用文件复制服务（FRS）来复制 SYSVOL，请按照 Microsoft 知识库[文章 290762](https://go.microsoft.com/fwlink/?LinkId=148443)中的步骤操作，使用**BurFlags**注册表项重新初始化 FRS 副本集，或在必要时使用文章 315457 [315457](https://support.microsoft.com/kb/315457)来重建 sysvol 树。 若要确定 FRS 是否复制了 SYSVOL，请参阅[确定 DFSR 或 Frs 是否复制域控制器的 SYSVOL 文件夹](/windows/win32/vss/backing-up-and-restoring-an-frs-replicated-sysvol-folder#determining_whether_a_domain_controller_s_sysvol_folder_is_replicated_by_dfsr_or_frs)。  
- 如果使用分布式文件系统（DFS）复制来复制 SYSVOL，请参阅[执行 DFSR 复制的 sysvol 的权威同步](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md)。  

## <a name="performing-a-nonauthoritative-restore"></a>执行非权威还原

使用以下过程，通过在运行 Windows Server 2012、Windows Server 2008 R2 或 Windows Server 2008 的 DC 上使用 wbadmin.exe，同时执行 AD DS 和 SYSVOL 的权威还原。 备份必须显式包含系统状态数据;用于完全服务器恢复的完整服务器备份将不起作用。 有关创建系统状态备份的详细信息，请参阅[备份系统状态数据](AD-Forest-Recovery-Backing-up-System-State.md)。  
  
### <a name="to-perform-a-nonauthoritative-restore-of-ad-ds-and-authoritative-restore-of-sysvol-using-wbadminexe"></a>使用 wbadmin.exe 执行 AD DS 和权威还原 SYSVOL 的非权威还原  
  
- 在恢复命令中包含 **-authsysvol**开关，如以下示例中所示：  

   ```  
   wbadmin start systemstaterecovery <otheroptions> -authsysvol  
   ```  

   例如：  

   ```  
   wbadmin start systemstaterecovery -version:11/20/2012-13:00 -authsysvol  
   ```  
  
![还原](media/AD-Forest-Recovery-Nonauthoritative-Restore/nonauth.png)

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
