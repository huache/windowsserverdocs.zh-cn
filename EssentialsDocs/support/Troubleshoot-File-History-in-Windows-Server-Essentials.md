---
title: 解决 Windows Server Essentials 中的文件历史记录问题
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: ed062945-27e9-4572-b1bb-6c8cf1b9c2f4
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 90f931c128d4e4eb9747203db7d097c68d451702
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625204"
---
# <a name="troubleshoot-file-history-in-windows-server-essentials"></a>解决 Windows Server Essentials 中的文件历史记录问题

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

## <a name="troubleshoot-issues-with-user-file-history-backups"></a>解决用户文件历史记录备份问题
 在为已添加到运行 Windows Server Essentials 的服务器的用户或计算机管理文件历史记录备份时，可能出现下列问题。

### <a name="file-history-data-is-not-automatically-deleted"></a>文件历史记录数据没有自动删除
 在以下情况下，文件历史记录数据可能不会被自动删除：

- 删除用户帐户时，可以选择不删除用户帐户的文件历史记录数据，并选择手动删除数据。

- 当你尝试删除文件历史记录数据时，文件历史记录数据正由其他进程使用。

  若要解决此问题，你必须使用以下过程手动删除文件历史记录：

####  <a name="to-manually-delete-file-history-backups-for-a-user-or-a-computer"></a><a name="BKMK_manuallyDelete"></a> 手动删除用户或计算机的文件历史记录备份

1.  以管理员身份登录到服务器。

2.  以管理员身份运行文件资源管理器。

3.  导航到文件历史记录备份文件夹。 默认位置为 C:\ServerFolders\File History Backups。

4.  删除存储文件历史记录备份的共享文件夹：

    -   若要删除用户的文件历史记录，请删除具有该用户名的文件历史记录备份子文件夹。

    -   若要删除计算机的文件历史记录，请删除具有该计算机名的文件历史记录备份子文件夹。 例如，如果用户在 \> 开始使用新的便携式计算机之后 <MyComputer01，则 <MyComputer02，则在 \> \\ \> \\ \> 验证用户是否已将所有文件和文件夹传输到新的便携式计算机并在将来不需要文件历史记录的情况下，你可以删除 c:\serverfolders\file history backups 历史记录备份<我的帐户<MyComputer01。

### <a name="cannot-apply-file-history-setting-to-a-new-user"></a>无法对新用户应用文件历史记录设置
 如果你添加了一位新用户，而其用户名与已从 Windows Server Essentials 中删除的用户的用户名完全相同，则当 Windows Server Essentials 尝试创建一个用于存储新用户的文件历史记录的文件夹时，新用户的文件历史记录配置可能会因命名冲突而失败。 若要解决此问题，你可以重命名已删除用户的文件历史记录文件夹。

##### <a name="to-locate-user-file-history-on-the-server"></a>查找服务器上的用户文件历史记录

1.  以管理员身份登录到服务器。

2.  在 Windows Server Essentials 仪表板上单击“存储”****。

3.  在“服务器文件夹”**** 选项卡上，记下文件历史记录备份文件夹的位置。 默认位置为%SystemDrive%\ServerFolders\File History backup \\ 。

##### <a name="to-resolve-file-history-issues-for-a-new-user-with-a-name-conflict"></a>为名称冲突的新用户解决文件历史记录问题

1.  以管理员身份登录到服务器。

2.  以管理员身份运行文件资源管理器。

3.  导航到文件历史记录备份文件夹。 默认位置为 C:\ServerFolders\File History Backups。

     每个已添加到 Windows Server Essentials 的用户帐户的文件历史记录备份文件夹都包含一个子文件夹。 例如，用户 John Smith 的文件历史记录将存储在 File History Backups\JohnSmith 子文件夹中。

4.  重命名已删除用户的子文件夹，例如， ** < *用户名*>_Deleted**。 如果不再需要该用户的文件历史记录，可删除该文件夹。

5. 现在可以添加新用户。 有关说明，请参阅添加用户帐户？在 " [管理用户帐户](../manage/Manage-User-Accounts-in-Windows-Server-Essentials.md)" 中。

### <a name="a-user-account-was-removed-but-the-users-file-history-remains"></a>用户帐户已删除，但用户的文件历史记录仍保留
 在某些情况下，网络管理员可以选择从服务器中删除用户或计算机，但保留文件历史记录备份以供将来使用。 当不再需要文件历史记录时，请从服务器上的共享文件夹中删除用户或计算机的文件历史记录备份文件夹。 若要执行此操作，请参阅 [To manually delete File History backups for a user or a computer](../support/Troubleshoot-File-History-in-Windows-Server-Essentials.md#BKMK_manuallyDelete)。


## <a name="see-also"></a>请参阅

-   [管理客户端备份](../manage/Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md)

-   [支持 Windows Server Essentials](../support/Support-Windows-Server-Essentials.md)

