---
title: 托管 Windows Server Essentials
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: fda5628c-ad23-49de-8d94-430a4f253802
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 5cf3498c2028650857d0aa2f35d796c441b0ca70
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80817840"
---
# <a name="hosted-windows-server-essentials"></a>托管 Windows Server Essentials

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本文档包含的信息特定于希望在其实验室中部署 Windows Server Essentials 并向其客户提供 Windows Server Essentials 即服务的托管商。  
  
## <a name="what-is-windows-server-essentials"></a>什么是 Windows Server Essentials？  
 Windows Server Essentials 是一种跨界小企业解决方案，它结合了同类最佳的64位产品技术，可为绝大多数的小型企业提供非常适用的服务器环境。 Windows Server Essentials 中包括以下技术。  
  
 **服务器操作系统：** Windows Server 2012 产品技术提供 Windows Server Essentials 的核心。 有关详细信息，请访问 [Windows Server 2012 网站](https://www.microsoft.com/server-cloud/products/windows-server-2012-r2/default.aspx#fbid=ZH0GD_CRAWh)。  
  
 **数据保护：** Windows Server Essentials 利用 Windows Server 2012 中提供的多项新功能来提供极大地改进的数据保护功能。 [最新“存储空间”功能](https://technet.microsoft.com/library/hh831739.aspx) 允许你将分散的硬盘的物理存储容量集合起来，以动态地增加硬盘，并根据指定的修复能力级别创建数据卷。 Windows Server Essentials 可以对服务器本身以及连接到网络的客户端计算机执行完整的系统备份和裸机还原，现在支持大于 2 TB 的卷。 作为 Windows Server 2012 的新功能， [Windows Azure Online Backup](https://technet.microsoft.com/library/hh831419.aspx) 可用于保护由微软管理的云存储服务中的文件和文件夹。 Windows Server Essentials 还能集中管理和配置 Windows 8.1 客户端的文件历史记录功能，帮助用户从意外删除或覆盖的文件中恢复，而无需管理员帮助。  
  
 **随处访问：** 远程 Web 访问旨在提供精简的触摸式浏览器体验：几乎可从任何具有 Internet 连接的位置、使用几乎任何设备访问应用程序和数据。 Windows Server Essentials 还为 Windows 8.1 客户端计算机提供更新的 Windows Phone 应用程序和新应用程序，允许用户直观地连接、搜索并访问服务器上的文件和文件夹。 当与服务器的连接变得可用时，文件还可自动高速缓存，以便脱机访问和同步。 Windows Server Essentials 将虚拟专用网络（VPN）设置为只需几次单击即可轻松完成向导驱动的过程，并简化对用户的 VPN 访问的管理。 客户端计算机可以通过 VPN 连接来远程连接 Windows SBS 的环境，且无需在办公室中就能操作。  
  
 **工作负载灵活性：** Windows Server Essentials 旨在允许客户灵活地选择本地运行的应用程序和服务以及在云中运行的应用程序和服务。 在以前的版本中，Windows Small Business Server Standard 将 Exchange Server 作为自己的一个组建产品，客户想要使用云端消息服务和协作服务时就必须多花费用，而且操作更加复杂。 使用 Windows Server Essentials，无论用户选择运行 Exchange Server 的本地副本、订阅托管 Exchange 服务还是订阅 Microsoft Office 365，客户都可以利用同一种集成管理体验。  
  
 **运行状况监视：** Windows Server Essentials 监视其自己的运行状况状态，以及运行 Windows 8.1、Windows 7 和 Mac OS X 版本10.5 及更高版本的客户端计算机的状态。 运行状况会显示与计算机备份、服务器存储、磁盘空间不足等相关的结果或问题。  
  
 **扩展性：** Windows Server Essentials 在 Windows SBS 2011 Essentials 的扩展性模型的基础上构建，它允许其他软件供应商向核心产品添加功能和功能，并添加一组新的 web 服务 Api。 而且，它还兼容现有的 [软件开发工具包](https://msdn.microsoft.com/library/gg513958.aspx) (SDK) 和为 Windows SBS 2011 Essentials 而创建的 [加载项](https://pinpoint.microsoft.com/applications/search?fpt=300105&q=small+business+server+essentials) 。  
  
## <a name="how-can-i-customize-an-image"></a>我怎样自定义映像?  
 请参阅[Windows Server essentials](https://go.microsoft.com/fwlink/p/?LinkID=249124)，它是一个标准的 windows server sysprep 过程，其中包含其他 Windows server essentials 自定义步骤。 如需结束自定义，可按照 [创建简单的自定义映像](https://technet.microsoft.com/library/jj200117) 和 [自定义该映像](https://technet.microsoft.com/library/jj200161)中的说明，然后按照 [准备要部署的映像](https://technet.microsoft.com/library/jj200142) 中的说明来捕捉最终映像。  
  
 请注意以下几点：  
  
1. 通过向任一驱动器的根目录添加 SkipIC.txt 文件来跳过初始配置 (IC)。 在安装服务器之后和进行初始配置之前，按组合键 Shift+F10 打开命令窗口，并在 C:/驱动器下创建 SkipIC.txt 文件。 自定义之后，切记删除该 SkipIC.txt 文件。  
  
2. 如果需要在小于 90 GB 的磁盘上部署 Windows Server Essentials，则应在 sysprep 之前添加一个注册表项：  
  
   ```  
   %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v HWRequirementChecks /t REG_DWORD /d 0 /f  
   ```  
  
   系统准备完成后，便可使用系统准备的磁盘映像，或重新封装回 Install.wim 以进行新的部署。  
  
   如果你使用的是“虚拟机管理器”，则可使用正在运行的实例来创建模板。 创建模板时会对实例进行系统准备，并关闭该服务器。 将其存储在程序库中，可根据情况提出实例。  
  
##  <a name="how-do-i-automate-the-deployment"></a><a name="BKMK_automatedeployment"></a>如何实现自动部署？  
 获取自定义映像后，你可以用自己的映像来部署。 如需进行半自动安装，你必须为 WinPE 设置提供或部署 unattend.xml。 若要执行完全无人参与的安装，还需要为 Windows Server Essentials 初始配置提供 cfg .ini 文件。  
  
1. 仅执行无人值守式 WinPE 设置。 这操作只能自动设置 WinPE，并使安装在“初始配置”之前停止，以便最终用户在 RDP 至服务器会话之后自己提供公司、域名及管理员的信息。 为此，请执行以下操作：  
  
   1.  提供 Windows unattend.xml 文件。 按照[WINDOWS 8.1 ADK](https://go.microsoft.com/fwlink/?LinkId=248694)生成文件，并提供所有必要的信息，包括服务器名称、产品密钥和管理员密码。 在 unattend.xml 文件的 "Microsoft Windows-设置" 部分，提供如下所示的信息。  
  
       ```  
       <InstallFrom>  
                <MetaData>  
                    <Key>IMAGE/WINDOWS/EDITIONID</Key>  
                    <Value>ServerSolution</Value>  
                </MetaData>  
                <MetaData>  
                    <Key>IMAGE/WINDOWS/INSTALLATIONTYPE</Key>  
                    <Value>Server</Value>  
                </MetaData>  
          </InstallFrom>  
       ```  
  
   2.  必须在公共 IP 上打开 RDP 端口3389，以便客户可以使用 unattend.xml 文件中指定的管理员和密码通过 RDP 连接到服务器以完成初始配置。  
  
   > [!NOTE]
   >  如果不修改默认密码，则服务器安装将会停在要求输入密码的屏幕上。**注意** 最终用户必须使用默认的管理员账号登录服务器并执行“初始配置”。  
  
   如果你使用的是“虚拟机管理器”，则当从模板创建新的实例时，可在控制台指定系统管理员密码。  
  
2. 执行完全无人值守式设置，包括无人值守式“初始配置”。 为此，请执行以下操作：  
  
   1.  如果部署是从 WinPE 设置开始，请按上述操作提供 unattend.xml 文件。  
  
   2.  请参阅名为的 Windows Server Essentials ADK 部分，[创建 Cfg 文件](https://technet.microsoft.com/library/jj200150)以生成 cfg。  
  
   3.  在 [InitialConfiguration] 中提供信息。  
  
       ```  
       WebDomainName=yourdomainname  
       TrustedCertFileName=c:\cert\a.pfx  
       TrustedCertPassword=Enteryourpassword  
       EnableVPN=true  
       EnableRWA=true  
       ; Provide all information so that after setup is complete, your customer can use your domain name to visit the server directly with the admin/user information you provide in the [InitialConfiguration] section.  
  
       VpnIPv4StartAddress=<IPV4Address>  
       VpnIPv4EndAddress=<IPV4Address>  
       VpnBaseIPv6Address=<IPV6Address>  
       VpnIPv6PrefixLength=<number>  
       ; Provide this information. IPv4StartAddress and IPv4Endaddress are required so that your VPN client can acquire valid IP through this range.  
  
       IPv4DNSForwarder=<IPV4Address,IPV4Address,Â¦>  
       IPv6DNSForwarder=<IPV6Address,IPV6Address,Â¦>  
       ; Provide this information as needed according to your network environment settings.  
       ```  
  
   4.  在 [PostOSInstall] 中提供信息。  
  
       ```  
       IsHosted=true   
       ; Must have, this will prevent Initial Configure webpage available for other computers under same subnet.  
  
       StaticIPv4Address=<IPV4Address>  
       StaticIPv4Gateway=<IPV4Address>  
       StaticIPv6Address=<IPV6Address>  
       StaticIPv6SubnetPrefixLength=<number>  
       StaticIPv6Gateway=<IPV6Address>  
       ; All these are optional if you have DHCP Server Service on the subnet, otherwise provide static IP here.  
       ```  
  
   5.  如果提供了 WebDomainName 参数，请确保还要将 DNS 记录更新为指向服务器的公共 IP。  
  
   6.  如果没有提供上述 WebDomainName 信息，请确保打开端口 3389 以便客户能够使用 RDP 连接到服务器并结束 VPN 配置。  
  
> [!NOTE]
>  确保 VM 主机服务器和 Windows Server Essentials VM 的时区设置相同。 否则，可能会出现几种不同的错误（“初始配置”可能在证书相关的任务上会失效；证书在安装之后几小时仍未生效；设备信息更新不正确；等等）。  
  
 部署后，请检查 HKLM\software\windows server\setup 路径下的下列注册表项，以验证“初始配置”是否成功。 如果 SetupStage == ICDone && ICStatus == 1，则表示“初始配置”成功完成。  
  
## <a name="what-is-the-supported-network-topology"></a>支持何种网络拓扑?  
 若要从漫游客户端使用 Windows Server Essentials，则应启用 VPN。 我们建议启用 443 端口进行 VPN SSTP 连接。 如果“媒体服务器”需要用于“远程网站访问”或“网站服务应用”，则还应启用 80 端口。  
  
 如果启用 VPN ，可在无人值守的部署中通过 Windows PowerShell 脚本完成，或者可以在初始配置后用我们的向导来配置。  
  

- 若要在无人参与部署期间启用 VPN，请参阅本文档中的 [How do I automate the deployment?](Hosted-Windows-Server-Essentials.md#BKMK_automatedeployment) 。  

- 若要在无人参与部署期间启用 VPN，请参阅本文档中的 [How do I automate the deployment?](../install/Hosted-Windows-Server-Essentials.md#BKMK_automatedeployment) 。  

  
- 如需通过 Windows PowerShell 启用 VPN，请根据管理权限运行以下 cmdlet， 并提供所有的必要信息。  
  
  ```  
  ##  
  ## To configure external domain and SSL certificate (if not yet done in unattended Initial Configuration).  
  ##  
  
  $myExternalDomainName = 'remote.contoso.com';   ## corresponds to A or AAAA DNS record(s) that can be resolved on Internet and routed to the server  
  $mySslCertificateFile = 'C:\ssl.pfx';   ## full path to SSL certificate file  
  $mySslCertificatePassword = ConvertTo-SecureString '******';   ## password for private key of the SSL certificate  
  $skipCertificateVerification = $true;   ## whether or not, skip verification for the SSL certificate  
  
  Add-Type -AssemblyName 'Wssg.Web.DomainManagerObjectModel';  
  [Microsoft.WindowsServerSolutions.RemoteAccess.Domains.DomainConfigurationHelper]::SetDomainNameAndCertificate($myExternalDomainName,$mySslCertificateFile,$mySslCertificatePassword,$skipCertificateVerification);  
  ##  
  ## To install VPN with static IPv4 pool (and allow all existing users to establish VPN).  
  ##  
  
  Install-WssVpnServer -IPv4AddressRange ('192.168.0.160','192.168.0.240') -ApplyToExistingUsers;  
  ```  
  
  如果在为客户提供服务器之前不能提供 VPN 连接，请确保服务器端口 3389 可以通过 Internet 访问，以便最终用户能够使用 RDP 连接到服务器并自己完成配置。  
  
  以下是两个典型的服务器端网络拓扑布局，同时介绍了 VPN/远程网站访问 (RWA) 如何配置：  
  
- 拓扑 1（优先选用）  
  
  -   NAT 设备下的服务器采用独立虚拟网络。  
  
  -   虚拟网络中已启用 DHCP 服务，或者该服务器已分配静态 IP 地址。  
  
  -   服务器端口 443 可从公共 IP 端口 443 获得。  
  
  -   端口 443 允许使用 VPN 通道。  
  
  -   VPN IPv4 地址池的范围应与该服务器地址的子网相同。  
  
  -   任何第二台服务器均应在同一子网内分配一个静态 IP，但需在 VPN 地址池之外。  
  
- 拓扑 2：  
  
  -   该服务器有一个专用 IP 地址。  
  
  -   可从公共 IP 地址 s 端口443访问服务器上的端口443。  
  
  -   端口 443 允许使用 VPN 通道。  
  
  -   VPN IPv4 地址池处于与该服务器地址不同的范围。  
  
  拓扑 2 不支持第二台服务器的方案。  
  
## <a name="how-do-i-perform-common-tasks-via-windows-powershell"></a>我如何通过 Windows PowerShell 执行常见任务?  
 **启用远程 Web 访问**  
  
```  
Enable-WssRemoteWebAccess [-SkipRouter] [-DenyAccessByDefault] [-ApplyToExistingUsers]  
```  
  
 示例：  
  
```  
$Enable-WssRemoteWebAccess  œDenyAccessByDefault  œApplyToExistingUsers  
```  
  
 此命令将启用“远程 Web 访问”并自动配置路由器，并改变全部现有用户的默认访问权限。  
  
 **添加用户**  
  
```  
Add-WssUser [-Name] <string> [-Password] <securestring> [-AccessLevel <string> {User | Administrator}] [-FirstName <string>] [-LastName <string>] [-AllowRemoteAccess] [-AllowVpnAccess]   [<CommonParameters>]  
```  
  
 示例：  
  
```  
$password = ConvertTo-SecureString "Passw0rd!" -asplaintext  œforce  
$Add-WssUser -Name User2Test -Password $password -Accesslevel Administrator -FirstName User2 -LastName Test  
```  
  
 此命令将添加一个名为 User2Test 的管理员，其中包含 password Passw0rd！。  
  
 **启用/禁用用户**  
  
 示例：  
  
```  
$CurrentUser = get-wssuser  œname user2test  
$CurrentUser.UserStatus = 0  
$CurrentUser.Commit()  
```  
  
 此命令将禁用名为 user2test 的用户。 如果将 UserStatus 设定为 1，将会启用该用户。  
  
 **添加服务器文件夹**  
  
```  
Add-WssFolder [-Name] <string> [-Path] <string> [[-Description] <string>] [-KeepPermissions] [<CommonParameters>]  
```  
  
 示例：  
  
```  
$Add-WssFolder -Name "MyTestFolder" -Path "C:\ServerFolders\MyTestFolder"  
```  
  
 此命令将在指定位置添加一个名为 MyTestFolder 的服务器文件夹。  
  
## <a name="how-do-i-add-a-second-server-to-the-windows-server-essentials-domain"></a>如何实现向 Windows Server Essentials 域添加第二台服务器？  
 由于 Windows Server Essentials 是域控制器，因此可以采用标准方式将第二台服务器加入域。  
  
## <a name="which-email-solutions-can-be-integrated"></a>可以集成哪一种电子邮件解决方案?  
 Windows Server Essentials 支持与现成的两种电子邮件解决方案集成： Office 365 和本地 Exchange。 如果你正在运行自己的托管电子邮件解决方案，则需要开发外接程序以将 Windows Server Essentials 与托管的电子邮件解决方案集成。  
  
## <a name="how-do-i-migrate-on-premises-windows-sbs-201120082003-to-the-hosted-windows-server-essentials"></a>如何实现将本地 Windows SBS （2011/2008/2003）迁移到托管的 Windows Server Essentials？  
 迁移指南可用于本地 Windows Small Business Server （Windows SBS）到 Windows Server Essentials 的迁移。 有些步骤可能不完全适用于你的托管环境。 然而，普通的迁移任务和工作负载应该是同样的。 建议你参考 [迁移指南](https://go.microsoft.com/fwlink/p/?LinkID=254292) 并根据自己的托管环境进行必要的自定义。  
  
 建议将源服务器和目标服务器放在同一个子网内。 如果无法放在同一子网内，请确保：  
  
-   源服务器和目标服务器的内部 DNS 名称可相互访问。  
  
-   所有必要的端口都已打开。  
  
## <a name="how-can-i-upgrade-windows-server-essentials-to-windows-server-standard"></a>如何将 Windows Server Essentials 升级到 Windows Server Standard？  
 你可以将 Windows Server Essentials 升级到 Windows Server Standard。 解除锁定和限制，添加 Windows Server Standard 缺少的程序包。 若要获取详细信息，请 [下载文档](https://go.microsoft.com/fwlink/p/?LinkID=253181)。  
  
## <a name="what-are-the-native-tools-for-monitoring-and-management"></a>监测和管理所用的本机工具有哪些？  
  
### <a name="group-policy-management"></a>组策略管理  
 Windows Server Essentials 利用 Windows Server 2012 中的本机组策略支持，并提供了用于配置文件夹重定向和安全设置的用户界面。  
  
> [!NOTE]
>  在托管环境中，用户配置文件的文件夹重定向一旦启用，当数据量很大时就有可能增加最终用户的登录时间。  
  
### <a name="management-pack"></a>管理包  
 Windows Server Essentials 管理包通过 Windows Server Essentials 中的运行状况警报系统提供监视功能，以帮助托管商管理专用于不同小型企业公司的大量 Windows Server Essentials 服务器。 此版本的监测功能仅包括系统内的严重警报。  
  
#### <a name="management-pack-scope"></a>管理包作用域  
 此管理包可帮助你监视特定于 Windows Server Essentials 的功能。 它无法监测 Windows Server 2012 Standard 操作系统中的通用功能。 为了监视 Windows Server Essentials，应同时使用 windows server Essentials 管理包和 Windows Server 2012 Standard 管理包。  
  
#### <a name="mandatory-configuration"></a>必须要进行的配置  
 需执行以下步骤方可使用管理包：  
  
1.  安装“代理”并利用证书信任配置信任关系。 由于 Windows Server Essentials 已预配置为域控制器，并且不能与其他域或林信任，因此应在 Windows Server Essentials 上安装 System Center operations Manager 代理，并使用管理对其进行配置信任使用证书的服务器。  
  
2.  下载管理包。 若要使用 Operations Manager 2007 监视 Windows Server Essentials，你必须首先从管理包目录中下载[Windows Server 操作系统管理包](https://connect.microsoft.com/WindowsServer/Downloads/DownloadDetails.aspx?DownloadID=45010)。  
  
3.  下载管理包文件。 如果你正在使用管理包的本地化版本，则需同时导入主要管理包文件和语言包。  
  
#### <a name="files-in-this-monitoring-pack"></a>在此“监测包”中的文件  
 适用于 Windows Server Essentials 的监视包包括以下文件：  
  
-   Microsoft.Windows.Server.2012.Essentials.mp  
  
-   \>< 区域设置的区域设置。  
  
### <a name="back-up-and-restore"></a>备份和还原  
 Windows Server Essentials 允许备份服务器和客户端。  
  
#### <a name="back-up-the-server"></a>备份服务器  
 Windows Server Essentials 支持两种方式备份服务器：本地备份和非本地备份。  
  
 **本地备份**允许你定期执行块级的增量备份，并备份到独立的硬盘上。 作为宿主，你可以将虚拟磁盘附加到 Windows Server Essentials VM，并将服务器备份配置到此虚拟磁盘。 虚拟磁盘应位于与 Windows Server Essentials VM 不同的物理磁盘上。  
  
- 如果你有另一种机制来备份 Windows Server Essentials VM，并且你不希望用户看到 Windows Server Essentials 本机服务器备份功能，则可以将其关闭并从 Windows Server Essentials 中删除所有相关的用户界面板. 有关详细信息，请参阅[ADK 文档](https://go.microsoft.com/fwlink/p/?LinkID=249124)的 "自定义服务器备份" 一节。  
  
  **非本地备份**允许你定期地将服务器数据备份到云计算服务。 您可以下载并安装适用于 Windows Server Essentials 的 Microsoft Azure 备份集成模块，以利用 Microsoft 提供的 Azure 备份。  
  
  如果你或你的用户喜欢别的云服务，可以：  
  
1.  更新 Windows Server Essentials 仪表板的用户界面，使其提供指向你的首选云服务的链接，而不是默认的 Azure 备份。 有关详细信息，请参考 [ADK 文档](https://go.microsoft.com/fwlink/p/?LinkID=249124)的“自定义映像”一节。  
  
2.  可有可无开发用于 Windows Server Essentials 仪表板的外接程序，以配置和管理云备份服务。  
  
#### <a name="back-up-the-client"></a>备份客户端  
 Windows Server Essentials 支持两种类型的客户端数据备份：完全客户端备份和文件历史记录。  
  
> [!NOTE]
>  备份客户端可能会影响到性能，因为数据需要通过 VPN 从客户端传送到服务器。  
  
 对于所有连接到 Windows Server Essentials 网络的客户端设备，默认情况下都是**完全客户端备份**。 它以递增的方式备份完全客户端（系统及数据），并支持重复数据删除。 备份数据将位于运行 Windows Server Essentials 的服务器上。 客户端一旦发生故障，可以使其数据返回到上一个备份点。 你可以按照[ADK 文档](https://technet.microsoft.com/library/jj200150)的创建 Cfg 文件部分中的步骤关闭此功能。  
  
 完全客户端备份需要考虑以下几点：  
  
- 性能：客户端初始备份可能很耗时，因为要上载的数据量相当大。  
  
- 稳定性：有时客户端侧的 Internet 连接不稳定。 客户端备份是可恢复的，默认检查点是 40GB（每完成 40GB 的数据备份，客户端备份数据库就会创建一个检查点）。 如果你预计 Internet 连接不可靠，则可将此容量值改小。  
  
  -   如需启用检查点，可在服务器上将注册表项 HKLM\Software\Microsoft\Windows\server\Backup\GetCheckPointJobs 设为 1。  
  
  -   如需改变检查点的阈值，可在客户端改变 HKLM\Software\Microsoft\Windows\server\Backup\CheckPointThreshold 的默认值 (40GB)。  
  
- 客户端裸机恢复：因为 Windows Preinstall Environment（预安装环境）不支持 VPN 连接，所以不支持客户端裸机备份。  
  
  **文件历史记录**是一项 Windows 8.1 功能，用于将配置文件数据（库、桌面、联系人、收藏夹）备份到网络共享。 在 Windows Server Essentials 中，我们允许对所有连接到 Windows Server Essentials 的 Windows 8.1 客户端的 "文件历史记录" 设置进行集中管理。 备份数据存储在运行 Windows Server Essentials 的服务器上。 你可以按照[ADK 文档](https://technet.microsoft.com/library/jj200150)的创建 Cfg 文件部分中的步骤关闭此功能。  
  
### <a name="storage-management"></a>存储管理  
 [最新“存储空间”功能](https://technet.microsoft.com/library/hh831739.aspx) 允许你将分散的硬盘的物理存储容量集合起来，以动态地增加硬盘，并根据指定的修复能力级别创建数据卷。 你还可以将 iSCSI 磁盘附加到 Windows Server Essentials 以扩展其存储。  
  
## <a name="what-are-the-main-scenarios-i-should-test"></a>我应该测试什么样的主要场景？  
 从托管的视角来看，建议你测试以下场景：  
  
 **服务器部署**  
  
- 在实验室环境中部署 Windows Server Essentials 服务器。  
  
- 根据需要自定义 Windows Server Essentials 映像。  
  
- 利用无人参与的文件和 cfg 来自动部署 Windows Server Essentials。  
  
- 将本地 Windows SBS 迁移到托管的 Windows Server Essentials。  
  
- 从 Windows Server Essentials 升级到 Windows Server 2012。  
  
  **服务器配置**  
  
- 配置随处访问（VPN、远程 Web 访问、DirectAccess）。  
  
- 配置存储及服务器文件夹。  
  
- （如需要）配置服务器备份、在线备份、客户端备份和 文件历史记录。  
  
- （如需要）配置并管理存储空间。  
  
- （如需要）配置电子邮件解决方案集成（Office 365、托管 Exchange，等等）。  
  
- （如需要）配置 Media Server（媒体服务器）。  
  
  **服务器管理**  
  
- 管理用户。  
  
- 配置并接收电邮通知警报。  
  
- 在发生错误或发出警告的情况下，运行 BPA。  
  
- 配置系统中心监控包。  
  
- 在数据损坏的情况下配置服务器恢复。  
  
  **客户端体验**  
  
- 通过 Internet（个人计算机或 Mac 操作系统）进行客户端部署。  
  
- 使用客户端上的启动面板访问“共享文件夹”。  
  
- 从不同的设备（个人计算机、手机、平板电脑）通过“远程 Web 访问”访问服务器资产。  
  
- Windows Phone 的“我的服务器“。  
  
- （如适用）文件历史记录、客户端备份与恢复（无 BMR）、文件夹重定向。  
  
- （如适用）电邮集成体验。  
  
## <a name="where-can-i-get-more-support"></a>我在哪里可以获得更多支持？  
 你可以从下面的链接获取软件开发工具包 (SDK) 和 应用系统开发包 (ADK) 文件：  
  
- [SDK](https://go.microsoft.com/fwlink/p/?LinkID=248648)  
  
- [ADK](https://go.microsoft.com/fwlink/p/?LinkID=249124)  
  
  你可以通过 Connect 向功能团队报告缺陷。 若要生成日志，请在服务器和连接该服务器的客户端两处压缩文件夹：C:\ProgramData\Microsoft\Windows Server\Logs。
