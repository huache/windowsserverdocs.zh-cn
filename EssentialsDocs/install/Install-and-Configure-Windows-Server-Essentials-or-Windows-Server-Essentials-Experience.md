---
title: 安装和配置 Windows Server Essentials 或 Windows Server Essentials 体验
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 48ea6cd4-3955-4aaf-9236-2515a6c3e730
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: dfd0611d47c159e629efff11073bec084e175a43
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626269"
---
# <a name="install-and-configure-windows-server-essentials-or-windows-server-essentials-experience"></a>安装和配置 Windows Server Essentials 或 Windows Server Essentials 体验

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

对于具有最多25个用户和50设备的小型企业，Windows Server Essentials 是理想的第一台服务器。 对于具有最多100用户和200设备的组织，你现在可以使用安装了 Windows Server Essentials Experience 角色的 Windows Server 2012 R2。 本主题将介绍这两种方案。

Windows Server Essentials 体验是 Windows Server 2016 中的一种角色，可让你充分利用在 windows Server Essentials 中可供你使用的所有功能 () Web 访问例如 Windows server essentials 中未实施的锁定和限制。 此服务器角色在 Windows Server Essentials 中也可用，并在默认情况下处于启用状态。

在安装 Windows Server Essentials 或 Essentials 体验角色之前，请注意以下限制。

|Windows Server Essentials 中的 windows Server Essentials 体验|Windows server 2016 中的 windows Server Essentials 体验
|----|----|
|-必须是位于林和域的根的域控制器，并且必须保留所有 FSMO 角色。<br /><br /> -无法安装在具有预先存在的 Active Directory 域 (的环境中，但是，在执行迁移) 需要21天的宽限期。|-如果安装在具有预先存在的 Active Directory 域的环境中，则无需成为域控制器。<br /><br /> -如果 Active Directory 域不存在，则安装角色将创建 Active Directory 域，并且服务器将成为位于林和域的根的域控制器，并保留所有 FSMO 角色。
|只能部署到单个域中。|只能部署到单个域中。
|只读域控制器不能存在于域中。|只读域控制器不能存在于域中。

> [!NOTE]
>  若要下载评估版本的操作系统，请访问 TechNet 评估中心：
>
>  [下载 Windows Server 2016](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016)
>
>  [下载 Windows Server Essentials](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016-essentials)

## <a name="installation-options"></a>安装选项
 本文档提供有关安装和配置 Windows Server Essentials 的分步说明。 根据你的网络环境，可以向你提供以下安装选项：

-    默认情况下启用 windows Server Essentials 体验角色的 windows Server Essentials () 

-    安装了 Windows Server Essentials Experience 角色的 windows Server 2016

|部署环境|说明|相关部分|
|----------------------------|-----------------|---------------------|
|新的 Active Directory 环境|可以安装 Windows Server Essentials 来创建新的 Active Directory 环境。|[部署 Windows Server Essentials 来设置新的 Active Directory 环境](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_NewAD)|
|现有 Active Directory 环境|可以在现有 Active Directory 环境中安装 Windows Server Essentials。|[在现有 Active Directory 环境中部署 Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_ExistingAD)|
|虚拟环境|可以将 Windows Server Essentials 部署为虚拟机。|[虚拟化环境](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_VirtualWSE)|
|自动化部署|可以使用 Windows PowerShell 自动部署 Windows Server Essentials。|[使用 Windows PowerShell 安装和配置 Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_PowerShell)|

## <a name="before-you-begin"></a>在开始之前
 在开始安装之前，请查看以下文档：

