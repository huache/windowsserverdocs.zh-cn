---
title: AD 林恢复-备份完整服务器
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 398918dc-c8ab-41a6-a377-95681ec0b543
ms.technology: identity-adds
ms.openlocfilehash: 3792a1e9b5c8978fdc8db5201ff4d439dbfb98d6
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519014"
---
# <a name="ad-forest-recovery---backing-up-a-full-server"></a>AD 林恢复-备份完整服务器

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

建议使用完整服务器备份来准备林恢复，因为它可以还原到不同的硬件或不同的操作系统实例。  使用 Windows Server 备份可以对服务器执行完整备份。

## <a name="windows-server-backup"></a>Windows Server Backup

默认情况下不安装 Windows Server Backup。 在 Windows Server 2016 和 Windows Server 2012 R2 中，按照以下步骤安装它。

>[!NOTE]
>请注意，Windows Server 2016 和 Windows Server 2012 R2 的步骤可能略有不同。

有关在 Windows Server 2008 和 Windows Server 2008 R2 中安装它的步骤，请参阅[安装 Windows Server 备份](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771232(v=ws.10))。

### <a name="to-install-windows-server-backup"></a>安装 Windows Server 备份

1. 打开**服务器管理器**，然后单击 "**添加角色和功能**"。
2. 在 "**添加角色和功能向导**" 中，单击 "**下一步**"。
3. 在 "**安装类型**" 屏幕上，保留默认的**基于角色或基于功能的安装**，然后单击 "**下一步**"。
4. 在**服务器选择**屏幕上，单击 "**下一步**"。
5. 在 "**服务器角色**" 屏幕上，单击 "**下一步**"。
6. 在 "**功能**" 屏幕上，选择**Windows Server 备份**然后单击 "**下一步**" 
    ![ 安装备份](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup2.png)
7. 单击“安装”  。
8. 安装完成后，单击 "**关闭**"。

### <a name="to-perform-a-backup-with-windows-server-backup"></a>使用 Windows Server 备份执行备份

1. 打开**服务器管理器**，单击 "**工具**"，然后单击 " **Windows Server 备份**"。
   - 在 Windows Server 2008 R2 和 Windows Server 2008 中，单击 "**开始**"，指向 "**管理工具**"，然后单击 " **Windows Server 备份**"。

   ![安装备份](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup1.png)

2. 如果系统提示，请在 "**用户帐户控制**" 对话框中提供备份操作员凭据，然后单击 **"确定"**。
3. 单击 "**本地备份**"。
4. 在 **“操作”** 菜单中，单击 **“一次性备份”**。
5. 在 "一次性备份" 向导中的 "**备份选项**" 页上，单击 "**其他选项**"，然后单击 "**下一步**"。

   ![安装备份](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup3.png)

6. 在 "**选择备份配置**" 页上，单击 "**完全服务器（推荐）**"，然后单击 "**下一步**"。
7. 在 "**指定目标类型**" 页上，单击 "**本地驱动器**" 或 "**远程共享文件夹**"，然后单击 "**下一步**"。
8. 在 "**选择备份目标**" 页上，选择备份位置。  如果选择了本地驱动器，请选择本地驱动器，或者如果选择了远程共享，请选择网络共享。
9. 在确认屏幕上，单击 "**备份**"。

   ![安装备份](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup4.png)

10. 完成此完成后，单击 "**关闭**"。
11. 关闭 Windows Server 备份。

>[!NOTE]
>如果收到一条错误消息，指出没有可用的备份存储位置，则需要排除已选择的某个卷，或添加新的卷或远程共享。
>如果收到一条警告，指出选定的卷也包含在要备份的项列表中，则确定是否删除并单击 **"确定"**。

## <a name="using-wbadminexe-to-backup-a-windows-server"></a>使用 Wbadmin.exe 来备份 windows server

Wbadmin.exe 是一种命令行实用工具，可用于在命令提示符下备份和还原操作系统、卷、文件、文件夹和应用程序。

### <a name="to-perform-a-full-server-backup-using-wbadminexe"></a>使用 Wbadmin.exe 执行完整服务器备份

- 打开提升的命令提示符，键入以下命令并按 ENTER：

   ```
   wbadmin start backup -backuptarget:<Drive_letter_to store_backup>: -include:<Drive_letter_to_include>:
   ```

   ![安装备份](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup5.png)

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
