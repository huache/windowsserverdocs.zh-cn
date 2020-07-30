---
title: 将 Windows Server Essentials 体验部署为托管服务器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: a455c6b4-b29f-4f76-8c6b-1578b6537717
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 63f5a72cf070b1520815f8f8f59d9c6ecf386aa5
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181253"
---
# <a name="deploy-windows-server-essentials-experience-as-a-hosted-server"></a>将 Windows Server Essentials 体验部署为托管服务器

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本文档包含的信息特定于希望在其实验室中部署装有 Windows Server Essentials 体验角色（在文档的其余部分中称为 Windows Server Essentials）的 Microsoft Windows Server 16 的托管商，并打算为其客户提供 Windows Server Essentials 体验作为服务。 此文档包括以下各节：


-   [Windows Server Essentials 体验概述](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_WSEEOverview)

-   [托管 Windows Server Essentials 体验的优点](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Benefits)

-   [支持的部署选项](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedDeployment)

-   [支持的网络拓扑](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedToplogy)

-   [自定义 Windows Server Essentials 体验角色的映像](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_CustomizeImage)

-   [自动部署 Windows Server Essentials 体验](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_AutomateDeployment)

-   [将数据从 Windows Small Business Server 迁移到 Windows Server Essentials 体验](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Migrate)

-   [通过使用 Windows PowerShell 执行常见任务](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_PowerShell)

-   [与 Windows Server Essentials 的电子邮件集成](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_EmailIntegration)

-   [通过使用本机工具进行监视和管理](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Monitoring)

-   [测试方案](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Scenarios)

-   [支持信息](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Support)


##  <a name="windows-server-essentials-experience-overview"></a><a name="BKMK_WSEEOverview"></a>Windows Server Essentials 体验概述
 Windows Server Essentials 体验是 Windows Server 2012 R2 Standard 和 Windows Server 2012 R2 Datacenter 中可用的服务器角色。 当 Windows Server Essentials Experience 角色安装在运行 Windows Server 2012 R2 的服务器上时，客户可以利用 Windows Server Essentials 中提供的所有功能，而无需锁定和限制。 Windows Server Essentials 体验为中小型企业启用以下跨界解决方案：

-   **数据存储和保护**你可以通过备份网络中的服务器和客户端计算机（小于75）将客户的 "存储数据" 存储在一个集中的位置，并保护服务器和客户端数据。

-   **用户管理**可以通过简化的服务器仪表板来管理用户和组。 此外，通过与 Microsoft Azure Active Directory （Azure AD）的集成，用户可以使用其域凭据轻松访问 Microsoft 联机服务（例如，Office 365、Exchange Online 和 SharePoint Online）。

-   **服务集成**你可以将服务器与 Microsoft 联机服务（如 Office 365、SharePoint Online 和 Microsoft Azure 备份）集成。 还可以将服务器与你的服务或由第三方提供商提供的服务集成。

-   **随处访问**客户几乎可以从任何有 Internet 连接的位置通过使用几乎所有设备访问服务器、网络计算机和数据。 远程 Web 访问为用户提供了在访问应用程序和数据时简化的、触摸友好的浏览器体验。 "我的服务器" 应用使他们能够访问 Windows Phone 或 Microsoft Store 应用中的数据。

-   **媒体流式处理**如果在启用了 Windows Server Essentials Experience 的服务器上安装媒体包，则最终用户可以将音乐、视频和照片存储在共享文件夹中，然后从联网的计算机或远程 Web 访问访问这些媒体文件。

-   **运行状况监视**你可以监视网络运行状况并获得自定义的运行状况报告。

##  <a name="benefits-of-hosting-windows-server-essentials-experience"></a><a name="BKMK_Benefits"></a>托管 Windows Server Essentials 体验的优点
  Windows Server Essentials 体验是 Windows Server 中的一个角色，因此你可以重复使用 Windows Server 中的现有部署和管理框架来部署和配置 Windows Server Essentials 体验角色。 托管 Windows Server Essentials 体验角色具有以下优点：

-   **简化的部署**只需打开 Windows Server Essentials 体验角色，一些最常用的角色和功能就会启用，并配置为适用于中小型企业的最佳做法。 可以自定义 Windows Server Essentials 功能，或隐藏某些本地功能。 如果使用 Windows Azure Pack，则可以下载 windows server 2012 R2 上 Windows Server Essentials 体验的库模板。

