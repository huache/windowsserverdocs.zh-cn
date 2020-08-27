---
title: AD 林恢复-使 RID 池失效
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 2f5f84df-bd85-4ca4-bdd3-835bd1d45c11
ms.openlocfilehash: 36919eb4f4e67129446975f9c8c4d60fd64cc499
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88939637"
---
# <a name="ad-forest-recovery---invalidating-the-current-rid-pool"></a>AD 林恢复-使当前 RID 池失效

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

使用以下过程向我们的 Windows PowerShell 使域控制器上的当前 RID 池失效。 默认情况下，windows PowerShell 在 Windows Server 2012 和 Windows Server 2008 R2 上处于启用状态，但 windows Server 2008 却不能通过使用 " **添加功能**" 安装。 可以将其 [下载](https://www.microsoft.com/download/details.aspx?id=20020) 到在 Windows Server 2003 上运行。

若要验证命令是否已成功完成，请检查事件 ID 16654 (源是否) Windows Server 2012 中事件查看器的系统日志中。 Windows 的早期版本不会记录此事件。

> [!NOTE]
> 使 RID 池无效后，在第一次尝试创建安全主体 (用户、计算机或组) 时，会收到错误。 尝试创建对象会触发对新 RID 池的请求。 重试操作成功，因为将分配新的 RID 池。

## <a name="to-invalidate-the-current-rid-pool"></a>使当前 RID 池无效

- 打开提升的 Windows PowerShell 会话，运行以下命令并按 ENTER：

   ```powershell
   $Domain = New-Object System.DirectoryServices.DirectoryEntry
   $DomainSid = $Domain.objectSid
   $RootDSE = New-Object System.DirectoryServices.DirectoryEntry("LDAP://RootDSE")
   $RootDSE.UsePropertyCache = $false
   $RootDSE.Put("invalidateRidPool", $DomainSid.Value)
   $RootDSE.SetInfo()
   ```

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
