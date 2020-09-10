---
title: 还原或修复运行 Windows Server Essentials 的服务器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 27bf6f24-30c4-4935-9b24-069eb43e22f4
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 00c57fab4ee9689ba8bd760e5c99d87e3e18d130
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622952"
---
# <a name="restore-or-repair-your-server-running-windows-server-essentials"></a>还原或修复运行 Windows Server Essentials 的服务器

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 本主题提供了有关还原或修复运行 Windows Server Essentials 的服务器的概述和支持步骤，并包括以下部分：

-   [服务器系统还原概述](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Overview)

-   [还原或修复系统驱动器](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore)

-   [还原服务器上的文件和文件夹](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesAndFolders)

##  <a name="overview-of-server-system-restores"></a><a name="BKMK_Overview"></a> 服务器系统还原概述
 服务器在执行还原时的状态将影响可用的还原方法，以及可执行还原的全面性。

 还原服务器的最常见原因如下：

- 无法对服务器上的病毒进行接种或将其删除。

- 服务器配置设置出现错误，并且无法启动服务器。

- 替换了系统驱动器。

- 停用该服务器，并且要还原到新服务器。

  既可以从备份中还原服务器，也可以将服务器还原到出厂默认设置。

- [从备份中还原服务器](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFromBackup)

- [将服务器重置为出厂默认设置](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_FactoryReset)

###  <a name="restoring-the-server-from-a-backup"></a><a name="BKMK_RestoreFromBackup"></a> 从备份还原服务器
 本部分提供了有关选择备份类型的指南。

 如果有可用的备份，则还原服务器的最佳选择是使用制造商的安装媒体从外部备份中进行还原。 还原操作会通过你选择的备份还原服务器设置和文件夹。 只需配置设置并还原在备份之后创建的数据。

 当你选择通过从以前的备份还原服务器时，必须选择要还原的特定备份，并且在直接连接到服务器的外部硬盘驱动器上必须存在有效的备份文件：

- **如果你最近成功创建了服务器备份**，并且你确定该备份包含所有关键数据，则选择服务器备份将非常简单。 你将只需重新创建在上次良好备份后创建的数据，并重新配置在该备份之后进行更改的设置。

- **如果由于存在病毒而还原服务器**，则选择确定是在收到病毒前所进行的备份。 可能需要选择比此备份的日期再向前几天的备份，以确保不存在病毒。

- **如果由于错误的配置设置而还原服务器**，则选择确定是在导致服务器上出现问题的配置设置的更改之前所进行的备份。

  在从备份中进行还原时，确切的过程和所需的后续步骤将取决于服务器上硬盘驱动器的数量以及是否替换了系统驱动器：

- **如果服务器具有单个硬盘驱动器并且该驱动器未进行替换**，则在还原服务器时驱动器分区信息将保持不变。 将还原系统卷，而保留剩余卷上的数据。

- **如果服务器具有单个硬盘驱动器并且该驱动器已进行替换**，则系统卷将被还原，然后你必须手动将文件夹还原到数据卷。 需要创建所有非默认的共享文件夹，因为在重新创建服务器存储时不会创建这些文件夹。

- **如果服务器具有多个硬盘驱动器，并且驱动器 0（包含系统卷）未进行替换**，则在还原服务器时驱动器分区信息将保持不变。 将还原系统卷，而保留所有剩余卷上的数据。

- **如果服务器具有多个硬盘驱动器，并且驱动器 0（包含系统卷）已进行替换**，则系统卷将被还原，然后你必须手动还原以前存储在驱动器 0 上的所有共享文件夹。

###  <a name="resetting-the-server-to-factory-default-settings"></a><a name="BKMK_FactoryReset"></a> 将服务器重置为出厂默认设置
 如果没有可进行还原的备份，或出于某些其他原因你希望或需要执行完整的系统还原，而无需还原以前的服务器配置，则可以执行以下还原：通过使用服务器硬件制造商提供的安装或恢复媒体将服务器重置为出厂默认设置。

 通过重置为出厂默认设置还原服务器时，服务器上的所有现有设置和安装的应用程序都将被删除，并且你必须再次配置服务器。 在执行出厂重置后，服务器将重新启动。

 在执行出厂重置时，可以选择保留数据或删除数据，这会具有以下效果：

