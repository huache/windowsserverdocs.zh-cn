---
title: 管理 Windows Server Essentials 中的服务器文件夹
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 090cf1b8-7b9b-48b9-ae85-b98477b8d7cc
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: e901038a2a4e294184241b4d35797347a5910026
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626119"
---
# <a name="manage-server-folders-in-windows-server-essentials"></a>管理 Windows Server Essentials 中的服务器文件夹

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 作为服务器管理员，你可以使用仪表板的 " **服务器文件夹** " 选项卡上的 "任务"，管理对 (称为 "共享文件夹" 的任何服务器文件夹的访问，这些文件夹从快速启动板、远程 Web 访问、my server 应用 Windows Phone 程序或服务器上的 "我的服务器" 应用程序) 

 以下主题提供了将帮助你了解、创建和管理服务器文件夹的信息：

-   [使用仪表板管理服务器文件夹](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_2)

-   [管理对服务器文件夹的访问](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_1)

-   [添加或移动服务器文件夹](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_5)

-   [添加丢失的服务器文件夹](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_9)

-   [了解共享文件夹](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_11)

-   [了解卷影副本](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_Shadow)

##  <a name="manage-server-folders-using-the-dashboard"></a><a name="BKMK_2"></a> 使用仪表板管理服务器文件夹
 通过 Windows Server Essentials，可以使用仪表板执行常见管理任务。 仪表板的“服务器文件夹”**** 页面提供了以下内容：

- 可显示以下内容的服务器文件夹列表：

  -   文件夹名称

  -   文件夹说明

  -   文件夹位置

  -   文件夹位置提供的可用空间量

  -   有关要在文件夹上执行的所有任务的简短状态信息；如果文件夹运行状况良好并且没有正在运行的任务，则“状态”**** 字段为空。

- 一个可能提供有关选定文件夹的附加信息的详细信息窗格

- 一个包含一组与文件夹相关的管理任务的任务窗格

  下表介绍了在 Windows Server Essentials 仪表板上可用的各种服务器文件夹任务。 大多数任务都特定于文件夹，它们仅在选择列表中的某个文件夹时才可见。

### <a name="server-folder-tasks-on-the-dashboard"></a>仪表板上的服务器文件夹任务

|任务名称|说明|
|---------------|-----------------|
|打开文件夹|在文件资源管理器（在以前版本的 Windows 中称为 Windows 资源管理器）中显示选定文件夹的内容。|
|删除文件夹|使你能够删除用户创建的文件夹。 此任务不适用于服务器安装创建的默认文件夹。|
|移动文件夹|打开一个可帮助你将服务器文件夹移动到新位置的向导。|
|停止共享文件夹|停止共享选定文件夹，但不会删除它。 当不再共享文件夹时，该文件夹便不会显示在仪表板中。 此任务不适用于服务器安装创建的默认文件夹。|
|查看文件夹属性|显示选定文件夹的属性，并允许你执行以下操作：<br /><br /> -更改用户创建的文件夹的名称。<br /><br /> -更改所选文件夹的说明。<br /><br /> -查看文件夹的大小。<br /><br /> -在文件资源管理器中打开所选文件夹。<br /><br /> -指定所选文件夹的用户帐户访问权限。<br /><br /> -从远程 Web 访问和 Web 服务应用程序中隐藏选定文件夹。<br /><br /> -指定文件夹配额。|
|添加文件夹|帮助你创建新的服务器文件夹，并指定每个用户帐户所允许的访问级别。|
|了解服务器文件夹|打开 Internet 上的帮助主题，该主题介绍了服务器文件夹的用途和功能。|

##  <a name="manage-access-to-server-folders"></a><a name="BKMK_1"></a> 管理对服务器文件夹的访问
 Windows Server Essentials 使你能够使用服务器文件夹将位于客户端计算机上的文件存储到中心位置。 将文件存储在服务器文件夹中将确保你的文件位于一个可始终通过安全方式从每个客户端访问的位置。

 使用服务器文件夹存储你的文件使你能够执行以下操作：

- 使用“服务器备份和还原”备份服务器文件夹，以帮助避免服务器完全失效。

- 通过远程 Web 访问或 Windows Phone 和 Windows 8 的“我的服务器”应用，使用 Internet 浏览器从任意位置访问存储在服务器文件夹上的文件。