-   [Windows Server Essentials 产品概述](https://www.microsoft.com/server-cloud/windows-server-essentials/windows-server-2012-r2-essentials.aspx)


-   [Windows Server Essentials 的系统要求](../get-started/system-requirements.md)


##  <a name="deploy-windows-server-essentials-to-set-up-a-new-active-directory-environment"></a><a name="BKMK_NewAD"></a> 部署 Windows Server Essentials 来设置新的 Active Directory 环境
 Windows Server Essentials 提供了一种方法，使你可以快速设置 Active Directory 环境和相关的服务器功能。

###  <a name="deploying-windows-server-essentials"></a><a name="BKMK_WSEDeploy"></a> 部署 Windows Server Essentials
 如果使用的是 Windows Server Essentials，则已启用 Windows Server Essentials Experience。 但是，必须完成一些步骤才能配置你的服务器。

##### <a name="to-configure-windows-server-essentials-on-a-physical-server"></a>在物理服务器上配置 Windows Server Essentials

1. 在 Windows“欢迎使用”**** 页之后，“配置 Windows Server Essentials 向导”**** 将在桌面上可见。

2. 按照说明完成向导，如下所示：

   1.  在“配置 Windows Server Essentials”**** 页上，单击“下一步”****。

   2.  在“时间设置”**** 中，确保日期、时间和时区均正确，然后单击“下一步”****。

   3.  在“公司信息”**** 中，键入公司名称（如 **Contoso,Ltd.**），然后单击“下一步”****。 （可选）可以更改内部域名和服务器名称。

   4.  在“创建网络管理员”**** 中，键入新的管理员帐户名称和密码。

       > [!NOTE]
       >  不要使用默认“管理员”**** 帐户名称和密码。

   5.  单击 **“配置”** 。

3. 服务器在配置过程中将多次重新启动，并且在完成配置前，将会自动进行登录。 此过程需要大约 20 分钟的时间。

4. 在桌面上，单击仪表板图标以启动服务器仪表板。 在“主页”**** 上，完成“安装”**** 选项卡上列出的“入门”**** 任务。

   完成服务器配置后，运行 Windows Server Essentials 的服务器将被设置为域控制器。

###  <a name="deploying-the-windows-server-essentials-experience-role-in-windows-server-2012-r2-standard-and-datacenter"></a><a name="BKMK_DeployWSERole"></a> 部署 windows server 2012 R2 Standard 和 Datacenter 中的 Windows Server Essentials 体验角色
 通过使用以下过程，你可以使用服务器管理器在 Windows Server 2012 R2 Standard 或 Windows Server 2012 R2 Datacenter 中启用并配置 Windows Server Essentials 体验角色。

##### <a name="to-deploy-the-windows-server-essentials-experience-role-in-windows-server-2012-r2"></a>部署 Windows Server 2012 R2 中的 Windows Server Essentials 体验角色

1.  以本地管理员身份登录到服务器。

2.  打开“服务器管理器”****，然后单击“添加角色和功能”****。

3.  在“选择服务器角色”**** 中，选择“Windows Server Essentials Experience”**** 角色。 在对话框中，单击“添加功能”****，然后单击“下一步”****。

4.  在“功能”**** 中，单击“下一步”****。

5.  查看“Windows Server Essentials Experience”**** 角色说明，然后单击“下一步”****。

6.  在后续页面中，单击“下一步”****，然后在配置页上，单击“安装”****。

7.  安装完成后，Windows Server Essentials Experience 应作为服务器角色在服务器管理器中列出。

8.  在服务器管理器中的标志通知区域内，单击标志，然后单击“配置 Windows Server Essentials”****。

9. （可选）更改服务器名称（如果需要）。

    > [!IMPORTANT]
    >  配置 Windows Server Essentials 之后，无法再更改服务器名称。


10. 按照向导配置 Windows Server Essentials，如之前在 [部署 Windows Server essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_WSEDeploy) 部分中所述。

10. 按照向导配置 Windows Server Essentials，如之前在 [部署 Windows Server essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_WSEDeploy) 部分中所述。


##  <a name="deploy-windows-server-essentials-in-an-existing-active-directory-environment"></a><a name="BKMK_ExistingAD"></a> 在现有 Active Directory 环境中部署 Windows Server Essentials
 如果组织已经具有现有 Active Directory 环境，也可以部署 Windows Server Essentials。 此外，可以选择是否要将 Windows Server Essentials 部署为域控制器。

> [!IMPORTANT]
>  仅当你在 Windows Server 2012 R2 Standard 或 Windows Server 2012 R2 Datacenter 中部署 Windows Server Essentials 体验角色时，此选项才可用。

#### <a name="to-deploy-windows-server-essentials-in-an-existing-active-directory-environment"></a>在现有 Active Directory 环境中部署 Windows Server Essentials

1.  （可选）更改服务器名称（如果需要）。

    > [!IMPORTANT]
    >  配置 Windows Server Essentials 之后，无法再更改服务器名称。

2.  将运行 Windows Server Essentials 的服务器加入到现有域中，如下所示：

    1.  如果希望将服务器成为域控制器，则将该服务器设置为副本域控制器。

    2.  如果不希望此服务器成为域控制器，则通过使用 Windows 本机工具将服务器加入域。

3.  重新启动服务器并以域管理员身份登录到服务器。

4.  打开服务器管理器，然后单击“添加角色和功能”****。

5.  在后续页面中，单击“下一步”****。

6.  在“选择服务器角色”**** 中，选择“Windows Server Essentials Experience”****。 在对话框中，单击“添加功能”****，然后单击“下一步”****。

7.  在“功能”**** 中，单击“下一步”****。

8.  查看“Windows Server Essentials Experience”**** 说明，然后单击“下一步”****。

9. 在后续页面中，单击“下一步”****，然后在配置页上，单击“安装”****。

10. 安装完成后，Windows Server Essentials 体验将作为服务器角色在服务器管理器中列出。

11. 在“服务器管理器”**** 中的标志通知区域内，单击标志，然后单击“配置 Windows Server Essentials”****。

12. 按照向导来配置 Windows Server Essentials。 根据 Active Directory 配置，将会通知你是否要将 Windows Server Essentials 配置在域控制器上或配置为域成员。 单击“配置”**** 以开始进行配置。 完成配置过程需要大约 10 分钟的时间。

##  <a name="virtualize-your-environment"></a><a name="BKMK_VirtualWSE"></a> 虚拟化环境
  Windows Server Essentials、Windows Server 2012 R2 Standard 和 Windows Server 2012 R2 Datacenter 可作为虚拟机运行。 可通过使用 Hyper-V 管理工具在运行 Hyper-V 的服务器上运行虚拟机。 从授权的角度来看，Windows Server Essentials 允许设置 Hyper-v 角色和虚拟化环境。 许可证允许你设置另一个运行 Windows Server Essentials 的来宾操作系统。 Windows Server Essentials 使你能够无缝地设置虚拟化环境，具体取决于系统提供程序的 "存储" 配置。

#### <a name="to-deploy-windows-server-essentials-as-a-virtual-machine"></a>将 Windows Server Essentials 部署为虚拟机

1.  在 "欢迎使用 Windows" 页后，根据您的系统提供程序 "存储配置)  (，" **开始之前** "页提供了一个选项，用于将 Windows Server Essentials 设置为虚拟实例或物理硬件。 这些选项的可用性由系统提供程序进行预定义，并且这两个选项可能不是始终都可用的。 若要将 Windows Server Essentials 安装为虚拟机，请在 " **安装 Windows Server essentials**" 中，选择 " **作为虚拟实例安装**"，然后单击 " **配置**"。

2.  该向导将自动设置虚拟机，大约需要五分钟。

3.  接下来，配置 Windows Server Essentials，如之前在 [部署 Windows Server essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_WSEDeploy) 部分中所述。


##  <a name="install-and-configure-windows-server-essentials-by-using-windows-powershell"></a><a name="BKMK_PowerShell"></a> 使用 Windows PowerShell 安装和配置 Windows Server Essentials
 可以使用 Windows PowerShell cmdlets 自动安装 Windows Server Essentials。

#### <a name="to-install-windows-server-essentials-by-using-windows-powershell"></a>使用 Windows PowerShell 安装 Windows Server Essentials

1.  从提升的命令提示符中打开 Windows PowerShell 控制台。

2.  使用以下命令安装 Windows Server Essentials 体验角色：

    ```
    Add-WindowsFeature ServerEssentialsRole
    ```

3.  运行 `Get-Help Start-WssConfigurationService`。

    1.  运行以下命令以启动配置，从而将 Windows Server Essentials 设置为域控制器：

        ```
        Start-WssConfigurationService -CompanyName "ContosoTest" -DNSName "ContosoTest.com" -NetBiosName "ContosoTest" -ComputerName "YourServerName  œNewAdminCredential $cred
        ```

    2.  运行以下命令以启动配置，从而将 Windows Server Essentials 设置为现有域成员。 你必须是 Active Directory 中的 Enterprise Admin 组和 Domain Admin 组的成员，才能执行此任务：

        ```
        Start-WssConfigurationService  œCredential <Your Credential>

        ```

4.  通过使用以下命令来监视安装进度：

    -   若要在进度栏上显示安装状态，请运行 `Get-WssConfigurationStatus  œShowProgress`。

    -   若要在没有进度栏的情况下获取即时进度，请运行 `Get-WssConfigurationStatus`。

## <a name="see-also"></a>请参阅

-   [Windows Server Essentials 中的新增功能](../get-started/what-s-new.md)

-   [安装 Windows Server Essentials](Install-Windows-Server-Essentials.md)

-   [Windows Server Essentials 入门](../get-started/get-started.md)
