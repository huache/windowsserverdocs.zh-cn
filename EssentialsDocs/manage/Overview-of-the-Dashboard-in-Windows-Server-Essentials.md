---
title: Windows Server Essentials 仪表板概述
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: f70a79de-9c56-4496-89b5-20a1bff2293e
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 50f610bec8573916edffd3efb5e551a45fc6e72a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625957"
---
# <a name="overview-of-the-dashboard-in-windows-server-essentials"></a>Windows Server Essentials 仪表板概述

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 已启用 Windows Server Essentials 体验角色的 Windows Server Essentials 和 Windows Server 2012 R2 Standard 包括管理仪表板，它可以简化管理 Windows Server Essentials 网络和服务器时所执行的任务。 通过使用 Windows Server Essentials 仪表板，你可以：

- 完成服务器的设置

- 访问并执行常见的管理任务

- 查看服务器警报，并对其采取操作

- 设置并更改服务器设置

- 访问或搜索 Web 上的帮助主题

- 访问 Web 上的社区资源

- 管理用户帐户

- 管理设备和备份

- 管理服务器文件夹和硬盘驱动器的访问权限和设置

- 查看并管理加载项应用程序

- 与 Microsoft Online Services 集成

  本主题包括以下内容：

- [仪表板的基本功能](#BKMK_Design)

- [仪表板主页的功能](#BKMK_Home)

- [仪表板的管理部分](#BKMK_Features)

- [访问 Windows Server Essentials 仪表板](#BKMK_AccessDb)

- [使用安全模式](#BKMK_UseSafeMode)

##  <a name="basic-features-of-the-dashboard"></a><a name="BKMK_Design"></a> 仪表板的基本功能
 Windows Server Essentials 仪表板可帮助你快速访问关键信息和服务器的管理功能。 该仪表板包含若干部分。 下表介绍了各个部分。



|项|仪表板功能|说明|
|----------|-----------------------|-----------------|
|1|导航栏|在导航栏上单击某个部分，以访问与该部分相关联的信息和任务。 每次打开仪表板时，默认情况下将显示“主页”****。|
|2|子部分选项卡|子部分选项卡提供对第二层 Windows Server Essentials 管理任务的访问。|
|3|“列表”窗格|列表视图显示可管理的对象，并包含每个对象的基本信息。|
|4|细节窗格|“详细信息”窗格显示有关在列表视图中选择的对象的其他信息。|
|5|任务窗格|“任务”窗格包含指向工具和信息的链接，它们可帮助你管理特定对象（例如用户帐户或计算机）的属性，或者管理用于对象类别的全局设置。 “任务”窗格分成以下两个部分：<br /><br /> **对象任务**  –包含指向工具和信息的链接，可帮助您管理您在列表视图中选择的对象的属性， (例如用户帐户或) 的计算机。<br /><br /> **全局任务**  –包含指向工具和信息的链接，可帮助你管理功能区域的全局任务。 全局任务包括添加新对象、设置策略的任务等。|
|6|信息和设置|本部分提供对服务器设置的直接访问，以及指向你所查看的仪表板页面相关信息的“帮助”链接。|
|7|警报状态|警报状态提供有关服务器运行状况的快速视觉指示。 单击警报图像以查看关键和重要警报。<br /><br /> **注意：** 在安装了 Windows Server Essentials Experience 角色的 Windows Server Essentials 和 Windows Server 2012 R2 Standard 中，" **信息和设置** " 选项卡上提供了警报状态。|
|8|状态栏|状态栏会显示列表视图中出现的对象数。 加载项应用程序还可能会显示其他状态。|

##  <a name="features-of-the-dashboard-home-page"></a><a name="BKMK_Home"></a> 仪表板主页的功能
 在打开仪表板时，默认情况下，将显示“主页”****，并显示“设置”**** 类别。 Windows Server Essentials 仪表板的“主页”**** 提供了对可帮助自定义服务器和配置关键功能的任务和信息的快速访问。 “主页”页面包括四个功能区域，它们将显示你选择的选项的信息和配置任务。 下表描述了这些功能。

|项|Feature|说明|
|----------|-------------|-----------------|
|1|导航栏|在导航栏上单击某个部分，以访问与该部分相关联的信息和任务。 每次打开仪表板时，默认情况下都将显示“主页”****。|
|2|“类别”窗格|此窗格将显示功能区域，这些功能区域提供对有助于设置和自定义服务器的信息和配置工具的快速访问。 单击某个类别以显示与该类别关联的任务和资源。|
|3|任务窗格|此窗格将显示指向选定类别的相关任务和信息的链接。 单击某个任务或资源以显示其他信息。|
|4|“操作”窗格|此窗格提供了某个功能或任务的简短说明，并提供用于打开配置向导和信息页面的链接。 单击某个链接以采取进一步的操作。|

##  <a name="administrative-sections-of-the-dashboard"></a><a name="BKMK_Features"></a> 仪表板的管理部分
 Windows Server Essentials 仪表板将网络信息和管理任务组织到功能区域。 每个功能区域的管理页面都提供了与该区域关联的对象（例如“用户”**** 或“设备”****）的相关信息。 管理页面所包括的任务还可用于查看或更改设置，或者用于运行可自动执需要多个步骤的任务的程序。

 下表介绍了仪表板的管理部分，这些部分在安装后默认为可用。 该表还列出了每个部分中可用的任务。

|部分|说明|
|-------------|-----------------|
|主页|默认情况下，“主页”**** 将在每次打开仪表板时显示。 它包括以下类别的任务和信息：<br /><br /> **安装**  –完成此类别的任务以首次配置服务器。 有关这些任务的信息，请参阅 [安装和配置 Windows Server Essentials](../install/Install-and-Configure-Windows-Server-Essentials.md)。<br /><br /> **电子邮件**  –在此类别中选择一个选项以将电子邮件服务与服务器集成。<br /><br /> **注意：** 此类别仅适用于 Windows Server Essentials。<br /><br /> **服务**  –在此类别中选择一个任务以将 Microsoft 联机服务与服务器集成。<br /><br /> **注意：** 此类别仅在已启用 Windows Server Essentials Experience 角色的 Windows Server Essentials 和 Windows Server 2012 R2 Standard 中可用。<br /><br /> **外接程序**  –单击此类别即可为你的业务安装宝贵的外接程序。<br /><br /> "**快速状态**" –显示高级服务器状态。 单击某个状态以查看有关该功能的信息和配置选项。 如果完成“设置”类别中的所有任务，则此类别将显示在“类别”窗格的顶部。<br /><br /> **帮助**  –使用 "搜索" 框在 Web 上搜索帮助。 单击某个链接以访问用于选定的支持选项的网站。|
|用户|对于需要访问 Windows Server Essentials 提供的资源的用户，你需要使用 Windows Server Essentials 仪表板来创建用户帐户。 在创建用户帐户后，可以使用仪表板的“用户”**** 页面上提供的任务来管理帐户。 可在此页面上执行的任务包括：<br /><br /> -查看用户帐户列表。<br /><br /> -查看和管理用户帐户属性。<br /><br /> -激活或停用用户帐户。<br /><br /> -添加或删除用户帐户。<br /><br /> -如果你的服务器与 Microsoft 365 集成，请将本地网络帐户分配给 Microsoft 联机服务帐户。<br /><br /> -更改用户帐户密码并管理密码策略。<br /><br /> 有关管理用户帐户的信息，请参阅 [管理用户帐户](Manage-User-Accounts-in-Windows-Server-Essentials.md)。|
|用户组|**注意：** 此功能仅在已启用 Windows Server Essentials Experience 角色的 Windows Server Essentials 和 Windows Server 2012 R2 Standard 中可用。<br /><br /> 可在此页面上执行的任务包括：<br /><br /> -查看用户组列表。<br /><br /> -查看和管理用户组。<br /><br /> -添加或删除用户组。|
|通讯组|**注意：** 此功能仅在已启用 Windows Server Essentials Experience 角色的 Windows Server Essentials 和 Windows Server 2012 R2 Standard 中可用。 仅当 Windows Server Essentials 与 Microsoft 365 集成时，才显示此选项卡。<br /><br /> 可在此页面上执行的任务包括：<br /><br /> -查看通讯组列表。<br /><br /> -添加或删除通讯组。|
|设备|在将计算机连接到 Windows Server Essentials 网络后，你可以通过仪表板的“设备”**** 页面管理计算机。 可在此页面上执行的任务包括：<br /><br /> -查看加入到网络的计算机的列表。<br /><br /> -通过利用 Microsoft 365 移动设备管理功能来管理移动设备。<br /><br /> **注意：** 此功能仅在已启用 Windows Server Essentials 体验角色的 Windows Server Essentials 和 Windows Server 2012 R2 Standard 中可用。<br /><br /> -查看每台计算机的计算机属性和运行状况警报。<br /><br /> -设置和管理计算机备份。<br /><br /> -将文件和文件夹还原到计算机。<br /><br /> -建立与计算机的远程桌面连接<br /><br /> -自定义计算机备份和文件历史记录设置<br /><br /> 有关管理计算机和备份的信息，请参阅 [管理设备](Manage-Devices-in-Windows-Server-Essentials.md)。|
|存储|默认情况下，仪表板的“存储”**** 部分包含以下部分，具体取决于你所运行的 Windows Server Essentials 版本。<br /><br /> -" **服务器文件夹** " 子节包含可帮助您查看和管理服务器文件夹属性的任务。 该页面还包括用于打开和添加服务器文件夹的任务。<br /><br /> -" **硬盘驱动器** " 页面包括的任务可帮助您查看和检查附加到服务器的驱动器的运行状况。<br /><br /> -在 Windows server Essentials 和 Windows Server 2012 R2 Standard 中，启用 Windows Server Essentials Experience 角色后， **SharePoint 库** 页面包含可帮助你在 Microsoft 365 service 中管理 SharePoint 库的任务。<br /><br /> 有关管理服务器文件夹的信息，请参阅 [管理服务器文件夹](Manage-Server-Folders-in-Windows-Server-Essentials.md)。<br /><br /> 有关管理硬盘驱动器的信息，请参阅 [管理服务器存储](Manage-Server-Storage-in-Windows-Server-Essentials.md)。|
|应用程序|-默认情况下，Windows Server Essentials 仪表板的 " **应用程序** " 部分包含两个子部分。<br /><br /> 有关管理外接程序应用程序的信息，请参阅 [管理应用程序](Manage-Applications-in-Windows-Server-Essentials.md)。<br /><br /> -" **外接程序** " 子节显示已安装加载项的列表，并提供使您能够删除外接程序和访问有关选定外接程序的其他信息的任务。<br /><br /> - **Microsoft** "查找" 子节显示 microsoft 查明可用的应用程序的列表。|
|Microsoft 365|仅当 Windows Server Essentials 与 Microsoft 365 集成时，" **Microsoft 365** " 选项卡才会显示。 本部分包含 Microsoft 365 订阅和管理员帐户信息。|

> [!NOTE]
>  如果为 Windows Server Essentials 仪表板安装一个加载项，则该加载项将可能创建其他管理部分。 这些部分可能会显示在主导航栏或子部分选项卡上。

##  <a name="access-the-windows-server-essentials-dashboard"></a><a name="BKMK_AccessDb"></a> 访问 Windows Server Essentials 仪表板
 可以使用以下方法之一来访问仪表板。 具体选择哪种方法取决于你是从服务器、从连接到 Windows Server Essentials 网络的计算机，还是从远程计算机访问仪表板。

 若要帮助维护安全网络，则只有具有管理权限的用户才可以访问 Windows Server Essentials 仪表板。 此外，不能使用内置管理员帐户从快速启动板登录到 Windows Server Essentials 仪表板。

###  <a name="access-the-dashboard-from-the-server"></a><a name="BKMK_Server"></a> 从服务器访问仪表板
 在安装 Windows Server Essentials 后，设置过程将在“开始”**** 屏幕以及桌面上创建仪表板的快捷方式。 如果这些位置中缺少该快捷方式，则可以使用“搜索”**** 窗格来查看并运行仪表板程序。

##### <a name="to-access-the-dashboard-from-the-server"></a>从服务器访问仪表板

-   以管理员身份登录到服务器，然后执行以下任何操作：

    -   在“开始”**** 屏幕上，单击“仪表板”****。

    -   在桌面上，双击“仪表板”****。

    -   在“搜索”**** 窗格中键入 **dashboard**，然后在搜索结果中单击“仪表板”****。

###  <a name="access-the-dashboard-from-a-computer-that-is-connected-to-the-network"></a><a name="BKMK_Network"></a> 从连接到网络的计算机访问仪表板
 在 Windows Server Essentials 中，在将计算机加入到网络后，管理员可以使用快速启动板从该计算机访问服务器仪表板。

> [!WARNING]
>  在 Windows Server Essentials 中，若要从客户端计算机连接到仪表板，请右键单击任务栏图标，然后从上下文菜单中打开仪表板。

##### <a name="to-access-the-dashboard-by-using-the-launchpad"></a>使用快速启动板访问仪表板

1.  从加入到网络的计算机打开“快速启动板”****。

2.  在快速启动板菜单上，单击“仪表板”****。

3.  在仪表板“登录”页面**** 上，键入你的网络管理员凭据，然后按 Enter 键。

     此时将打开到 Windows Server Essentials 仪表板的远程连接。

###  <a name="access-the-dashboard-from-a-remote-computer"></a><a name="BKMK_Remote"></a> 从远程计算机访问仪表板
 在远程计算机上工作时，可以使用远程 Web 访问站点访问 Windows Server Essentials 仪表板。

##### <a name="to-access-the-dashboard-by-using-remote-web-access"></a>使用远程 Web 访问来访问仪表板

1.  从远程计算机打开 Internet 浏览器，如 Internet Explorer。

2.  在 Internet 浏览器地址栏中，键入以下内容：**https://<DomainName \> /remote**，其中 *DomainName* 是组织的外部域名 (例如 contoso.com) 。

3.  键入用户名和密码以登录到远程 Web 访问站点。

4.  在远程 Web 访问**主页**的 "**计算机**" 部分中;找到你的服务器，然后单击 "**连接**"。

     此时将打开到仪表板的远程连接。

    > [!NOTE]
    >  如果你的服务器未在“主页”页面的“计算机”**** 部分中显示，请单击“连接到多台计算机”****，在列表中查找你的服务器，然后单击该服务器以进行连接。
    >
    >  若要授予用户从远程 Web 访问访问仪表板的权限，请打开该用户帐户的 "属性" 页，然后在 "**随处访问**" 选项卡上选择 "**服务器仪表板**" 选项。

##  <a name="use-the-safe-mode"></a><a name="BKMK_UseSafeMode"></a> 使用安全模式
 Windows Server Essentials 的安全模式功能将监视安装在服务器上的加载项。 如果仪表板变得不稳定或无响应，则安全模式将检测出可能导致此问题的加载项并将其隔离，在你下次打开仪表板时，这些加载项将显示在“安全模式设置”**** 页面上。 在“安全模式设置”**** 页面中，你可以逐个禁用和启用加载项，以确定导致问题的加载项。 然后，可以选择在未来启动时禁用该加载项，或者可以卸载该加载项。

 你随时可以查看服务器上安装的所有加载项列表。 你还可以在安全模式下打开仪表板，这会自动禁用所有非 Microsoft 加载项。Windows Server Essentials 还允许你通过网络上的另一台计算机在安全模式下访问仪表板。

#### <a name="to-view-a-list-of-installed-add-ins"></a>查看已安装的加载项列表

-   从仪表板单击“帮助”****，然后单击“安全模式设置”****。

#### <a name="to-open-the-dashboard-in-safe-mode"></a>在安全模式下打开仪表板

-   在“搜索”**** 窗格中，键入 **safe**，然后在搜索结果中单击“仪表板(安全模式)”****。

#### <a name="to-open-the-dashboard-in-safe-mode-from-another-computer-on-the-network"></a>通过网络上的其他计算机在安全模式下打开仪表板

1.  通过连接到网络的计算机打开 Windows Server Essentials 快速启动板，然后单击“仪表板”****。

2.  在仪表板登录页面上，键入有权登录服务器的帐户的用户名及密码，选中“允许我选择要加载的加载项”**** 复选框，然后单击箭头以进行登录。

## <a name="additional-references"></a>其他参考

-   [管理应用程序](Manage-Applications-in-Windows-Server-Essentials.md)

-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)