- 从任何客户端计算机中访问新服务器文件夹。

  通过使用仪表板的“服务器文件夹”**** 选项卡上的任务，你可以管理对服务器上任何服务器文件夹的访问。 下表列出了默认情况下在安装 Windows Server Essentials 或在服务器上打开媒体流时创建的服务器文件夹。

|服务器文件夹名称|说明|
|------------------------|-----------------|
|客户端计算机备份|默认情况下，Windows Server Essentials 将创建存储在此文件夹中的客户端计算机备份。 网络管理员可以修改客户端计算机备份的设置。|
|Company|用于供网络用户存储和访问与你的组织相关的文档。|
|文件历史记录备份|默认情况下，Windows Server Essentials 使用文件历史记录创建存储在此文件夹中的文件备份。 网络管理员可以修改这些文件历史记录设置。|
|文件夹重定向|用于供网络用户存储和访问为文件夹重定向设置的文件夹。|
|用户|用于供网络用户存储和访问文件。 针对你创建的每个网络用户帐户，特定于用户的文件夹将在“用户”**** 服务器文件夹中自动生成。|
|Music|用于供网络用户存储和访问音乐文件。 此文件夹在你打开媒体共享时可用。|
|图片|用于供网络用户存储和访问图片文件。 此文件夹在你打开媒体共享时可用。|
|录制的电视|用于供网络用户存储和访问录制的电视节目。 此文件夹在你打开媒体共享时可用。|
|视频|用于供网络用户存储和访问视频文件。 此文件夹在你打开媒体共享时可用。|

 若要隐藏或设置服务器文件夹的权限或者修改服务器文件夹属性，请参阅以下过程：

-   [隐藏服务器文件夹](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_Hide)

-   [设置对服务器文件夹的权限](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_Perms)

-   [查看或修改服务器文件夹属性](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_10)

###  <a name="hide-server-folders"></a><a name="BKMK_Hide"></a> 隐藏服务器文件夹
 作为网络管理员，你可以选择隐藏任何服务器文件夹，并阻止将它们显示在远程 Web 访问网站或 Web 服务器应用程序（例如“我的服务器”）上。

> [!NOTE]
>  你必须是网络管理员，才能执行此过程。

##### <a name="to-hide-server-folders-from-being-displayed-in-remote-web-access"></a>隐藏要显示在远程 Web 访问中的服务器文件夹

1.  打开 Windows Server Essentials 仪表板。

2.  单击“存储”****，然后单击“服务器文件夹”****。

3.  在列表视图中，选择要查看或修改其属性的服务器文件夹。

4.  在 **<ServerFolder \> 任务** "窗格中，单击" **查看文件夹属性**"。

5.  在 **<文件夹名 \> 属性**中，单击 " **共享**"，选择 " **在远程 Web 访问和 Web 服务应用程序中隐藏此文件夹**"，然后单击 " **应用**"。

###  <a name="set-permissions-to-server-folders"></a><a name="BKMK_Perms"></a> 设置对服务器文件夹的权限
 对于你使用仪表板添加在服务器上的任何其他服务器文件夹，你可以为它选择三种不同的访问设置：

-   **读/写**

     如果你想要允许此用户创建、更改和删除服务器文件夹中的任何文件，则选择此设置。

-   **只读**

     如果你想要仅允许此用户读取服务器文件夹中的文件，则选择此设置。 具有只读访问权限的用户不能创建、更改或删除服务器文件夹中的任何文件。

-   **无访问权限**

     如果你不希望此用户访问服务器文件夹中的任何文件，则选择此设置。

> [!IMPORTANT]
>  文件夹属性中显示的权限仅表示由仪表板管理的用户。 这些权限不包括用户权限（例如组或服务帐户）、可能使用其他本机工具在该文件夹上设置的任何权限，也不包括尚未通过仪表板添加的用户。

> [!NOTE]
>  你必须是网络管理员，才能执行此过程。

##### <a name="to-set-permissions-to-server-folders-on-the-server"></a>在服务器上设置对服务器文件夹的权限

1.  打开 Windows Server Essentials 仪表板。

2.  单击“存储”****，然后单击“服务器文件夹”****。

3.  在列表视图中，选择要查看或修改其属性的服务器文件夹。

4.  在 **<ServerFolder \> 任务** "窗格中，单击" **查看文件夹属性**"。

5.  在 **<文件夹名 \> 属性**中，单击 " **共享**"，为列出的用户帐户选择适当的用户访问级别，然后单击 " **应用**"。