-   如果选择保留所有数据，则系统卷上的所有数据都将被删除，但其他卷上的数据将会保留。

    > [!CAUTION]
    >  如果磁盘设置不匹配默认设置，则将删除磁盘上的所有数据。 如果替换了系统磁盘，则新磁盘必须大于原始磁盘的系统卷。
    >
    >  如果系统驱动器的分区信息不可读，或如果要替换系统驱动器，则即使选择保留所有数据，也将删除系统驱动器上的所有数据。

-   如果你打算解除服务器的授权或调整其用途，请选择删除所有数据。 除了服务器配置、其他设置和系统卷上的数据，还将删除所有其他数据，并重新格式化服务器上的所有硬盘驱动器。

> [!NOTE]
>  如果在服务器上配置了存储空间，则在执行出厂重置之前，应使用 **“管理存储空间”** 控制台的 **“高级”** 部分手动删除所有存储空间。

 在执行出厂重置后，将需要执行以下任务：

-   **重新配置服务器。** 在服务器上，使用“配置服务器”向导重新输入配置设置。 若要从客户端计算机配置远程管理的 Windows Server Essentials 服务器，请打开 web 浏览器，然后在地址栏中键入 " **http://** _<服务器名称 \> _ "。

-   **将客户端计算机重新连接到服务器。** 如果计算机以前连接过服务器，则必须先从计算机中卸载 Windows Server Essentials 连接器软件，然后才能将计算机再次连接到服务器。 有关详细信息，请参阅[卸载连接器软件](../use/Get-Connected-in-Windows-Server-Essentials.md#BKMK_13)和[将计算机连接到服务器](../use/Get-Connected-in-Windows-Server-Essentials.md#BKMK_9)。

##  <a name="restore-or-repair-the-system-drive"></a><a name="BKMK_Restore"></a> 还原或修复系统驱动器
 还原服务器的第一步是还原或修复服务器系统驱动器。 在还原系统驱动器后，你将需要执行还原服务器上的数据驱动器所需的所有操作并还原在还原过程中丢失的所有共享。

 提供了以下三种执行还原的方法：

-   [使用安装媒体还原或修复服务器](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_1)。 使用服务器制造商提供的安装媒体从备份中还原。

-   **使用安装媒体将服务器还原到默认出厂设置**。 若要了解如何在服务器上执行此操作，请参阅服务器制造商提供的文档。

-   [使用恢复 DVD 从客户端计算机上还原或重置服务器](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_2)。 如果需要还原运行 Windows Server Essentials 的远程管理的服务器，则必须使用服务器制造商提供的还原 DVD 从客户端计算机执行还原。

###  <a name="restore-or-repair-your-server-using-installation-media"></a><a name="BKMK_Restore_1"></a> 使用安装媒体还原或修复服务器
 以下过程描述如何使用 Windows Server Essentials 安装媒体从备份中还原服务器系统驱动器。 （若要了解如何使用安装媒体还原到出厂默认设置，请参阅服务器制造商提供的文档。）

> [!NOTE]
>  如果服务器使用存储空间，并且要将数据还原到新服务器，则应首先恢复系统驱动器，然后登录到 Windows Server Essentials 仪表板，以与在旧服务器上类似的方式配置存储空间，然后再恢复数据卷。

##### <a name="to-restore-the-server-system-drive-from-a-backup-using-installation-media"></a>使用安装媒体从备份中还原服务器系统驱动器

1.  将 Windows Server Essentials 安装 DVD 插入服务器 DVD 驱动器中、重新启动服务器，然后按任意键从 DVD 启动。

    > [!NOTE]
    >  如果还原过程未自动启动，请检查服务器的 BIOS 设置，以确保 DVD 驱动器显示为启动菜单中的第一项。

     -或者-

     如果制造商将安装媒体预加载在服务器上，请在启动时按 F8 来从安装媒体启动。

2.  在 Windows Server 文件加载后，请选择语言和其他首选项，然后单击 **“下一步”**。

3.  在向导的下一页上，单击 **“修复计算机”**。

    > [!CAUTION]
    >  不要选择 **“立即安装”** 选项。 该选项将指导你完成整个系统安装，并删除系统驱动器上的所有配置设置和所有数据。

4.  在 **“选择一个选项”** 页上，单击 **“疑难解答”**。

5.  在 " **系统映像恢复** " 页上，选择 "当前系统？ **windows server essentials** " 或 " **windows server essentials**"。

     此时将打开“重置计算机映像”向导。

6.  在 **“选择系统映像备份”** 页上，你可以选择使用最新的备份，也可以选择以前的备份。 系统将还原到备份时所处的状态，该备份是你为还原或修复服务器所选择的。 必须重新创建在保存备份后添加的数据和对设置进行的更改。

     选择以下选项之一，然后单击 **“下一步”**：

    -   **“使用最新的可用系统映像(推荐)”**

    -   **“选择系统映像”**

    > [!NOTE]
    >  如果你最近成功创建了服务器备份，并且你确定该备份包含所有关键数据，则选择服务器备份将非常简单。 你将只需重新创建在上次良好备份后创建的数据，并重新配置在该备份之后进行更改的设置。
    >
    >  如果由于存在病毒而还原服务器，则选择确定是在收到病毒前所进行的备份。 可能需要选择比此备份的日期再向前几天的备份，以确保不存在病毒。
    >
    >  如果由于错误的配置设置而还原服务器，则选择确定是在导致服务器上出现问题的配置设置的更改之前所进行的备份。

7.  按照向导中的说明完成系统还原。

8.  成功还原服务器后，请移除安装 DVD（如果使用），然后重新启动服务器。

> [!NOTE]
>  若要还原并共享服务器上的文件夹，你可能需要采取其他步骤。 有关详细信息，请参阅[还原服务器上的文件和文件夹](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesAndFolders)。

###  <a name="restore-or-reset-your-server-from-a-client-computer-using-the-recovery-dvd"></a><a name="BKMK_Restore_2"></a> 使用恢复 DVD 从客户端计算机还原或重置服务器
 在 Windows Server Essentials 中，你可以从你创建的可启动 u 盘中启动服务器，然后通过使用服务器制造商提供的恢复 DVD 从客户端计算机恢复服务器。 客户端计算机必须与服务器位于同一网络上。 此方法在 Windows Server Essentials 中不可用。

 以下过程提供了执行服务器还原的常规步骤。 这些步骤同样适用于从备份中进行还原或还原到出厂默认设置。 有关更具体的说明，请参阅服务器制造商提供的文档。

##### <a name="to-restore-or-reset-the-server-from-a-client-computer-using-the-recovery-dvd"></a>使用恢复 DVD 从客户端计算机上还原或重置服务器。

1.  插入在客户端计算机上从服务器制造商处收到的 Windows Server Essentials 服务器恢复媒体。

     此时将打开“恢复服务器”向导。

2.  按照向导中的说明创建将用来在恢复模式下启动服务器的可启动 U 盘。

3.  在“恢复服务器”向导准备好可启动 U 盘后，将闪存驱动器插入服务器，然后在恢复模式下启动服务器。 若要了解如何在恢复模式下启动服务器，请参阅服务器硬件制造商提供的文档。

     在恢复模式下启动服务器后，“恢复服务器”向导将查找该服务器，然后建立连接。

4.  按照向导中的说明完成还原服务器。

> [!NOTE]
>  这种服务器恢复的方法将忽略在恢复期间连接到服务器的外部存储设备。 如果你想要清除外部存储设备上的数据，则必须手动执行此操作。

> [!NOTE]
>  如果在服务器上创建了其他共享文件夹，则从备份中还原数据后，服务器可能无法识别其他共享文件夹。 必须重新共享这些文件夹。 有关详细信息，请参阅[还原服务器上的文件和文件夹](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesAndFolders)。

##  <a name="restore-files-and-folders-on-the-server"></a><a name="BKMK_RestoreFilesAndFolders"></a> 还原服务器上的文件和文件夹
 根据用来还原或修复服务器的方法，以及服务器使用的存储类型，你可能需要在还原系统驱动器后恢复数据卷。 在某些情况下，你可能需要重新共享现有的文件夹，以便服务器能够识别它们。

 当你可能需要还原文件和文件夹时，下面提供了一些示例：

-   [从服务器备份中还原文件和文件夹](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesFromBackup)。 如果替换了系统磁盘，或者如果系统磁盘上的分区信息不可读，则可以还原系统，但无法还原该磁盘上其他卷中的数据。 若要还原其他数据卷中的文件和文件夹，必须使用“还原文件和文件夹”向导。

-   [还原服务器上的共享文件夹](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_ConfigreSharedFolders)。 如果在服务器上创建了其他共享文件夹，则从备份中还原系统驱动器后，共享文件夹仍在数据分区中，或已还原到数据分区，但服务器可能无法识别它们。 必须重新共享这些文件夹。

###  <a name="restore-files-and-folders-from-a-server-backup"></a><a name="BKMK_RestoreFilesFromBackup"></a> 从服务器备份中还原文件和文件夹
 如果硬盘停止工作或文件被意外删除，“还原文件和文件夹”向导将会帮助你保护数据。 使用 Windows Server Essentials 备份，你可以在硬盘驱动器上创建所有数据的副本，并将数据存储在外部存储设备上。 如果硬盘驱动器上的原始数据被意外删除、覆盖或由于故障而变得无法访问，则可以从备份中还原这些数据。 “还原文件或文件夹”向导可帮助你从现有的备份中还原单个文件或文件夹、多个文件或文件夹或者整个硬盘驱动器。

 在还原系统后，可能需要使用“还原文件和文件夹”向导来还原在还原期间未保留的文件和文件夹。 例如，如果替换了系统磁盘，或者系统磁盘上的分区信息不可读，则无法从系统磁盘上的其他卷中恢复数据。

> [!NOTE]
>  无法使用“还原文件和文件夹”向导还原整个系统驱动器。 有关如何还原整个系统的信息，请参阅[使用安装媒体还原或修复服务器](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_1)或[使用恢复 DVD 从客户端计算机还原或重置服务器](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_2)。

##### <a name="to-restore-files-and-folders-from-a-server-backup"></a>从服务器备份中还原文件和文件夹

1.  打开 Windows Server Essentials 仪表板，然后单击 " **设备** " 选项卡。

2.  单击服务器的名称，然后单击 **“任务”** 窗格中的 **“为服务器还原文件或文件夹”**。

     此时将打开“还原文件和文件夹”向导。

3.  按照向导中的说明还原文件或文件夹。

> [!WARNING]
>  有关备份和还原文件和文件夹的详细信息，请参阅 [管理备份和还原](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)。

###  <a name="restore-shared-folders-on-the-server"></a><a name="BKMK_ConfigreSharedFolders"></a> 还原服务器上的共享文件夹
 还原服务器的系统驱动器后，如果共享文件夹仍在数据分区中，或已还原到数据分区，则可能需要再次配置共享文件夹，以便服务器能够识别这些文件夹。 以下过程将介绍如何添加之前已共享的共享文件夹。

##### <a name="to-add-an-existing-folder-to-the-server-shared-folders"></a>将现有文件夹添加到服务器共享文件夹

1.  在文件资源管理器中，找到硬盘驱动器上的共享文件夹。

2.  右键单击共享文件夹，依次单击 **“属性”**、**“设置”** 选项卡，然后记下文件夹权限。

3.  登录到 Windows Server Essentials 仪表板，单击 "**存储**" 选项卡，然后在 "**服务器文件夹任务**" 窗格中单击 "**添加文件夹**"。

     此时将打开“添加文件夹”向导。

4.  在 **“名称”** 框中键入共享的名称。

5.  单击 "**浏览**"，导航到 *<驱动器 \> \\<ServerName \> *\ServerFolders (例如 " *d:\Contoso\ServerFolders* ") 中，选择要共享的文件夹，然后单击 **"确定"**。

6.  单击“下一步”。 

7.  指定在步骤 2 中记下的权限，然后单击 **“添加文件夹”**。

    > [!IMPORTANT]
    >  这些权限将替换未通过使用 Windows Server Essentials 仪表板添加到文件夹的任何现有权限。

> [!IMPORTANT]
>  在完成将文件夹添加到共享文件夹的列表后，请确保在服务器备份中包含这些文件夹。 有关将文件夹添加到服务器备份的信息，请参阅[设置或自定义服务器备份](Set-up-or-customize-server-backup.md)。

## <a name="additional-references"></a>其他参考

-   [管理备份和还原](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)

-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)

-   [使用 Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)
