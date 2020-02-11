---
title: 部署 Windows Server 混合云打印
description: 如何设置 Microsoft 混合云打印
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: Windows Server 2016
ms.tgt_pltfrm: na
ms.topic: ''
ms.assetid: fc239aec-e719-47ea-92fc-d82a7247c5e9
author: msjimwu
ms.author: coreyp
manager: dongill
ms.date: 3/15/2018
ms.openlocfilehash: 77462ab74ee63677362b779615376e831c71de00
ms.sourcegitcommit: eca5bb75d1db20ac07232cea759b6b542626c02f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/10/2020
ms.locfileid: "77114526"
---
# <a name="deploy-windows-server-hybrid-cloud-print"></a>部署 Windows Server 混合云打印

>适用于：Windows Server 2016

本主题为 IT 管理员介绍了 Microsoft 混合云打印（HCP）解决方案的端到端部署。 此解决方案层位于作为打印服务器运行的现有 Windows Server 之上，并启用了 Azure Active Directory （Azure AD），并启用了 MDM 管理的设备，以发现和打印到组织托管的打印机。

## <a name="pre-requisites"></a>先决条件

开始此安装之前，需要获取多个订阅、服务和计算机。 它们是：

- Azure AD 高级订阅。

  请参阅[azure 订阅入门](https://azure.microsoft.com/trial/get-started-active-directory/)，了解 azure 的试用订阅。

- MDM 服务，例如 Intune。

  请参阅[Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) ，了解 Intune 的试用订阅。

- 运行 Active Directory 的 Windows Server 2016 或更高版本计算机。

  有关设置 Active Directory 的帮助，请参阅[在 Windows Server 2016 中设置 Active Directory](https://blogs.technet.microsoft.com/canitpro/2017/02/22/step-by-step-setting-up-active-directory-in-windows-server-2016/) 。

- 一个专用的、已加入域的 Windows Server 2016 或更高版本的计算机，作为打印服务器运行。

- 一个专用的、已加入域的 Windows Server 2016 或更高版本的计算机，作为连接器服务器运行。

  有关详细信息，请参阅[了解 Azure AD 应用程序代理连接器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors)。

- Windows 10 秋季创建者更新或更高版本的计算机，用于发布打印机。

- 面向公众的域名。

  你可以使用 Azure 为你创建的*域名（onmicrosoft.com*），或购买你自己的域名。 请参阅[使用 Azure Active Directory 门户添加自定义域名](https://docs.microsoft.com/azure/active-directory/fundamentals/add-custom-domain)。

## <a name="deployment-steps"></a>部署步骤

以下步骤适用于典型的混合云打印部署。

### <a name="step-1---install-azure-ad-connect"></a>步骤 1-安装 Azure AD Connect

1. Azure AD connect Azure AD 同步到本地 AD。 在带有 Active Directory 的 Windows Server 计算机上，下载并安装具有快速设置的 Azure AD Connect 软件。 请参阅[使用快速设置开始使用 Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-express)。

### <a name="step-2---install-application-proxy"></a>步骤 2-安装应用程序代理

1. 应用程序代理允许组织中的用户访问云中的本地应用程序。 在连接器服务器上安装应用程序代理。
    - 有关安装说明，请参阅[教程：在 Azure Active Directory 中通过应用程序代理添加用于远程访问的本地应用程序](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application)。
    - 如果组织具有复杂的网络拓扑，则建议使用专用连接器组。 请参阅[使用连接器组在单独的网络和位置上发布应用程序](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connector-groups)。

### <a name="step-3---register-and-configure-applications"></a>步骤 3-注册和配置应用程序

若要启用与 HCP 服务的经过身份验证的通信，需要创建3个应用程序：2个 Web 应用程序来表示两个 HCP 服务，1个本机应用程序用于与这些服务通信。

1. 登录到 Azure 门户以注册 web 应用。
    - 在 "Azure Active Directory" 下，中转到**应用注册** > "**新注册**"。

    ![AAD 应用注册1](../media/hybrid-cloud-print/AAD-AppRegistration.png)

    - 输入 Mopria 发现服务的应用名称。 单击 "**注册**" 完成操作。

    ![AAD 应用注册2](../media/hybrid-cloud-print/AAD-AppRegistration-Mopria.png)

    - 针对企业云打印服务重复此操作。
    - 对于本机应用重复此操作。
    - 这三个应用程序应显示在**应用注册**下。

    ![AAD 应用注册3](../media/hybrid-cloud-print/AAD-AppRegistration-AllApps.png)

2. 公开2个 Web 应用程序的 API。
    - 在**应用注册**边栏选项卡中，单击 Mopria 发现服务应用，选择 "**公开 API**"，然后单击 "应用程序 ID URI" 旁的 "**设置**"。

    ![AAD 公开 API 1](../media/hybrid-cloud-print/AAD-AppRegistration-Mopria-ExposeAPI.png)

    - 单击 "**保存**" 而不更改应用程序 ID URI 的默认值。 只需设置此值，稍后将进行更改。

    ![AAD 公开 API 2](../media/hybrid-cloud-print/AAD-AppRegistration-Mopria-ExposeAPI-Save.png)

    - 单击 "**添加作用域**"。

    ![AAD 公开 API 3](../media/hybrid-cloud-print/AAD-AppRegistration-Mopria-ExposeAPI-AddScope.png)

    - 提供一个作用域名称，允许管理员和用户同意，输入同意说明，然后单击 "**添加范围**" 完成操作。

    ![AAD 公开 API 4](../media/hybrid-cloud-print/AAD-AppRegistration-Mopria-ExposeAPI-ScopeName.png)

    - 针对企业云打印服务重复此操作。 请使用不同的范围名称和同意说明。

    ![AAD 公开 API 5](../media/hybrid-cloud-print/AAD-AppRegistration-ECP-ExposeAPI-ScopeName.png)

3. 添加 API 权限
    - 返回应用注册边栏选项卡。 单击 "本机应用" 并选择 "API 权限"。 单击 "**添加权限**"。

    ![AAD API 权限1](../media/hybrid-cloud-print/AAD-AppRegistration-APIPermission.png)

    - 切换到**我的组织使用的 api**，然后使用搜索框查找先前添加的 Mopria 发现服务。 从搜索结果中单击该服务。

    ![AAD API 权限2](../media/hybrid-cloud-print/AAD-AppRegistration-APIPermission-Mopria.png)

    - 选择 "**委托的权限**"。 选中 "API" 作用域旁边的复选框。 单击 "**添加权限**"。

    ![AAD API 权限3](../media/hybrid-cloud-print/AAD-AppRegistration-APIPermission-Mopria-Add.png)

    - 重复此步骤可向企业云打印服务添加权限。

    ![AAD API 权限4](../media/hybrid-cloud-print/AAD-AppRegistration-APIPermission-ECP-Add.png)

    - 返回到 "API 权限" 边栏选项卡后，请等待10秒钟，然后单击 "**总计管理员许可 ...** "。

    ![AAD API 权限5](../media/hybrid-cloud-print/AAD-AppRegistration-APIPermission-GrantConsent.png)

    - 出现提示时单击 **"是"** 。

    ![AAD API 权限6](../media/hybrid-cloud-print/AAD-AppRegistration-APIPermission-GrantConsent-Yes.png)

    - 验证是否显示 API 权限的 "状态" 列带有绿色复选标记。

    ![AAD API 权限7](../media/hybrid-cloud-print/AAD-AppRegistration-APIPermission-Verify.png)

4. 为 Web 应用程序配置应用程序代理
    - 请参阅 > **企业应用程序** > **所有应用**程序的**Azure Active Directory** 。 搜索 Mopria Discovery 服务并单击它。

    ![AAD 应用代理1](../media/hybrid-cloud-print/AAD-EnterpriseApp-AllApps.png)

    - 单击 "**应用程序代理**"。 使用格式 `https://<fully qualified domain name of the Print Server>/mcs/`输入内部 Url。 单击 "**保存**" 完成操作。

    ![AAD 应用代理2](../media/hybrid-cloud-print/AAD-EnterpriseApp-Mopria-AppProxy.png)

    - 针对企业云打印服务重复此操作。 请注意，内部 URL 是 `https://<fully qualified domain name of the Print Server>/ecp/`。

    ![AAD 应用代理3](../media/hybrid-cloud-print/AAD-EnterpriseApp-ECP-AppProxy.png)

    - 请参阅**Azure Active Directory** > **应用注册**。 单击 Mopria 发现服务。 请注意，在 "**概述**" 下，应用程序 ID URI 已从默认值更改为 "**应用程序代理**" 下的外部 URL。 此 URI 将在打印服务器安装过程中、客户端 MDM 策略和发布打印机中使用。

    ![AAD 应用代理4](../media/hybrid-cloud-print/AAD-AppRegistration-Mopria-Overview.png)

5. 将用户分配到应用程序
    - 请参阅 > **企业应用程序** > **所有应用**程序的**Azure Active Directory** 。 搜索 Mopria Discovery 服务并单击它
    - 单击 "**用户和组**"，然后单击 "**属性**" 并将 **"需要进行用户分配"** 更改为 "**否**"
    - 针对企业云打印服务重复此操作。

6. 在本机应用程序中配置重定向 URI
    - 请参阅**Azure Active Directory** > **应用注册**。 单击本机应用。 请参阅**概述**并复制**应用程序（客户端） ID**。

    ![AAD 重定向 URI 1](../media/hybrid-cloud-print/AAD-AppRegistration-Native-Overview.png)

    - 请参阅**身份验证**。 将 "**类型**" 下拉框更改为 "`Public...`"，然后使用以下格式输入两个重定向 uri，其中 `<NativeClientAppID>` 与上一步相同：

        `ms-appx-web://Microsoft.AAD.BrokerPlugin/<NativeClientAppID>`

        `ms-appx-web://Microsoft.AAD.BrokerPlugin/S-1-15-2-3784861210-599250757-1266852909-3189164077-45880155-1246692841-283550366`

    ![AAD 重定向 URI 2](../media/hybrid-cloud-print/AAD-AppRegistration-Native-Authentication.png)

    - 单击 "**保存**" 完成操作。

### <a name="step-4---setup-the-print-server"></a>步骤 4-设置打印服务器

1. 请确保打印服务器安装了所有可用 Windows 更新。 注意：必须将服务器2019修补为版本17763.165 或更高版本。
    - 安装以下服务器角色：
        - 打印服务器角色
        - Internet 信息服务（IIS）
    - 有关如何安装服务器角色的详细信息，请参阅[使用添加角色和功能向导安装角色、角色服务和功能](https://docs.microsoft.com/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#BKMK_installarfw)。

    ![打印服务器角色](../media/hybrid-cloud-print/PrintServer-Roles.png)

2. 安装混合云打印 PowerShell 模块。
    - 在提升权限的 PowerShell 命令提示符下运行以下命令：

        `find-module -Name "PublishCloudPrinter"` 以确认计算机可以访问 PowerShell 库（PSGallery）

        `install-module -Name "PublishCloudPrinter"`

    > 注意：你可能会看到一条消息，指出 "PSGallery" 是不受信任的存储库。  输入 "y" 以继续安装。

    ![打印服务器发布云打印机](../media/hybrid-cloud-print/PrintServer-PublishCloudPrinter.png)

3. 安装混合云打印解决方案。
    - 在已提升权限的 PowerShell 命令提示符下，将目录更改为以下内容（需要引号）：

        `"C:\Program Files\WindowsPowerShell\Modules\PublishCloudPrinter\1.0.0.0"`

    - 运行

        `.\CloudPrintDeploy.ps1 -AzureTenant <Azure Active Directory domain name> -AzureTenantGuid <Azure Active Directory ID>`

    - 请参阅下面的屏幕截图，查找 Azure Active Directory 域名。

    ![打印服务器如何获取 AAD 域名](../media/hybrid-cloud-print/PrintServer-GetAADDomainName.png)

    - 请参阅下面的屏幕截图，查找 Azure Active Directory ID。

    ![打印服务器云打印部署](../media/hybrid-cloud-print/PrintServer-GetAADId.png)

    - CloudPrintDeploy 脚本的输出如下所示：

    ![打印服务器云打印部署](../media/hybrid-cloud-print/PrintServer-CloudPrintDeploy.png)

    - 检查日志文件以查看是否存在任何错误： `C:\Program Files\WindowsPowerShell\Modules\PublishCloudPrinter\1.0.0.0\CloudPrintDeploy.log`

4. 在提升的命令提示符下运行**RegitEdit** 。 中转到计算机 \ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\CloudPrint\EnterpriseCloudPrintService。
    - 请确保将 AzureAudience 设置为企业云打印应用的应用程序 ID URI。
    - 请确保 AzureTenant 设置为 Azure AD 域名。

    ![打印服务器 ECP 注册表项](../media/hybrid-cloud-print/PrintServer-RegEdit-ECP.png)

5. 中转到计算机 \ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\CloudPrint\MopriaDiscoveryService。
    - 请确保 AzureAudience 是 Mopria Discovery 服务应用的应用程序 ID URI。
    - 请确保 AzureTenant 是 Azure AD 的域名。
    - 请确保 URL 是 Mopria 发现服务应用的应用程序 ID URI。

    ![打印服务器 Mopria 注册表项](../media/hybrid-cloud-print/PrintServer-RegEdit-Mopria.png)

6. 在提升 Powershell 命令提示符下运行**iisreset** 。 这将确保在上一步中所做的任何注册表更改都生效。

7. 将 IIS 终结点配置为支持 SSL。
    - SSL 证书可以是自签名证书，也可以是从受信任的证书颁发机构（CA）颁发的证书。
    - 如果使用自签名证书，请**确保将证书导入到客户端计算机**。
    - 如果向第三方提供商注册您的域，则需要配置带 SSL 证书的 IIS 终结点。 有关详细信息，请参阅此[指南](https://www.sslsupportdesk.com/microsoft-server-2016-iis-10-10-5-ssl-installation/)。

8. 安装 SQLite 包。
   - 打开提升权限的 PowerShell 命令提示符。
   - 运行以下命令以下载 system.exception nuget 包。

        `Register-PackageSource -Name nuget.org -ProviderName NuGet -Location https://www.nuget.org/api/v2/ -Trusted -Force`

   - 运行以下命令以安装包。

        `Install-Package system.data.sqlite [-requiredversion x.x.x.x] -providername nuget`

   > 注意：建议通过保留 "-requiredversion" 选项来下载并安装最新版本。

    ![打印服务器 Mopria 注册表项](../media/hybrid-cloud-print/PrintServer-InstallSQLite.png)

9. 将 SQLite dll 复制到 MopriaCloudService Webapp bin 文件夹（C:\inetpub\wwwroot\MopriaCloudService\bin）。
    - 创建包含下面的 PowerShell 脚本的 ps1 文件。
    - 将 $version 变量更改为在上一步中安装的 SQLite 版本。
    - 在提升权限的 PowerShell 命令提示符下运行 ps1 文件。

    ```powershell
    $source = "\Program Files\PackageManagement\NuGet\Packages"
    $core = "System.Data.SQLite.Core"
    $linq = "System.Data.SQLite.Linq"
    $ef6 = "System.Data.SQLite.EF6"
    $version = "x.x.x.x"
    $target = "C:\inetpub\wwwroot\MopriaCloudService\bin"

    xcopy /y "$source\$core.$version\lib\net46\System.Data.SQLite.dll" "$target\"
    xcopy /y "$source\$core.$version\build\net46\x86\SQLite.Interop.dll" "$target\x86\"
    xcopy /y "$source\$core.$version\build\net46\x64\SQLite.Interop.dll" "$target\x64\"
    xcopy /y "$source\$linq.$version\lib\net46\System.Data.SQLite.Linq.dll" "$target\"
    xcopy /y "$source\$ef6.$version\lib\net46\System.Data.SQLite.EF6.dll" "$target\"
    ```

10. 更新 c:\inetpub\wwwroot\MopriaCloudService\web.config 文件以在以下 `<runtime>/<assemblyBinding>` 节中包含 SQLite 版本 1.x. x. x. x. x. x. x. x. x. x。 这是在上一步骤中使用的相同版本。

    ```xml
    ...
    <dependentAssembly>
    assemblyIdentity name="System.Data.SQLite" culture="neutral" publicKeyToken="db937bc2d44ff139" /
    <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
    </dependentAssembly>
    <dependentAssembly>
    <assemblyIdentity name="System.Data.SQLite.Core" culture="neutral" publicKeyToken="db937bc2d44ff139" />
    <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
    </dependentAssembly>
    <dependentAssembly>
    <assemblyIdentity name="System.Data.SQLite.EF6" culture="neutral" publicKeyToken="db937bc2d44ff139" />
    <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
    </dependentAssembly>
    <dependentAssembly>
    <assemblyIdentity name="System.Data.SQLite.Linq" culture="neutral" publicKeyToken="db937bc2d44ff139" />
    <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
    </dependentAssembly>
    ...
    ```

11. 创建 SQLite 数据库。
    - 从 `https://www.sqlite.org/`下载并安装 SQLite 工具二进制文件。
    - 请参阅 `c:\inetpub\wwwroot\MopriaCloudService\Database` directory。
    - 执行以下命令以在此目录中创建数据库：

        `sqlite3.exe MopriaDeviceDb.db ".read MopriaSQLiteDb.sql"`

    - 在文件资源管理器中，打开 MopriaDeviceDb 文件属性以添加允许在 "安全" 选项卡中发布到 Mopria 数据库的用户或组。用户或组必须位于本地 Active Directory 中，并与 Azure AD 同步。
    - 如果将解决方案部署到不可路由的域（例如*mydomain*），则需要将 Azure AD 域（例如，onmicrosoft.com 或从第三方供应商购买的域）添加为本地 ACTIVE DIRECTORY 的 UPN*后缀。* 这样就可以在数据库文件的安全设置中添加与发布打印机的用户完全相同的用户（*例如 admin@ onmicrosoft.com）。* [有关目录同步，请参阅准备不可路由的域](https://docs.microsoft.com/office365/enterprise/prepare-a-non-routable-domain-for-directory-synchronization)。

    ![打印服务器 Mopria 注册表项](../media/hybrid-cloud-print/PrintServer-SQLiteDB.png)

### <a name="step-5-optional---configure-pre-authentication-with-azure-ad"></a>步骤 5 \[可选\] 配置预先身份验证 Azure AD

1. 查看文档[Kerberos 约束委派，以便通过应用程序代理进行单一登录到你的应用程序](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-kcd)。

2. 配置本地 Active Directory。
    - 在 Active Directory 计算机上，打开 "服务器管理器 **并 > "** **Active Directory 用户和计算机**"。
    - 导航到 "**计算机**" 节点，然后选择连接器服务器。
    - 右键单击并选择 " **属性**" -> **委派** "选项卡。
    - 选择 " **仅信任此计算机来委派指定的服务**"。
    - 选择 " **使用任何身份验证协议**"。
    - 在 "服务" 下 **，此帐户可以向其提供委派凭据**。
        - 添加打印服务器计算机的服务主体名称（SPN）。
        - 选择服务类型的主机。
    Active Directory 委托 ![](../media/hybrid-cloud-print/AD-Delegation.png)

3. 验证是否在 IIS 中启用了 Windows 身份验证。
    - 在打印服务器上，打开服务器管理器 > 工具 "> Internet 信息服务（IIS）管理器。
    - 导航到此站点。
    - 双击 "**身份验证**"。
    - 单击 " **Windows 身份验证**" 并单击 "**操作**" 下的 "**启用**"。
    ![打印服务器 IIS 身份验证](../media/hybrid-cloud-print/PrintServer-IIS-Authentication.png)

4. 配置单一登录。
    - 在 Azure 门户上，请参阅**Azure Active Directory** > **企业应用程序** > **所有应用程序**"。
    - 选择 MopriaDiscoveryService 应用。
    - 中转到 "**应用程序代理**"。 将预身份验证方法更改为**Azure Active Directory**。
    - 请参阅**单一登录**。 选择 "集成 Windows 身份验证" 作为单一登录方法。
    - 将 "**内部应用程序 spn** " 设置为打印服务器计算机的 spn。
    - 将**委派的登录标识**设置为 "用户主体名称"。
    - 对 EntperiseCloudPrint 应用重复此步骤。
    ![AAD 单一登录 IWA](../media/hybrid-cloud-print/AAD-SingleSignOn-IWA.png)

### <a name="step-6---configure-the-required-mdm-policies"></a>步骤 6-配置所需的 MDM 策略

1. 登录到 MDM 提供程序。
2. 查找企业云打印策略组并按照以下准则配置策略：
    - CloudPrintOAuthAuthority = `https://login.microsoftonline.com/<Azure AD Directory ID>`。 可以在 Azure Active Directory > "属性" 下找到该目录 ID。
    - CloudPrintOAuthClientId = "应用程序 \(的本机应用程序\) ID" 值。 你可以在 Azure Active Directory > "下找到此应用注册 > 选择" 本机应用 > 概述 "。
    - CloudPrinterDiscoveryEndPoint = Mopria Discovery 服务应用的外部 URL。 可以在 Azure Active Directory > 企业应用程序 "下找到此 > 选择" Mopria 发现服务应用 > 应用程序代理 "。 **它必须完全相同，但不包含结尾的 "/"** 。
    - MopriaDiscoveryResourceId = Mopria Discovery 服务应用的应用程序 ID URI。 你可以在 Azure Active Directory > "下找到此应用注册 > 选择" Mopria 发现服务应用 > 概述 "。 **它必须与尾随 "/" 完全相同**。
    - CloudPrintResourceId = 企业云打印应用的应用程序 ID URI。 可以在 Azure Active Directory > "应用注册 > 选择" 企业云打印应用 > 概述 "。 **它必须与尾随 "/" 完全相同**。
    - DiscoveryMaxPrinterLimit = \<正整数\>。

> 注意：如果使用 Microsoft Intune 服务，则可以在 "云打印机" 类别下找到这些设置。

|Intune 显示名称                     |策略                         |
|----------------------------------------|-------------------------------|
|打印机发现 URL                   |CloudPrinterDiscoveryEndpoint  |
|打印机访问授权 URL            |CloudPrintOAuthAuthority       |
|Azure Native client 应用 GUID            |CloudPrintOAuthClientId        |
|打印服务资源 URI              |CloudPrintResourceId           |
|要查询的最大打印机数（仅限移动设备）  |DiscoveryMaxPrinterLimit       |
|打印机发现服务资源 URI  |MopriaDiscoveryResourceId      |

> 注意：如果云打印策略组不可用，但 MDM 提供程序支持 OMA URI 设置，则可以设置相同的策略。  有关其他信息，请参阅[此](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint#enterprisecloudprint-cloudprintoauthauthority)信息。

    - OMA-URI 的值
        - CloudPrintOAuthAuthority =./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority
            - 值 = https://login.microsoftonline.com/<Azure AD Directory ID>
        - CloudPrintOAuthClientId =./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintOAuthClientId
            - 值 = Azure AD 本机应用的应用程序 ID < >
        - CloudPrinterDiscoveryEndPoint =./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint
            - 值 = Mopria 发现服务应用的外部 URL （必须完全相同，但不能包含结尾的 "/"）
        - MopriaDiscoveryResourceId =./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/MopriaDiscoveryResourceId
            - 值 = Mopria 发现服务应用的应用程序 ID URI
        - CloudPrintResourceId =./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintResourceId
            - 值 = 企业云打印应用的应用程序 ID URI
        - DiscoveryMaxPrinterLimit =./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit
            - 值 = 正整数
    
### <a name="step-7---publish-the-shared-printer"></a>步骤 7-发布共享打印机

1. 在打印服务器上安装所需的打印机。
2. 通过 "打印机属性" UI 共享打印机。
3. 选择要授予访问权限的用户组。
4. 保存更改并关闭 "打印机属性" 窗口。
5. 准备 Windows 10 秋季创建者更新或更高版本的计算机。 将计算机加入到 Azure AD，并以与本地 Active Directory 同步的用户身份登录，并向 MopriaDeviceDb 文件授予适当的权限。
6. 在 Windows 10 计算机上，打开提升的 Windows PowerShell 命令提示符。
    - 运行以下命令。
        - `find-module -Name "PublishCloudPrinter"` 以确认计算机可以访问 PowerShell 库（PSGallery）
        - `install-module -Name "PublishCloudPrinter"`

            > 注意：你可能会看到一条消息，指出 "PSGallery" 是不受信任的存储库。  输入 "y" 以继续安装。

        - `Publish-CloudPrinter`
        - Printer = 共享打印机名称。 此名称必须与在打印服务器上打开的打印机属性 "**共享**" 选项卡中显示的共享名称完全匹配。

        ![打印服务器打印机属性](../media/hybrid-cloud-print/PrintServer-PrinterProperties.png)

        - 制造商 = 打印机制造商。
        - 型号 = 打印机型号。
        - OrgLocation = 指定打印机位置的 JSON 字符串，例如

            `{"attrs": [{"category":"country", "vs":"USA", "depth":0}, {"category":"organization", "vs":"Microsoft", "depth":1}, {"category":"site", "vs":"Redmond, WA", "depth":2}, {"category":"building", "vs":"Building 1", "depth":3}, {"category":"floor_number", "vs":1, "depth":4}, {"category":"room_name", "vs":"1111", "depth":5}]}`

        - Sddl = 用于表示打印机权限的 SDDL 字符串。
            - 以管理员身份登录到打印服务器，然后针对要发布的打印机运行以下 PowerShell 命令： `(Get-Printer PrinterName -full).PermissionSDDL`。
            - 将**O:BA**作为前缀添加到上述命令中的结果。 例如 如果上一个命令返回的字符串为 "G:DUD：（A; OICI; FA;;;WD） "，然后 SDDL =" O:BAG： DUD：（A; OICI; FA;;;WD） "。
        - DiscoveryEndpoint = 登录到 Azure 门户然后从企业应用程序 > Mopria Discovery 服务应用程序 > 应用程序代理 > 外部 URL 获取字符串。 省略结尾的 "/"。
        - PrintServerEndpoint = 登录到 Azure 门户然后从企业应用程序 > 企业云打印应用程序 > 应用程序代理 > 外部 URL 获取字符串。 省略结尾的 "/"。
        - AzureClientId = 已注册的本机应用程序的应用程序 ID。
        - AzureTenantGuid = Azure AD 租户的目录 ID。
        - DiscoveryResourceId = Mopria Discovery 服务应用程序的应用程序 ID URI。

    - 也可以在命令行中输入所有必需的参数值。 语法为：

        `Publish-CloudPrinter -Printer <string> -Manufacturer <string> -Model <string> -OrgLocation <string> -Sddl <string> -DiscoveryEndpoint <string> -PrintServerEndpoint <string> -AzureClientId <string> -AzureTenantGuid <string> -DiscoveryResourceId <string>`

        示例命令：

        `Publish-CloudPrinter -Printer HcpTestPrinter -Manufacturer Manufacturer1 -Model Model1 -OrgLocation '{"attrs": [{"category":"country", "vs":"USA", "depth":0}, {"category":"organization", "vs":"MyCompany", "depth":1}, {"category":"site", "vs":"MyCity, State", "depth":2}, {"category":"building", "vs":"Building 1", "depth":3}, {"category":"floor_name", "vs":1, "depth":4}, {"category":"room_name", "vs":"1111", "depth":5}]}' -Sddl "O:BAG:DUD:(A;OICI;FA;;;WD)" -DiscoveryEndpoint "https://mopriadiscoveryservice-contoso.msappproxy.net/mcs" -PrintServerEndpoint "https://enterprisecloudprint-contoso.msappproxy.net/ecp" -AzureClientId "dbe4feeb-cb69-40fc-91aa-73272f6d8fe1" -AzureTenantGuid "8de6a14a-5a23-4c1c-9ae4-1481ce356034" -DiscoveryResourceId "https://mopriadiscoveryservice-contoso.msappproxy.net/mcs/"`

    - 使用以下命令验证是否已发布打印机。

        `Publish-CloudPrinter -Query -DiscoveryEndpoint <string> -AzureClientId <string> -AzureTenantGuid <string> -DiscoveryResourceId <string>`

        示例命令：

        `Publish-CloudPrinter -Query -DiscoveryEndpoint "https://mopriadiscoveryservice-contoso.msappproxy.net/mcs" -AzureClientId "dbe4feeb-cb69-40fc-91aa-73272f6d8fe1" -AzureTenantGuid "8de6a14a-5a23-4c1c-9ae4-1481ce356034" -DiscoveryResourceId "https://mopriadiscoveryservice-contoso.msappproxy.net/mcs/"`

## <a name="verify-the-deployment"></a>验证部署

在配置了 MDM 策略的 Azure AD 联接设备上：
- 打开 web 浏览器并中转*到 https://mopriadiscoveryservice-的 msappproxy.net/mcs/services。*
- 应该会看到描述此终结点功能集的 JSON 文本。
- 请参阅 "**设置**" > **设备** > **打印机 & 扫描器**"。
    - 单击 "**添加打印机或扫描程序**"。
    - 应该会看到 "搜索云打印机" （或 "在我的组织中搜索打印机" 的最新的 Windows 10 计算机）链接。
    - 单击链接。
    - 单击 "请选择一个搜索位置" 链接。
        - 应会看到设备位置层次结构。
    - 选择一个位置，然后单击 **"确定"** ，然后单击 "**搜索**" 按钮查找打印机。
    - 选择 "打印机"，然后单击 "**添加设备**按钮"。
    - 安装成功后，请从喜欢的应用打印到打印机。

> 注意：如果使用 "EcpPrintTest" 打印机，则可以在打印服务器计算机的 "C：\\ECPTestOutput\\EcpTestPrint" 位置下找到输出文件。

## <a name="troubleshooting"></a>故障排除

下面是 HCP 部署过程中的常见问题

|错误 |建议的步骤 |
|------|------|
|CloudPrintDeploy PowerShell 脚本失败 | <ul><li>确保 Windows Server 具有最新更新。</li><li>如果使用 Windows Server Update Services （WSUS），请参阅[如何在使用 WSUS/SCCM 时提供按需功能和语言包](https://docs.microsoft.com/windows/deployment/update/fod-and-lang-packs)。</li></ul> |
|SQLite 安装失败，出现以下消息：检测到包 "system.string" 的依赖关系循环 | 安装包 SkipDependencies-providername nuget-providername<br>安装包 EF6-providername nuget-SkipDependencies<br>安装包 system.object-providername-providername nuget-SkipDependencies<br><br>成功下载包后，请确保它们都是相同的版本。 如果没有，请将-requiredversion 参数添加到上述命令，并将其设置为相同版本。 |
|发布打印机失败 | <ul><li>对于 "直通预身份验证"，请确保为发布打印机的用户提供对发布数据库的适当权限。</li><li>对于 Azure AD 预身份验证，请确保在 IIS 中启用 Windows 身份验证。 请参阅步骤5.3。 此外，先尝试先传递预身份验证。 如果直通预身份验证正常工作，则问题可能与应用程序代理有关。 请参阅[排查应用程序代理问题和错误消息](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-troubleshoot)。 请注意，切换到 passthrough 会重置单一登录设置;重新访问步骤5，重新设置 Azure AD 预身份验证。</li></ul> |
|打印作业处于 "发送到打印机" 状态 | <ul><li>确保连接器服务器上启用了 TLS 1.2。 请参阅步骤2.1 中的链接项目。</li><li>确保连接器服务器上已禁用 HTTP2。 请参阅步骤2.1 中的链接项目。</li></ul> |

下面是可以帮助进行故障排除的日志的位置

|组件 |日志位置 |
|------|------|
|Windows 10 客户端 | <ul><li>使用事件查看器查看 Azure AD 操作的日志。 单击 "**开始**"，然后键入 "事件查看器"。 导航到应用程序和服务日志 > Microsoft > Windows > AAD > 操作。</li><li>使用反馈中心收集日志。 请参阅[通过反馈中心应用将反馈发送到 Microsoft](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)</li></ul> |
|连接器服务器 | 使用事件查看器查看应用程序代理的日志。 单击 "**开始**"，然后键入 "事件查看器"。 导航到应用程序和服务日志 > Microsoft > AadApplicationProxy > 连接器 > Admin。 |
|打印服务器 | 可在 C:\inetpub\logs\LogFiles\W3SVC1. 中找到 Mopria 发现服务应用和企业云打印应用的日志 |