> [!NOTE]
>  默认情况下，当你将用户帐户添加到网络时，将在服务器上的“用户”**** 文件夹下为用户创建一个子文件夹。 仅用户或管理员才能从网络计算机中访问此子文件夹。 这些权限是在“用户”**** 下为每个子文件夹设置的，因此没有适用于顶级“用户”**** 文件夹的常规访问权限。

> [!NOTE]
>  不能修改“文件历史记录备份”****、“文件夹重定向”**** 和“用户”**** 服务器文件夹的共享权限。 因此，这些服务器文件夹的文件夹属性不包含“共享”**** 选项卡。

###  <a name="view-or-modify-server-folder-properties"></a><a name="BKMK_10"></a> 查看或修改服务器文件夹属性
 通过仪表板的“服务器文件夹”**** 选项卡上的“查看文件夹属性”**** 任务，你可以修改服务器文件夹名称和说明，并定义哪些用户帐户有权访问服务器文件夹。

> [!NOTE]
>  在安装了 Windows Server Essentials Experience 角色的 Windows Server Essentials 和 Windows Server 2012 R2 中，你还可以修改文件夹配额。

##### <a name="to-view-or-modify-folder-properties"></a>查看或修改文件夹属性

1.  打开 Windows Server Essentials 仪表板。

2.  单击“存储”****，然后单击“服务器文件夹”****。

3.  在列表视图中，选择要查看或修改其属性的服务器文件夹。

4.  在 **<ServerFolder \> 任务** "窗格中，单击" **查看文件夹属性**"。

5.  在 **<文件夹 \> **名称 "属性的" **常规** "选项卡上，查看或修改服务器文件夹的名称和说明。

    > [!NOTE]
    >  在安装了 Windows Server Essentials Experience 角色的 Windows Server Essentials 和 Windows Server 2012 R2 中，你还可以修改在服务器文件夹达到其指定大小时提供警告消息的文件夹配额。

##  <a name="add-or-move-a-server-folder"></a><a name="BKMK_5"></a> 添加或移动服务器文件夹
 除了在设置期间创建的默认服务器文件夹，你还可以**添加更多的服务器文件夹**来存储服务器上的文件。 你可以将服务器文件夹添加到运行 Windows Server Essentials 的主服务器或成员服务器上。

 通过使用“移动文件夹”向导，你可以在需要时将位于运行 Windows Server Essentials 的主服务器上并显示在仪表板的“服务器文件夹”**** 选项卡上的**服务器文件夹**移动到另一个硬盘驱动器。 在以下情况下，你可以将服务器文件夹移动到另一个硬盘驱动器位置地址：

- 数据硬盘驱动器不再具有足够的空间来存储数据。

- 你想要更改默认存储位置。 若要实现更快地移动，请考虑在服务器文件夹不包含任何数据的情况下来进行移动。

- 你想要删除现有硬盘驱动器，但不丢失位于其上的服务器文件夹。

  在移动该文件夹之前，请确保以下内容：

- 确保你已备份你的服务器。

- 确保所有客户端备份均已停止且未在进行中（如果你计划移动客户端计算机备份文件夹）。 移动客户端计算机备份文件夹时，直到完成文件夹移动，服务器才能备份任何客户端计算机。

- 确保服务器未执行任何关键系统操作。 建议你在开始文件夹移动之前，先完成正在进行的任何更新或备份，否则完成该过程可能需要更长的时间。

- 未使用文件夹中要移动的任何文件。 在移动服务器文件夹时，你将不能访问它。

  如果服务器文件夹中的文件实现了以下技术，则不支持将文件夹从 NTFS 移动到 ReFS：

- 备用数据流

- 对象 ID

- 短名称（8.3 名称）

- 压缩

- EFS 加密

- 事务性 NTFS、TxF（已引入 Windows Vista）

- 稀疏文件

- 硬链接

- 扩展属性

- 配额

###  <a name="where-to-add-or-move-a-server-folder"></a><a name="BKMK_6"></a> 添加或移动服务器文件夹的位置
 通常，你应将服务器文件夹添加或移动到具有最大可用空间量的硬盘驱动器上。 如果可能，避免将共享文件夹添加或移动到系统驱动器（例如 C:），因为它可能占用操作系统及其更新所需的必要驱动器空间。 同样，避免将服务器文件夹添加或移动到外部硬盘驱动器，因为它们很容易断开连接，从而导致你无法访问你的文件。 相反，我们建议你在内部驱动器上创建该文件夹。

 无法将服务器文件夹添加或移动到以下位置，如果针对添加或移动操作选定以下任意位置，则该服务器文件夹将产生一个错误：

