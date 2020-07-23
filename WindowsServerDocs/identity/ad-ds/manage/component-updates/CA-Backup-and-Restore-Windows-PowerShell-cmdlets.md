---
ms.assetid: 7e195f5b-b194-40f3-a26d-5cf4ade5fc4d
title: CA 备份和还原 Windows PowerShell cmdlet
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 02393a7f34e20b50b60a738ceb0f5f3a2ac17990
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958639"
---
# <a name="ca-backup-and-restore-windows-powershell-cmdlets"></a>CA 备份和还原 Windows PowerShell cmdlet

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012
> 
> **作者**： Justin Turner，具有 Windows 组的高级支持升级工程师  
> 
> [!NOTE]
> 本内容由 Microsoft 客户支持工程师编写，适用于正在查找比 TechNet 主题通常提供的内容更深入的有关 Windows Server 2012 R2 中的功能和解决方案的技术说明的有经验管理员和系统架构师。 但是，它未经过相同的编辑审批，因此某些语言可能看起来不如通常在 TechNet 上找到的内容那么精练。  
  
## <a name="overview"></a>概述  
Windows Server 2012 中引入了 ADCSAdministration Windows PowerShell 模块。  Windows Server 2012 R2 中向此模块添加了两个新的 cmdlet，以支持 CA 的备份和还原。  
  
-   Backup-CARoleService  
  
-   Restore-CARoleService  
  
## <a name="backup-caroleservice"></a>Backup-CARoleService  
**表 SEQ 表 \\ \* 阿拉伯语17：备份和还原 Windows PowerShell cmdlet**  
  
**ADCSAdministration Cmdlet：备份-Backup-caroleservice**  
  
|参数-需要**粗体**参数|说明|  
|------------------------------------------------|---------------|  
|**-路径**|-String-保存备份的位置<br />-这是唯一未命名的参数<br />-位置参数<p>**示例：**<p>Backup-caroleservice-Path c:\adcsbackup1<p>备份-Backup-caroleservice c:\adcsbackup2|  
|-KeyOnly|-备份不包含数据库的 CA 证书<p>**示例：**<p>Backup-caroleservice c:\adcsbackup3-KeyOnly|  
|-Password|-指定用于保护 CA 证书和私钥的密码<br />-必须是安全字符串<br />-DatabaseOnly 参数无效<p>示例：<p>Backup-caroleservice c:\adcsbackup4-Password （Read-Host-prompt "Password："-AsSecureString）<p>Backup-caroleservice c:\adcsbackup5-Password （Convertto-html-SecureString "Pa55w0rd！" -AsPlainText-Force）|  
|-DatabaseOnly|-不带 CA 证书备份数据库<p>Backup-caroleservice c:\adcsbackup6-DatabaseOnly|  
|-Force|1. 允许您覆盖在-Path 参数中指定的位置预先存在的备份。<p>Backup-caroleservice c:\adcsbackup1-Force|  
|-增量|-执行增量备份<p>Backup-caroleservice c:\adcsbackup7-增量备份|  
|-KeepLog|1. 指示命令保留日志文件。 如果未指定开关，则默认情况下会截断日志文件，但在增量方案中除外<p>Backup-caroleservice c:\adcsbackup7-KeepLog|  
  
### <a name="-password-secure-string"></a>-Password <Secure String>  
如果使用了-Password 参数，则提供的密码必须是安全字符串。  使用 "**读取主机**" cmdlet 启动安全密码条目的交互式提示，或使用**convertto-html-SecureString** cmdlet 来指定密码。  
  
查看以下示例  
  
**使用读取主机为密码参数指定一个安全字符串**  
  
```powershell  
Backup-CARoleService c:\adcsbackup4 -Password (Read-Host -prompt "Password:" -AsSecureString)  
```  
  
**使用 Convertto-html-SecureString 为 Password 参数指定一个安全字符串**  
  
```powershell  
Backup-CARoleService c:\adcsbackup5 -Password (ConvertTo-SecureString "Pa55w0rd!" -AsPlainText -Force)  
```  
  