-   **简化仪表板** Windows Server Essentials 仪表板简化了常见任务，如管理服务器文件夹、服务器存储、备份和还原、用户或组帐户、设备、远程访问和电子邮件。 中小型企业客户可以执行日常管理任务，而不是呼叫服务台来寻求技术支持。

-   **扩展性** Windows Server Essentials 仪表板和 Windows Server Essentials 连接器软件都是可扩展的。 你可以添加自己的品牌和服务集成，以便你的客户在所有有关其服务器和服务内容中都有一个入口点。

-   **监视**新版本的 System Center 监视包可用来监视并管理运行 Windows Server Essentials 的多台服务器。 若要下载管理包，请参阅[适用于 Windows Server Essentials 的 System Center 管理包](https://www.microsoft.com/download/details.aspx?id=40809)。

##  <a name="supported-deployment-options"></a><a name="BKMK_SupportedDeployment"></a>支持的部署选项
  Windows Server Essentials 体验可以作为域控制器部署到新的 Active Directory 环境中;也可以将其作为域成员部署到现有 Active Directory 环境中。

 建议首先部署 Windows Server 2012 R2 Standard 或 Windows Server 2012 R2 Datacenter，然后安装 Windows Server Essentials 体验角色。 利用此部署方法，你可以获得 Windows Server Essentials edition 的所有功能，而无需锁和限制。


 有关安装带有 Windows Server Essentials 体验角色的 Windows Server 2012 R2 的详细信息，请参阅[安装和配置 Windows Server essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)。



##  <a name="supported-network-topologies"></a><a name="BKMK_SupportedToplogy"></a>支持的网络拓扑
 若要从漫游客户端使用 Windows Server Essentials 体验，应启用 VPN。 若要允许从漫游客户端远程访问到服务器，你需要在服务器上打开端口 443 和端口 80。

 以下是两个典型的服务器端网络拓扑，同时介绍了如何配置 VPN 和远程 Web 访问：

- **拓扑 1** （这是首选拓扑，它将所有服务器和 VPN IP 范围放置在同一子网中）：

  -   设置在网络地址转换 (NAT) 设备下的单独虚拟网中的服务器。

  -   在虚拟网中启用 DHCP 服务，或者向服务器分配静态 IP 地址。

  -   将路由器上的公用 IP 端口 443 转发到服务器的本地网络地址。

  -   允许 VPN 对端口 443 直通。

  -   将 VPN IPv4 地址池设置在与服务器地址相同的子网范围中。

  -   向第二台服务器分配同一个子网中的静态 IP 地址，但不是 VPN 地址池中的地址。

- **拓扑 2**：

  -   向服务器分配专用 IP 地址。

  -   允许服务器上的端口 443 达到公用端口 443 IP 地址。

  -   允许 VPN 对端口 443 直通。

  -   为 VPN IPv4 地址池和服务器地址分配不同的范围。

  通过拓扑 2，将不支持第二台服务器方案，因为无法将另一台服务器添加到同一域中。

  可以通过使用我们的 Windows PowerShell 脚本，在无人参与部署期间启用 VPN，或者可以在初始配置后借助向导来配置 VPN。

  若要使用 Windows PowerShell 启用 VPN，请使用管理权限在运行 Windows Server Essentials 的服务器上运行以下命令，并提供所有必要的信息。

```
##
## To configure external domain and SSL certificate (if not yet done in unattended Initial Configuration).
##

$myExternalDomainName = 'remote.contoso.com';   ## corresponds to A or AAAA DNS record(s) that can be resolved on Internet and routed to the server
$mySslCertificateFile = 'C:\ssl.pfx';   ## full path to SSL certificate file
$mySslCertificatePassword = ConvertTo-SecureString  œAsPlainText  œForce '******';   ## password for private key of the SSL certificate
$skipCertificateVerification = $true;   ## whether or not, skip verification for the SSL certificate

Set-WssDomainNameConfiguration  œDomainName $myExternalDomainName  œCertificatePath $mySslCertificateFile  œCertificateFilePassword $mySslCertificatePassword  œNoCertificateVerification
##
## To install VPN with static IPv4 pool (and allow all existing users to establish VPN).
##

Install-WssVpnServer -IPv4AddressRange ('192.168.0.160','192.168.0.240') -ApplyToExistingUsers;

```

> [!NOTE]
>  如果在客户接管服务器之前不能提供 VPN 连接，请确保服务器端口 3389 可通过 Internet 访问，以便客户可以使用远程桌面协议连接到服务器并对其进行配置。

##  <a name="customize-the-image-of-windows-server-essentials-experience-role"></a><a name="BKMK_CustomizeImage"></a>自定义 Windows Server Essentials 体验角色的映像
 在配置 Windows Server Essentials 体验角色之前可以自定义映像。 若要了解标准 Windows Server Sysprep 过程，请参阅 [Windows 评估和部署工具包](https://msdn.microsoft.com/library/hh825420.aspx)。 在使用 Sysprep 准备好映像后，可以使用它或将它封装到 Install.wim 中，以供进行新部署。

 如果你使用的是虚拟机管理器，则可以使用正在运行的实例来创建模板。 此过程使用 Sysprep 准备实例，并关闭计算机。 将模板存储在库中之后，可以根据情况使用它。

 安装 Windows Server Essentials 体验角色后，可以自定义 Windows Server Essentials 中的功能。 最重要的自定义之一是 **IsHosted** 注册表项： **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\Deployment\IsHosted**。

 如果将此项设置为 0x1，将会更改一些本地功能的行为。 这些功能更改包括：

- **客户端备份**默认情况下将针对新加入的客户端计算机关闭客户端备份。

- **客户端还原服务**将禁用客户端还原服务，并且在仪表板中隐藏该 UI。

- **文件历史记录**服务器将不会自动管理新创建用户帐户的文件历史记录设置。

- **服务器备份**将禁用服务器备份服务，并且在仪表板中隐藏服务器备份 UI。

- **存储空间**将在仪表板中隐藏用于创建或管理存储空间的 UI。

- **随处访问**在运行设置随处访问向导时，默认情况下将跳过路由器和 VPN 配置。

  如果想要控制列出的每个功能的行为，你可以为每个功能设置相应的注册表项。 有关如何设置注册表项的信息，请参考 [在 Windows Server 2012 R2 中自定义和部署 Windows Server Essentials](https://technet.microsoft.com/library/dn293241.aspx)

##  <a name="automate-the-deployment-of-windows-server-essentials-experience"></a><a name="BKMK_AutomateDeployment"></a>自动部署 Windows Server Essentials 体验
 若要自动执行部署，你需要先部署操作系统，然后安装 Windows Server Essentials 体验角色。

-   若要自动部署 Windows Server 2012 R2 Standard 或 Windows Server 2012 R2 Datacenter，请按照[Windows 评估和部署工具包](https://msdn.microsoft.com/library/hh825420.aspx)中的说明进行操作。

-   若要了解如何使用 Windows PowerShell 安装 Windows Server Essentials 体验角色，请参阅[安装和配置 Windows Server essentials](https://technet.microsoft.com/library/dn281793.aspx)。

> [!NOTE]
>  确保主机虚拟机和 Windows Server Essentials 体验的时区设置相同。 否则，可能会遇到一些错误。 其中包括：服务器的初始配置可能不会对证书相关任务成功，证书可能在安装 Windows Server Essentials Experience 角色后的几小时内不起作用，并且设备信息将不会正确更新。

 在部署之后，使用 Windows PowerShell cmdlet **Get-WssConfigurationStatus** 来验证初始配置是否已成功。 返回的状态应为以下状态之一：“Notstarted” ****、“FinishedWithWarning” ****、“Running” ****、“Finished” ****、“Failed” **** 或“PendingReboot” ****。

 在初始配置期间，将重新启动服务器。 如果你需要防止自动重新启动，在开始初始配置之前，可以使用以下命令添加注册表项：

```
New-ItemProperty "HKLM:\Software\Microsoft\Windows Server\Setup"Ã‚Â  -Name "WaitForReboot" -Value 1 -PropertyType "DWord" -Force -Confirm:$false

```

 开始进行初始配置后，可以使用 **Get-WssConfigurationStatus** 检查初始配置状态，当状态为“PendingReboot”**** 时，可以重新启动服务器。

##  <a name="migrate-data-from-windows-small-business-server-to-windows-server-essentials-experience"></a><a name="BKMK_Migrate"></a>将数据从 Windows Small Business Server 迁移到 Windows Server Essentials 体验
 你可以将数据从运行 Windows Small Business Server 2011、Windows Small Business Server 2008、Windows Small Business Server 2003 或 Windows Server Essentials 的服务器迁移到运行 Windows Server Essentials 的服务器。 查看针对本地2migrations 的[迁移到 Windows Server Essentials](../migrate/Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)迁移指南，并根据你的托管环境进行必要的自定义。

> [!NOTE]
>  建议将源服务器和目标服务器放在同一个子网内。 如果无法放在同一子网内，请确保：
>
> - 源服务器和目标服务器可以访问彼此的 "存储内部 DNS 名称"。
>   -   所有必要的端口都已打开。

 迁移完成后，你可以升级许可证以删除锁定和限制。 有关详细信息，请参阅[从 Windows Server Essentials 转换到 Windows server 2012 Standard](https://technet.microsoft.com/library/jj247582.aspx)。

##  <a name="perform-common-tasks-by-using-windows-powershell"></a><a name="BKMK_PowerShell"></a>使用 Windows PowerShell 执行常见任务
 本部分介绍一些可以通过使用 Windows PowerShell 执行的常见任务。

### <a name="enable-remote-web-access"></a>启用远程 Web 访问
 **语法**：

 Enable-WssRemoteWebAccess [-SkipRouter] [-DenyAccessByDefault] [-ApplyToExistingUsers]

 **示例**：

 $Enable-WssRemoteWebAccess œDenyAccessByDefault œApplyToExistingUsers

 此命令将启用“远程 Web 访问”并自动配置路由器，并改变全部现有用户的默认访问权限。

### <a name="add-user"></a>添加用户
 **语法**：

 Add-wssuser [-Name] <string \> [-Password] <securestring \> [-AccessLevel <string \> {User &#124; Administrator}] [-FirstName <string \> ] [-LastName <string \> ] [-AllowRemoteAccess] [-AllowVpnAccess] [<CommonParameters \> ]

 **示例**：

 $password = Convertto-html-SecureString "Passw0rd！" -asplaintext œforce $ Add-wssuser-Name User2Test-Password $password-Accesslevel Administrator-FirstName

 此命令将添加一个名为 User2Test 的管理员，其中包含 password Passw0rd！。

### <a name="add-server-folder"></a>添加服务器文件夹
 **语法**：

 Add-wssfolder [-Name] <string \> [-Path] <string \> [[-Description] <string \> ] [-KeepPermissions] [<CommonParameters \> ]

 **示例**：

 $Add-WssFolder -Name "MyTestFolder" -Path "C:\ServerFolders\MyTestFolder"

 此命令将在指定位置添加一个名为 MyTestFolder 的服务器文件夹。

##  <a name="email-integration-with-windows-server-essentials"></a><a name="BKMK_EmailIntegration"></a>Windows Server Essentials 的电子邮件集成
 你可以将 Windows Server Essentials 体验与 Office 365 或托管 Exchange Server 集成。 如果你希望你的客户使用托管的电子邮件，则需要开发外接程序以将 Windows Server Essentials 体验与托管的电子邮件解决方案集成。 有关详细信息，请参阅 [Windows Server Essentials SDK](https://msdn.microsoft.com/library/gg513877.aspx)。

##  <a name="monitor-and-manage-by-using-native-tools"></a><a name="BKMK_Monitoring"></a>使用本机工具进行监视和管理
 本部分讨论在 Windows Server 2012 R2 中提供的可用于监视和管理服务器的本机工具。

### <a name="group-policy"></a>组策略
  Windows Server Essentials Experience 利用 Windows Server 2012 R2 中的本机组策略支持，并提供了一个用户界面来配置文件夹重定向和安全设置。

> [!NOTE]
>  在托管环境中，用户配置文件的文件夹重定向一旦启用，当数据量很大时就有可能增加最终用户的登录时间。

### <a name="system-center-monitoring-pack"></a>System Center 监视包
 适用于 Windows Server Essentials 体验的 System Center 监视包将监视运行状况警报系统，以帮助你管理运行 Windows Server Essentials 的大量服务器，这些服务器专用于小型企业组织。 有关详细信息，请参阅[适用于 Windows Server Essentials 的 System Center 管理包](https://www.microsoft.com/download/details.aspx?id=40809)。

### <a name="backup-and-restore"></a>备份和还原
  带有 Windows Server Essentials 体验的 windows Server 2012 R2 允许你备份网络中的服务器和客户端计算机。

#### <a name="server-backup"></a>服务器备份
 Windows Server Essentials 支持采用两种方式备份服务器：本地备份和异地备份。 如果你想要部署自己的服务器备份解决方案，你可以自定义这些选项。

-   **本地备份** 允许你定期执行块级的增量备份，并备份到独立的硬盘上。 作为主机托管服务提供商，你可以将虚拟硬盘附加到运行 Windows Server Essentials 的虚拟机上，然后将服务器备份配置到此虚拟硬盘上。 虚拟硬盘应位于与运行 Windows Server Essentials 的虚拟机不同的物理磁盘上。

    > [!NOTE]
    >  如果你有其他的虚拟机的备份解决方案，并且不希望让用户看到 Windows Server Essentials 本机服务器备份功能，可以将其关闭，并从仪表板中删除相关的用户界面。 有关详细信息，请参阅 [自定义和部署 Windows Server 2012 R2 中的 Windows Server Essentials](https://technet.microsoft.com/library/dn293413.aspx) 的 [自定义服务器备份](https://technet.microsoft.com/library/dn293241.aspx)部分。

-   **异地备份** 允许你定期地将服务器数据备份到基于云的服务。 您可以下载并安装适用于 Windows Server Essentials 的 Microsoft Azure 备份集成模块，以利用 Microsoft 提供的 Azure 备份。

     有关详细信息，请参阅[管理服务器备份](../manage/Manage-Server-Backup-in-Windows-Server-Essentials.md)中的将 Windows Azure Backup 与 Windows Server Essentials 集成部分。

     如果你或你的用户希望使用其他云服务，你应该考虑以下各项：

    -   更新仪表板的用户界面，使其链接到首选的云服务而不是默认的 Azure 备份。

    -   （可选）为仪表板开发外接程序来配置和管理基于云的备份服务。

#### <a name="client-computer-backup"></a>Client Computer Backup
 Windows Server Essentials 体验支持两种方式的客户端数据备份：完全客户端备份和“文件历史记录”。

> [!NOTE]
>  备份客户端可能会影响到性能，因为数据需要通过 VPN 从客户端传送到服务器。

##### <a name="full-client-backup"></a>完全客户端备份
 默认情况下，为所有连接到 Windows Server Essentials 网络的客户端设备启用完全客户端备份。 这将会完全备份客户端的系统信息和数据，并支持重复数据删除。 备份数据将存储在运行 Windows Server Essentials 的服务器上。 这使得失败的客户端可以从以前的备份点中检索数据。

 完全客户端计算机备份需要考虑以下几点：

-   **性能** 客户端初始备份可能很耗时，因为要上载的数据量非常大。

-   **稳定性** 有时 Internet 连接在客户端上不稳定。 客户端备份设计为自动恢复，并且在每次备份 40 GB 数据时，客户端备份数据库都会创建一个检查点。 如果你预计 Internet 连接不可靠，则可将此容量值改小。

    -   若要启用检查点作业，请执行以下操作：在服务器上，将注册表项“HKLM\Software\Microsoft\Windows Server\Backup\GetCheckPointJobs” **** 设置为 1。

    -   若要更改检查点阈值，请执行以下操作：在客户端上，更改“HKLM\Software\Microsoft\Windows Server\Backup\CheckPointThreshold” **** 的 40 GB 的默认值。

-   **客户端裸机还原** 因为 Windows 预安装环境不支持 VPN 连接，所以不支持客户端裸机还原。 应按照 [自定义和部署 Windows Server 2012 R2 中的 Windows Server Essentials](https://technet.microsoft.com/library/dn293241.aspx)中的步骤来隐藏客户端还原服务任务。

##### <a name="file-history"></a>文件历史记录
 文件历史记录是 Windows 8.1 和 Windows 8 中的一项功能，用于将配置文件数据（库、桌面、联系人、收藏夹）备份到网络共享。 可以集中管理所有加入到 Windows Server Essentials 网络且运行 Windows 8.1 或 Windows 8 的计算机的文件历史记录设置。 备份数据存储在运行 Windows Server Essentials 的服务器上。 你应按照在[Windows server 2012 R2 中自定义和部署 Windows Server Essentials](https://technet.microsoft.com/library/dn293241.aspx)中的步骤来隐藏客户端还原服务任务

### <a name="storage-management"></a>存储管理
 存储空间允许你将分散的硬盘的物理存储容量集合起来，以动态地增加硬盘，并根据指定的修复能力级别创建数据卷。 可以在主机上或虚拟机上执行此操作。 如果你希望在运行 Windows Server Essentials 的虚拟机中隐藏此功能，请按照 [自定义和部署 Windows Server 2012 R2 中的 Windows Server Essentials](https://technet.microsoft.com/library/dn293241.aspx)中的说明进行操作。

##  <a name="test-scenarios"></a><a name="BKMK_Scenarios"></a>测试方案
 从托管的角度来看，建议你测试以下方案：


-   [服务器部署](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerDeploy)

-   [服务器配置](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerConfig2)

-   [服务器管理](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerManage)

-   [客户端体验](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ClientXP)


###  <a name="server-deployment"></a><a name="BKMK_ServerDeploy"></a>服务器部署
 你可以测试以下服务器部署方案：

-   在实验室环境中将运行 Windows Server 2012 R2 的服务器部署为域控制器，然后安装 Windows Server Essentials 体验角色。

-   在实验室环境中部署运行 Windows Server 2012 R2 的服务器，将此服务器加入到现有域，然后安装 Windows Server Essentials 体验角色。

-   根据需要自定义 Windows Server Essentials 映像。

-   使用无人参与的文件与 Windows PowerShell 自动部署 Windows Server Essentials。

-   将运行 Windows Small Business Server 的本地服务器迁移到运行 Windows Server Essentials 的托管服务器。

###  <a name="server-configuration"></a><a name="BKMK_ServerConfig2"></a>服务器配置
 你可以测试以下服务器配置方案：

-   配置随处访问（虚拟专用网络、远程 Web 访问和 DirectAccess）。

-   配置存储及服务器文件夹。

-   打开 BranchCache。

-   （如需要）配置服务器备份、在线备份、客户端备份和文件历史记录。

-   （如需要）配置并管理存储空间。

-   （如需要）配置电子邮件解决方案集成（Office 365 和托管的 Exchange Server）。

-   （如需要）配置与其他 Microsoft Online Services 的集成。

-   （如需要）配置 Media Server（媒体服务器）。

###  <a name="server-management"></a><a name="BKMK_ServerManage"></a>服务器管理
 你可以测试以下服务器管理方案：

-   管理用户和组。

-   配置并接收电邮通知警报。

-   运行最佳做法分析程序以查看是否存在错误或警告消息。

-   配置 System Center Operations Manager 包。

-   操作系统发生损坏时，配置服务器恢复。

###  <a name="client-experience"></a><a name="BKMK_ClientXP"></a>客户端体验
 可以测试以下最终用户方案：

-   通过 Internet 部署客户端（PC 或 Mac 操作系统）。

-   使用客户端上的快速启动板访问共享文件夹。

-   从不同的设备（电脑、手机和平板电脑）通过远程 Web 访问来访问服务器资源。

-   访问适用于 Windows Phone 的“我的服务器”应用。

-   （如需要）访问文件历史记录、客户端备份和还原以及文件夹重定向。

-   （如需要）验证电子邮件集成体验。

##  <a name="support-information"></a><a name="BKMK_Support"></a>支持信息
 您可以下载 Windows Server Essentials 软件开发工具包（SDK）和 Windows Server Essentials 评估和部署工具包（ADK）：

-   [Windows Server Essentials 软件开发工具包](https://msdn.microsoft.com/library/gg513877.aspx)SDK

-   [在 Windows Server 2012 R2 中自定义和部署 Windows Server Essentials](https://technet.microsoft.com/library/dn293241.aspx)

## <a name="additional-references"></a>其他参考

-   [Windows Server Essentials 中的新增功能](../get-started/what-s-new.md)

-   [安装 Windows Server Essentials](Install-Windows-Server-Essentials.md)

-   [Windows Server Essentials 入门](../get-started/get-started.md)