-   未使用 NTFS 或 ReFS 文件系统进行格式化的硬盘驱动器

-   %windir% 文件夹

-   映射的网络驱动器

-   包含共享文件夹的文件夹

-   位于“可移动存储设备”**** 下的硬盘驱动器

-   硬盘的根目录 (如 C： \\ 、D： \\ 、E： \\) 

-   现有共享文件夹的子文件夹

-   运行 Windows server Essentials 或 Windows Server 2012 R2 且安装了 Windows Server Essentials Experience 角色的成员服务器

### <a name="steps-to-add-or-move-a-server-folder"></a>添加或移动服务器文件夹的步骤

> [!NOTE]
>  你必须是服务器管理员，才能完成这些过程。

##### <a name="to-add-a-server-folder"></a>添加服务器文件夹

1. 打开“仪表板”。

2. 单击“存储”****，然后单击“服务器文件夹”****。

3. 在“服务器文件夹任务”**** 中，单击“添加文件夹”****。 这将启动“添加文件夹向导”。

4. 按照说明完成向导。

   > [!NOTE]
   > - 如果你通过使用“浏览”按钮浏览特定文件夹来指定服务器文件夹位置，则将已导航到的文件夹添加为服务器文件夹。
   >   -   你可以定义通过远程 Web 访问可以访问哪些服务器文件夹。 有关详细信息，请参阅[管理对服务器文件夹的访问](Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_1)。

##### <a name="to-move-a-server-folder"></a>移动服务器文件夹

1.  打开“仪表板”。

2.  单击“存储”****，然后单击“服务器文件夹”****。

3.  从服务器文件夹列表中，选择要移动的文件夹。

4.  在“任务”窗格中，单击“移动文件夹”****。

5.  按照说明完成向导。

##  <a name="add-a-missing-server-folder"></a><a name="BKMK_9"></a> 添加丢失的服务器文件夹
 当服务器检测到预定义的服务器文件夹时？由于某些原因或其他) ，公司、用户、客户端计算机备份、文件历史记录备份或文件夹重定向不会再共享 (，因此会生成一个警报来指导用户解决此问题。 建议你从服务器备份中尝试和还原文件夹。 但是，如果尚未备份服务器，则选择丢失的文件夹，然后单击“重新创建丢失的文件夹”**** 以重新配置服务器文件夹的位置。

> [!NOTE]
>  仅限预定义文件夹？可以重新创建公司、用户、客户端计算机备份、文件历史记录备份或文件夹重定向。 无法重新创建用户创建的服务器文件夹和媒体服务器文件夹。

 还原或重新创建丢失的文件夹后，不应再将其作为“丢失”**** 列出。

 有关从服务器备份中还原文件的信息，请参阅 [管理备份和还原](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)主题中的 "了解有关还原文件和文件夹的详细信息" 部分。

##  <a name="understand-shared-folders"></a><a name="BKMK_11"></a> 了解共享文件夹
 你可以通过多种不同的方式从已连接到服务器的设备中访问 Windows Server Essentials 上的共享文件夹。 有关详细信息，请参阅主题 [使用共享文件夹](../use/Use-Shared-Folders-in-Windows-Server-Essentials.md)。

##  <a name="understand-shadow-copies"></a><a name="BKMK_Shadow"></a> 了解卷影副本
 借助服务器卷影副本，当共享文件和文件夹在过去的时间点出现时，用户可以查看这些文件和文件夹。 访问以前版本的文件或卷影副本很重要，因为用户可以实现以下目的：

1. **恢复意外删除的文件**。 如果你意外删除了某个文件，则可以打开以前的版本并将其复制到一个安全位置。

2. **恢复意外覆盖的文件**。 如果你意外覆盖了某个文件，则可以恢复该文件的以前版本。 （版本数量取决于已创建的快照数。）

3. **在工作时比较文件的各个版本**。 当你想要检查文件的各个版本之间所发生的更改时，你可以使用以前的版本。

   若要使用卷影副本，请从客户端计算机中，右键单击服务器共享文件夹，然后选择“还原以前版本”****。

## <a name="additional-references"></a>其他参考

-   [管理服务器存储](Manage-Server-Storage-in-Windows-Server-Essentials.md)

-   [使用共享文件夹](../use/Use-Shared-Folders-in-Windows-Server-Essentials.md)

-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)