## <a name="restore-caroleservice"></a>Restore-CARoleService  
**ADCSAdministration Cmdlet： Restore-Backup-caroleservice**  
  
|参数-需要**粗体**参数|说明|  
|------------------------------------------------|---------------|  
|**-路径**|-String-要从中还原备份的位置<br />-这是唯一未命名的参数<br />-位置参数<p>**示例：**<p>Backup-caroleservice.-Path c:\adcsbackup1-Force<p>Backup-caroleservice c:\adcsbackup2-Force|  
|-KeyOnly|-不在数据库的情况下还原 CA 证书<br />-如果备份是通过-KeyOnly 选项创建的，则必须指定-<p>**示例：**<p>Backup-caroleservice c:\adcsbackup3-KeyOnly-Force|  
|-Password|-指定 CA 证书和私钥的密码<br />-必须是安全字符串<p>**示例：**<p>Backup-caroleservice c:\adcsbackup4-Password （read-host-prompt "Password："-AsSecureString）-Force<p>Backup-caroleservice c:\adcsbackup5-Password （Convertto-html-SecureString "Pa55w0rd！" -AsPlainText）-Force|  
|-DatabaseOnly|-不带 CA 证书还原数据库<p>Backup-caroleservice c:\adcsbackup6-DatabaseOnly|  
|-Force|-用于覆盖预先存在的密钥<br />-可选参数，但在就地还原时，可能需要<p>Backup-caroleservice c:\adcsbackup1-Force|  
  
### <a name="issues"></a>问题  
如果在将备份-Backup-caroleservice 与-Password 参数一起使用时，Convertto-html-SecureString 函数失败，则会执行非密码保护的备份。  
  
![CA 备份和还原](media/CA-Backup-and-Restore-Windows-PowerShell-cmdlets/GTR_ADDS_BackupCARole.gif)  
  
**表 SEQ 表 \\ \* 阿拉伯语18：常见错误**  
  
|操作|错误|注释|  
|----------|---------|-----------|  
|**Backup-caroleservice C:\ADCSBackup**|Backup-caroleservice：该进程无法访问文件，因为另一个进程正在使用该文件。 （异常来自 HRESULT：<p>0x80070020|在运行 Backup-caroleservice cmdlet 之前停止 Active Directory 证书服务服务|  
|**Backup-caroleservice C:\ADCSBackup**|Backup-caroleservice：目录不为空。 （异常来自 HRESULT：0x80070091）|使用-Force 参数覆盖预先存在的密钥|  
|**Backup-caroleservice C:\ADCSBackup-Password （Read-Host-Prompt "Password："-AsSecureString）-DatabaseOnly**|Backup-caroleservice：无法使用指定的命名参数解析参数集。|-Password 参数仅用于对私钥进行密码保护，因此在不进行备份时无效。|  
|**Backup-caroleservice C:\ADCSBack15-Password （Read-Host-Prompt "Password："-AsSecureString）-DatabaseOnly**|Backup-caroleservice：无法使用指定的命名参数解析参数集。|-Password 参数仅用于对私钥进行密码保护，因此在不还原私钥时无效|  
|**Backup-caroleservice C:\ADCSBack14-Password （Read-Host-Prompt "Password："-AsSecureString）**|Backup-caroleservice：系统找不到指定的文件。 （异常来自 HRESULT：0x80070002）|指定的路径不包含有效的数据库备份。  也许路径无效，或者备份是通过-KeysOnly 选项创建的吗？|  
  
## <a name="additional-resources"></a>其他资源  
[Active Directory 证书服务迁移指南](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee126170(v=ws.10))  
  
[备份 CA 数据库和私钥](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee126140(v=ws.10)#BKMK_BackUpDB)  
  
[在目标服务器上还原 CA 数据库和配置](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee126140(v=ws.10)#BKMK_RestoreCA)  
  
## <a name="try-this-backup-the-ca-in-your-lab-using-windows-powershell"></a>请尝试以下操作：使用 Windows PowerShell 在实验室中备份 CA  
  
1.  使用本课中的命令备份使用密码保护的 CA 数据库和私钥。  
  
2.  暂时保留 CA 的还原。  
  
