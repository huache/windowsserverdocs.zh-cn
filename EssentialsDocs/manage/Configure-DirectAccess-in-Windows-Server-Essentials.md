---
title: 在 Windows Server Essentials 中配置 DirectAccess
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: c959b6fc-c67e-46cd-a9cb-cee71a42fa4c
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: a1f568d34fd0fbd94d09046b59a93d21feb60890
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181073"
---
# <a name="configure-directaccess-in-windows-server-essentials"></a>在 Windows Server Essentials 中配置 DirectAccess

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本主题提供有关在 Windows Server Essentials 中配置 DirectAccess 的分步说明，使移动工作人员可以从任何配备 Internet 的远程位置无缝连接到组织的网络，而不必建立虚拟专用网络（VPN）连接。 DirectAccess 可为移动工作人员提供与 Windows 8.1、Windows 8 和 Windows 7 计算机相同的相同连接体验。

 在 Windows Server Essentials 中，如果域包含多个 Windows Server Essentials 服务器，则必须在域控制器上配置 DirectAccess。

> [!NOTE]
>  本主题提供有关在 Windows Server Essentials 服务器是域控制器时配置 DirectAccess 的说明。 如果 Windows Server Essentials 服务器是域成员，请按照[将 Directaccess 添加到现有远程访问（VPN）部署](https://technet.microsoft.com/library/jj574220.aspx)中的域成员上的说明进行操作。

## <a name="process-overview"></a>过程概述
 若要在 Windows Server Essentials 中配置 DirectAccess，请完成以下步骤。

> [!IMPORTANT]
>  使用本指南中的过程在 Windows Server Essentials 中配置 DirectAccess 之前，必须在服务器上启用 VPN。 有关说明，请参阅[管理 VPN](Manage-VPN-in-Windows-Server-Essentials.md)。

-   [步骤 1：将远程访问管理工具添加到你的服务器](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddRAM)

-   [步骤 2：将该服务器的网络适配器地址更改为静态 IP 地址](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddStaticIP)

-   [步骤 3：准备网络位置服务器证书和 DNS 记录](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)

    -   [步骤3a：向经过身份验证的用户授予 Web 服务器的证书模板的完全权限](#BKMK_GrantFullPermissions)

    -   [步骤 3b：使用无法从外部网络解析的公用名来为网络位置服务器注册证书](#BKMK_EnrollaCertificate)

    -   [步骤3c：在 DNS 服务器上添加一个新主机，并将其映射到 Windows Server Essentials 服务器地址](#BKMK_MapNewHosttoServerAddress)

-   [步骤 4：创建 DirectAccess 客户端计算机的安全组](#BKMK_AddSecurityGroup)

-   [步骤 5：启用和配置 DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableConfigureDA)

    -   [步骤 5a：使用远程访问管理控制台启用 DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)

    -   [步骤5b：删除 RRAS GPO 中的无效 IPv6Prefix （仅适用于 Windows Server Essentials）](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)

    -   [步骤 5c：使运行 Windows 7 企业版的客户端计算机能够使用 DirectAccess](#BKMK_Step4cWindows7Setup)

    -   [步骤 5d：配置网络位置服务器](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)

    -   [步骤 5e：建立 IPsec 通道时，添加注册表项以避免使用 CA 证书](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)

-   [步骤 6：为 DirectAccess 服务器配置名称解析策略表设置](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NRPT)

-   [步骤 7：为 DirectAccess 服务器 GPO 配置 TCP 和 UDP 防火墙规则](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_TCPUDP)

-   [步骤 8：更改 DNS64 配置以侦听 IP-HTTPS 接口](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS64)

-   [步骤 9：保留 WinNat 服务的端口](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_ExemptPort)

-   [步骤 10：重新启动 WinNat 服务](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_WinNAT)

> [!NOTE]
>  [附录：使用 Windows PowerShell 设置 DirectAccess](#BKMK_AppendixBPowerShellScript) 提供了可用于执行 DirectAccess 安装的 Windows PowerShell 脚本。

##  <a name="step-1-add-remote-access-management-tools-to-your-server"></a><a name="BKMK_AddRAM"></a>步骤1：将远程访问管理工具添加到服务器

#### <a name="to-add-remote-accregss-management-tools--reg"></a>添加远程 Acc &reg; Ss 管理工具&reg;

1.  在服务器上，在“开始”页的左下角，单击“服务器管理器”**** 图标。

     在 Windows Server Essentials 中，你将需要搜索服务器管理器打开它。 在“开始”页上，键入 **Server Manager**，然后单击搜索结果中的“服务器管理器”****。 若要将服务器管理器固定到“开始”页，请右键单击搜索结果中的服务器管理器，并单击“固定到‘开始’屏幕”****。

2.  如果显示“用户帐户控制”**** 警告消息，请单击“是”****。

3.  在服务器管理器仪表板上，单击“管理”****，然后单击“添加角色和功能”****。

4.  在“添加角色和功能向导”中，执行以下操作：

    1.  在“安装类型”**** 页上，选择“基于角色或基于功能的安装”****。

    2.  在 "**服务器选择" 页**（或 Windows server Essentials 中的 "**选择目标服务器**" 页）上，单击 **"从服务器池中选择一个服务器"**。

    3.  在“功能”**** 页上，依次展开“远程服务器管理工具（已安装）”****、“远程访问管理工具（已安装）”****、“角色管理工具（已安装）”****、“远程访问管理工具”****，然后选择“远程访问 GUI 和命令行工具”****。

    4.  按照说明完成向导。

##  <a name="step-2-change-the-network-adapter-address-of-the-server-to-a-static-ip-address"></a><a name="BKMK_AddStaticIP"></a>步骤2：将服务器的网络适配器地址更改为静态 IP 地址
 DirectAccess 需要使用具有静态 IP 地址的适配器。 你需要更改服务器本地网络适配器的 IP 地址。

#### <a name="to-add-a-static-ip-address"></a>添加静态 IP 地址的步骤

1.  在“开始”页上，打开“控制面板”****。

2.  单击“网络和 Internet”****，然后单击“查看网络状态和任务”****。

3.  在“网络和共享中心”**** 的任务窗格中，单击“更改适配器设置”****。

4.  右键单击本地网络适配器，然后单击“属性”****。

5.  在“网络”**** 选项卡上，单击“Internet 协议版本 4 (TCP/IPv4)”****，然后单击“属性”****。

6.  在“常规”**** 选项卡上，单击“使用下面的 IP 地址”****，然后键入要使用的 IP 地址。

     子网掩码的默认值会自动显示在“子网掩码”**** 框中。 接受该默认值，或键入要使用的子网掩码值。

7.  在“默认网关”**** 框中，键入默认网关的 IP 地址。

8.  在“首选 DNS 服务器”**** 框中，键入 DNS 服务器的 IP 地址。

    > [!NOTE]
    >  使用 DHCP 分配给网络适配器的 IP 地址（例如 192.168.X.X），而非环回网络分配的 IP 地址（例如，127.0.0.1）。 若要查找分配的 IP 地址，请在命令提示符处运行 **ipconfig**。

9. 在“备用 DNS 服务器”**** 框中，键入备用 DNS 服务器的 IP 地址（如果有）。

10. 单击 **“确定”** ，再单击 **“关闭”** 。

> [!IMPORTANT]
>  确保配置路由器将端口 80 和 443 转发到服务器的新静态 IP 地址。

##  <a name="step-3-prepare-a-certificate-and-dns-record-for-the-network-location-server"></a><a name="BKMK_DNS"></a>步骤3：准备网络位置服务器的证书和 DNS 记录
 若要准备网络位置服务器的证书和 DNS 记录，请执行以下任务：

-   [步骤3a：向经过身份验证的用户授予 Web 服务器的证书模板的完全权限](#BKMK_GrantFullPermissions)

-   [步骤 3b：使用无法从外部网络解析的公用名来为网络位置服务器注册证书](#BKMK_EnrollaCertificate)

-   [步骤 3c：在 DNS 服务器上添加一个新主机，并将其映射到 Windows Server Essentials 服务器地址](#BKMK_MapNewHosttoServerAddress)

###  <a name="step-3a-grant-full-permissions-to-authenticated-users-for-the-web-servers-certificate-template"></a><a name="BKMK_GrantFullPermissions"></a>步骤3a：向经过身份验证的用户授予 Web 服务器的证书模板的完全权限
 你的第一项任务是在证书颁发机构中授予对 Web 服务器的证书模板的用户进行身份验证的完全权限。

####  <a name="to-grant-full-permissions-to-authenticated-users-for-the-web-servers-certificate-template"></a><a name="BKMK_ToGrantFullPermissions"></a>向经过身份验证的用户授予 Web 服务器的证书模板的完全权限

1.  在“开始”**** 页上，打开“证书颁发机构”****。

2.  在控制台树中的 "**证书颁发机构（Local）**" 下，展开 **<servername \> -CA**"，右键单击"**证书模板**"，然后单击"**管理**"。

3.  在“证书颁发机构（本地）”**** 中，右键单击“Web 服务器”****，然后单击“属性”****。

4.  在 Web 服务器属性中，在“安全”**** 选项卡上，单击“经身份验证的用户”****，选择“完全控制”****，然后单击“确定”****。

5.  重新启动“Active Directory 证书服务”****。 在控制面板中，打开“查看本地服务”****。 在服务列表中，右键单击“Active Directory 证书服务”****，然后单击“重新启动”****。

###  <a name="step-3b-enroll-a-certificate-for-the-network-location-server-with-a-common-name-that-is-unresolvable-from-the-external-network"></a><a name="BKMK_EnrollaCertificate"></a>步骤3b：使用无法从外部网络解析的公用名为网络位置服务器注册证书
 接下来，使用无法从外部网络解析的公用名来为网络位置服务器注册证书。

####  <a name="to-enroll-a-certificate-for-the-network-location-server"></a><a name="BKMK_ToEnrollaCertificate"></a>为网络位置服务器注册证书

1.  在“开始”**** 页上，打开“mmc”****（Microsoft 管理控制台）。

2.  如果出现“用户帐户控制”**** 警告消息，请单击“是”****。

     Microsoft 管理控制台 (MMC) 会打开。

3.  在“文件”**** 菜单上，单击“添加/删除管理单元”****。

4.  在“添加或远程管理单元”**** 框中，单击“证书”****，然后单击“添加”****。

5.  在“证书管理单元”**** 页上，单击“计算机帐户”****，然后单击“下一步”****。

6.  在“选择计算机”**** 页上，依次单击“本地计算机”****、“完成”**** 和“确定”****。

7.  在控制台树中，依次展开“证书（本地计算机）”****、“个人”****，右键单击“证书”****，然后在“所有任务”**** 中单击“请求新证书”****。

8.  当证书注册向导出现时，单击“下一步”****。

9. 在“选择证书注册策略”**** 页上，单击“下一步”****。

10. 在“请求证书”**** 页上，选中“Web 服务器”**** 复选框，然后单击“注册此证书需要更多信息”****。

11. 在“证书属性”**** 中，为“主题名称”**** 输入以下设置：

    1.  对于“类型”****，选择“公用名”****。

    2.  对于“值”****，键入该网络位置服务器的名称（例如，DirectAccess-NLS.contoso.local），然后单击“添加”****。

    3.  单击“确定”****，然后单击“注册”****。

12. 证书注册完成后，单击“完成”****。

###  <a name="step-3c-add-a-new-host-on-the-dns-server-and-map-it-to-the-windows-server-essentials-server-address"></a><a name="BKMK_MapNewHosttoServerAddress"></a>步骤3c：在 DNS 服务器上添加一个新主机，并将其映射到 Windows Server Essentials 服务器地址
 若要完成 DNS 配置，请在 DNS 服务器上添加一个新主机，并将其映射到 Windows Server Essentials 服务器地址。

####  <a name="to-map-a-new-host-to-the-windows-server-essentials-server-address"></a><a name="BKMK_ToMapNewHosttoServerAddress"></a>将新主机映射到 Windows Server Essentials 服务器地址

1.  在“开始”页上，打开 DNS 管理器。 若要打开 DNS 管理器，请搜索 **dnsmgmt.msc**，然后单击结果中的“dnsmgmt.msc” **** 。

2.  在 DNS 管理器控制台树中，展开本地服务器，展开 "**正向查找区域**"，右键单击带有服务器域后缀的区域，然后单击 "**新建主机（A 或 AAAA）**"。

3.  键入该服务器的名称和 IP 地址（例如，DirectAccess-NLS.contoso.local）及其对应的服务器地址（例如，192.168.x.x）。

4.  依次单击“添加主机”****、“确定”****，然后单击“完成”****。

##  <a name="step-4-create-a-security-group-for-directaccess-client-computers"></a><a name="BKMK_AddSecurityGroup"></a>步骤4：为 DirectAccess 客户端计算机创建安全组
 接下来，创建用于 DirectAccess 客户端计算机的安全组，然后将计算机帐户添加到该组。

#### <a name="to-add-a-security-group-for-client-computers-that-use-directaccess"></a>添加使用 DirectAccess 的客户端计算机的安全组的步骤

1. 在服务器管理器仪表板上，单击“工具”****，然后单击“Active Directory 用户和计算机”****。

   > [!NOTE]
   >  如果你未在“工具”**** 菜单上看到“Active Directory 用户和计算机”****，则必须安装该功能。 若要安装 Active Directory 用户和组，需要以管理员身份运行以下 Windows PowerShell cmdlet： `Install-WindowsFeature RSAT-ADDS-Tools`。 有关详细信息，请参阅 [安装或删除远程服务器管理工具程序包](https://technet.microsoft.com/library/cc730825.aspx)。

2. 在控制台树中，展开服务器，右键单击“用户”****，单击“新建”****，然后单击“组”****。

3. 输入组名称、组作用域和组类型（创建安全组），然后单击“确定”****。

   新安全组已添加到“用户”**** 文件夹。

#### <a name="to-add-computer-accounts-to-the-security-group"></a>将计算机帐户添加到安全组的步骤

1.  在服务器管理器仪表板上，单击“工具”****，然后单击“Active Directory 用户和计算机”****。

2.  在控制台树中，展开服务器，然后单击“用户”****。

3.  在服务器上的用户帐户和安全组列表中，右键单击为 DirectAccess 创建的安全组，然后单击“属性”****。

4.  在“成员”**** 选项卡上，单击“添加”****。

5.  在对话框中，键入要添加到该组的计算机帐户的名称，并用分号 (;) 分隔这些名称。 然后单击“检查名称”****。

6.  在验证计算机帐户后，单击 **“确定”**。 然后再次单击“确定”****。

> [!NOTE]
>  你还可以使用计算机帐户属性中的“成员所属的组”**** 选项卡将帐户添加到安全组。

##  <a name="step-5-enable-and-configure-directaccess"></a><a name="BKMK_EnableConfigureDA"></a>步骤5：启用和配置 DirectAccess
 若要在 Windows Server Essentials 中启用和配置 DirectAccess，必须完成以下步骤：

-   [步骤 5a：使用远程访问管理控制台启用 DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)

-   [步骤5b：删除 RRAS GPO 中的无效 IPv6Prefix （仅适用于 Windows Server Essentials）](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)

-   [步骤 5c：使运行 Windows 7 企业版的客户端计算机能够使用 DirectAccess](#BKMK_Step4cWindows7Setup)

-   [步骤 5d：配置网络位置服务器](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)

-   [步骤 5e：建立 IPsec 通道时，添加注册表项以避免使用 CA 证书](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)

###  <a name="step-5a-enable-directaccess-by-using-the-remote-access-management-console"></a><a name="BKMK_EnableDA"></a>步骤5a：通过使用远程访问管理控制台启用 DirectAccess
 本部分提供在 Windows Server Essentials 中启用 DirectAccess 的分步说明。 如果你尚未在服务器上配置 VPN，则应该在开始此过程之前执行该操作。 有关说明，请参阅[管理 VPN](Manage-VPN-in-Windows-Server-Essentials.md)。

##### <a name="to-enable-directaccess-by-using-the-remote-access-management-console"></a>使用远程访问管理控制台启用 DirectAccess 的步骤

1.  在“开始”页上，打开“远程访问管理”****。

2.  在启用 DirectAccess 向导中，执行以下操作：

    1.  查看“DirectAccess 先决条件”****，然后单击“下一步”****。

    2.  在“选择组”**** 选项卡上，添加你以前为 DirectAccess 客户端创建的安全组。 （如果尚未创建安全组，请参阅[步骤4：为 DirectAccess 客户端计算机创建安全组](#BKMK_AddSecurityGroup)以获取说明。）

    3.  如果要让移动计算机使用 DirectAccess 远程访问该服务器，请在“选择组”**** 选项卡上，单击“仅为移动计算机启用 DirectAccess”****，然后单击“下一步”****。

    4.  在“网络拓扑”**** 中，选择服务器拓扑，然后单击“下一步”****。

    5.  在“DNS 后缀搜索列表”**** 中，额外添加客户端计算机的 DNS 后缀（如果需要），然后单击“下一步”****。

        > [!NOTE]
        >  默认情况下，启用 DirectAccess 向导已经向当前的域名中添加了 DNS 后缀。 不过，你可以添加更多信息（如果需要）。

    6.  查看将要应用的组策略对象 (GPO) 并对它们进行修改（如果需要）。

    7.  单击“下一步”  ，然后单击“完成”  。

    8.  通过在提升模式下运行以下 Windows PowerShell 命令，重新启动远程访问管理服务：

        ```powershell
        Restart-Service RaMgmtSvc
        ```

###  <a name="step-5b-remove-the-invalid-ipv6prefix-in-rras-gpo-windows-server-essentials-only"></a><a name="BKMK_RemoveIPv6"></a>步骤5b：删除 RRAS GPO 中的无效 IPv6Prefix （仅适用于 Windows Server Essentials）
  本节适用于运行 Windows Server Essentials 的服务器。

 以管理员身份打开 Windows PowerShell，并运行下列命令：

```powershell
gpupdate
$key = Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\RemoteAccess\config\MachineSIDs | Where-Object{$_.GetValue("IPv6RrasPrefix") -ne $null}
Remove-GPRegistryValue -Name "DirectAccess Server Settings" -Key $key.Name -ValueName IPv6RrasPrefix
gpupdate
```

###  <a name="step-5c-enable-client-computers-running-windows-7-enterprise-to-use-directaccess"></a><a name="BKMK_Step4cWindows7Setup"></a>步骤5c：使运行 Windows 7 企业版的客户端计算机能够使用 DirectAccess
 如果客户端计算机运行的是 Windows 7 企业版，请完成以下过程以从这些计算机启用 DirectAccess。

##### <a name="to-enable--windows-7-enterprise-computers-to-use-directaccess"></a>使 Windows 7 企业计算机能够使用 DirectAccess

1.  在服务器的 "开始" 页上，打开 "**远程访问管理**"。

2.  在远程访问管理控制台中，单击“配置”****。 然后在“设置详细信息”**** 窗格中的“步骤 2”**** 下，单击“编辑”****。

     远程访问服务器设置向导将打开。

3.  在 "**身份验证**" 选项卡上，选择将成为受信任根证书的证书颁发机构（ca）证书（可以选择 Windows Server Essentials 服务器的 CA 证书）。 单击“使 Windows 7 客户端计算机能够通过 DirectAccess 进行连接”****，然后单击“下一步”****。

4.  按照说明完成向导。

> [!IMPORTANT]
>  如果 Windows Server Essentials 服务器未附带预安装的 UR1，则通过 DirectAccess 连接的 Windows 7 企业计算机存在一个已知问题。 若要在该环境中启用 DirectAccess 连接，必须执行以下附加步骤：
>
> 1. 在 Windows Server Essentials 服务器上安装[Microsoft 知识库（KB）文章 2796394](https://support.microsoft.com/kb/2796394)中所述的修补程序。 然后重新启动该服务器。
>    2. 然后在每个 Windows 7 计算机上安装[Microsoft 知识库（KB）文章 2615847](https://support.microsoft.com/kb/2615847)中所述的修补程序。
>
>    此问题已在 Windows Server Essentials 中解决。

###  <a name="step-5d-configure-the-network-location-server"></a><a name="BKMK_NLS"></a>步骤5d：配置网络位置服务器
 本节提供配置网络位置服务器设置的分步操作说明。

> [!NOTE]
>  开始之前，请将 <SystemDrive \inetpub\wwwroot 文件夹的内容复制 \> 到 <SystemDrive \> \Program Files\Windows Server\Bin\WebApps\Site\insideoutside 文件夹中。 同时将 <SystemDrive \Program Files\Windows Server\Bin\WebApps\Site 文件夹中的 default.aspx 文件复制 \> 到 <SystemDrive \Program Files\Windows Server\Bin\WebApps\Site\insideoutside \> 文件夹中。

##### <a name="to-configure-the-network-location-server"></a>要配置网络位置服务器，请执行以下操作：

1.  在“开始”页上，打开“远程访问管理”****。

2.  在“远程访问管理”控制台中，单击“配置”****，然后在“远程访问设置”**** 详细信息窗格的“步骤 3”**** 中，单击“编辑”****。

3.  在远程访问服务器设置向导的“网络位置服务器” **** 选项卡上，选择“在远程访问服务器上部署网络位置服务器” ****，然后选择之前颁发的证书（在 [Step 3: Prepare a certificate and DNS record for the network location server](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)中）。

4.  按照说明完成向导，然后单击“完成”****。

###  <a name="step-5e-add-a-registry-key-to-bypass-ca-certification-when-you-establish-an-ipsec-channel"></a><a name="BKMK_CA"></a>步骤5e：建立 IPsec 通道时，添加注册表项以避免使用 CA 证书
 下一步是将该服务器配置为在建立 IPsec 通道时避免使用 CA 证书。

##### <a name="to-add-a-registry-key-to-bypass-the-ca-certification"></a>添加注册表项以避免使用 CA 证书的步骤

1.  在“开始”页上，打开“regedit”****（注册表编辑器）。

2.  在注册表编辑器中，依次展开“HKEY_LOCAL_MACHINE”****、“System”****、“CurrentControlSet”****、“Services”**** 和“IKEEXT”****。

3.  在“IKEEXT”**** 下，右键单击“参数”****，单击“新建”****，然后单击“DWORD(32 位)值”****。

4.  将新添加的值重命名为 **ikeflags**。

5.  双击“ikeflags”****，将“类型”**** 设置为“十六进制”****，将值设置为 **8000**，然后单击“确定”****。

> [!NOTE]
>  可以在提升模式下使用以下 Windows PowerShell 命令以添加此注册表项：
>
>  `Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\IKEEXT\Parameters -Name ikeflags -Type DWORD -Value 0x8000`

##  <a name="step-6-configure-name-resolution-policy-table-settings-for-the-directaccess-server"></a><a name="BKMK_NRPT"></a>步骤6：为 DirectAccess 服务器配置名称解析策略表设置
 本节提供以下相关说明：编辑 DirectAccess 客户端 GPO 内部地址（例如，带有 contoso.local 后缀的项）名称解析策略表 (NPRT) 项，然后设置 IPHTTPS 接口地址。

#### <a name="to-configure-name-resolution-policy-table-entries"></a>配置名称解析策略表项的步骤

1.  在“开始”页上，打开“组策略管理”****。

2.  在组策略管理控制台中，单击默认的林和域，右键单击“DirectAccess 客户端设置”****，然后单击“编辑”****。

3.  依次单击“计算机配置”****、“策略”****、“Windows 设置”**** 和“名称解析策略”****。 选择命名空间与你的 DNS 后缀相同的条目，然后单击“编辑规则”****。

4.  单击“DirectAccess 的 DNS 设置”**** 选项卡，然后选择“启用此规则中 DirectAccess 的 DNS 设置”****。 在 DNS 服务器列表中添加 IP-HTTPS 接口的 IPv6 地址。

    > [!NOTE]
    >  可以使用以下 Windows PowerShell 命令获取 IPv6 地址：
    >
    >  `(Get-NetIPInterface -InterfaceAlias IPHTTPSInterface | Get-NetIPAddress -PrefixLength 128)[1].IPAddress`

##  <a name="step-7-configure-tcp-and-udp-firewall-rules-for-the-directaccess-server-gpos"></a><a name="BKMK_TCPUDP"></a>步骤7：为 DirectAccess 服务器 Gpo 配置 TCP 和 UDP 防火墙规则
 本节包含为 DirectAccess 服务器 GPO 配置 TCP 和 UDP 防火墙规则的分步操作说明。

#### <a name="to-configure-firewall-rules"></a>配置防火墙规则的步骤

1.  在“开始”页上，打开“组策略管理”****。

2.  在组策略管理控制台中，单击默认的林和域，右键单击“DirectAccess 客户端设置”****，然后单击“编辑”****。

3.  依次单击“计算机配置”****、“策略”****、“Windows 设置”****、“安全设置”****、“高级安全 Windows 防火墙”****、下一级的“高级安全 Windows 防火墙”**** 和“入站规则”****。 右键单击“域名服务器(TCP-In)”****，然后单击“属性”****。

4.  单击“作用域”**** 选项卡，然后在“本地 IP 地址”**** 列表中，添加 IP-HTTPS 接口的 IPv6 地址。

5.  针对“域名服务器(UDP-In)”**** 重复同样的过程。

##  <a name="step-8-change-the-dns64-configuration-to-listen-to-the-ip-https-interface"></a><a name="BKMK_DNS64"></a>步骤8：更改 DNS64 配置以侦听 IP-HTTPS 接口
 必须更改 DNS64 配置，以便使用以下 Windows PowerShell 命令侦听 IP-HTTPS 接口。

```powershell
Set-NetDnsTransitionConfiguration -AcceptInterface IPHTTPSInterface
```

##  <a name="step-9-reserve-ports-for-the-winnat-service"></a><a name="BKMK_ExemptPort"></a>步骤9：保留 WinNat 服务的端口
 使用以下 Windows PowerShell 命令保留 WinNat 服务的端口。 请将 "192.168.1.100" 替换为 Windows Server Essentials 服务器的实际 IPv4 地址。

```powershell
Set-NetNatTransitionConfiguration -IPv4AddressPortPool @("192.168.1.100, 10000-47000")
```

> [!IMPORTANT]
>  若要避免与应用程序的端口冲突，请确保你为 WinNat 服务保留的端口范围不包括端口 6602。

##  <a name="step-10-restart-the-winnat-service"></a><a name="BKMK_WinNAT"></a>步骤10：重新启动 WinNat 服务
 通过运行以下 Windows PowerShell 命令重新启动 Windows NAT 驱动程序 (WinNat) 服务。

```powershell
Restart-Service winnat
```

##  <a name="appendix-set-up-directaccess-by-using-windows-powershell"></a><a name="BKMK_AppendixBPowerShellScript"></a>附录：使用 Windows PowerShell 设置 DirectAccess
 本节介绍如何使用 Windows PowerShell 设置和配置 DirectAccess。

### <a name="preparation"></a>准备
 在开始为 DirectAccess 配置服务器之前，必须完成以下操作：

1.  按照[步骤3：为网络位置服务器准备证书和 DNS 记录](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)中的过程注册一个名为 " **DirectAccess-NLS.contoso.com** " 的证书（其中**contoso.com**替换为实际的内部域名），并为网络位置服务器（NLS）添加 DNS 记录。

2.  在 Active Directory 中添加名为“DirectAccessClients”的安全组****，然后添加要提供 DirectAccess 功能的客户端计算机。 有关详细信息，请参阅[步骤4：为 DirectAccess 客户端计算机创建安全组](#BKMK_AddSecurityGroup)。

### <a name="commands"></a>命令

> [!IMPORTANT]
>  在 Windows Server Essentials 中，无需删除不必要的 IPv6 前缀 GPO。 删除具有下列标签的代码段： `# [WINDOWS SERVER 2012 ESSENTIALS ONLY] Remove the unnecessary IPv6 prefix GPO`。

```powershell
# Add Remote Access role if not installed yet
$ra = Get-WindowsFeature RemoteAccess
If ($ra.Installed -eq $FALSE) { Add-WindowsFeature RemoteAccess }

# Server may need to restart if you installed RemoteAccess role in the above step

# Set the internet domain name to access server, replace contoso.com below with your own domain name
$InternetDomain = "www.contoso.com"
#Set the SG name which you create for DA clients
$DaSecurityGroup = "DirectAccessClients"
#Set the internal domain name
$InternalDomain = [System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain().Name

# Set static IP and DNS settings
$NetConfig = Get-WmiObject Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true"
$CurrentIP = $NetConfig.IPAddress[0]
$SubnetMask = $NetConfig.IPSubnet | Where-Object{$_ -like "*.*.*.*"}
$NetConfig.EnableStatic($CurrentIP, $SubnetMask)
$NetConfig.SetGateways($NetConfig.DefaultIPGateway)
$NetConfig.SetDNSServerSearchOrder($CurrentIP)

# Get physical adapter name and the certificate for NLS server
$Adapter = (Get-WmiObject -Class Win32_NetworkAdapter -Filter "NetEnabled=$true").NetConnectionId
$Certs = dir cert:\LocalMachine\My
$nlscert = $certs | Where-Object{$_.Subject -like "*CN=DirectAccess-NLS*"}

# Add regkey to bypass CA cert for IPsec authentication
Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\IKEEXT\Parameters -Name ikeflags -Type DWORD -Value 0x8000

# Install DirectAccess.
Install-RemoteAccess -NoPrerequisite -DAInstallType FullInstall -InternetInterface $Adapter -InternalInterface $Adapter -ConnectToAddress $InternetDomain -nlscertificate $nlscert -force

#Restart Remote Access Management service
Restart-Service RaMgmtSvc

# [WINDOWS SERVER 2012 ESSENTIALS ONLY] Remove the unnecessary IPv6 prefix GPO

gpupdate
$key = Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\RemoteAccess\config\MachineSIDs | Where-Object{$_.GetValue("IPv6RrasPrefix") -ne $null}
Remove-GPRegistryValue -Name "DirectAccess Server Settings" -Key $key.Name -ValueName IPv6RrasPrefix
gpupdate

# Enable client computers running Windows 7 to use DirectAccess
$allcertsinroot = dir cert:\LocalMachine\root
$rootcert = $allcertsinroot | Where-Object{$_.Subject -like "*-CAA*"}
Set-DAServer -IPSecRootCertificate $rootcert[0]
Set -DAClient -OnlyRemoteComputers Disabled -Downlevel Enabled

#Set the appropriate security group used for DA client computers. Replace the group name below with the one you created for DA clients
Add-DAClient -SecurityGroupNameList $DaSecurityGroup
Remove-DAClient -SecurityGroupNameList "Domain Computers"

# Gather DNS64 IP address information
$Remoteaccess = get-remoteaccess
$IPinterface = get-netipinterface -InterfaceAlias IPHTTPSInterface | get-netipaddress -PrefixLength 128
$DNS64IP=$IPInterface[1].IPaddress
$Natconfig = Get-NetNatTransitionConfiguration

# Configure TCP and UDP firewall rules for the DirectAccess server GPO
$GpoName = 'GPO:'+$InternalDomain+'\DirectAccess Server Settings'
Get-NetFirewallRule -PolicyStore $GpoName -Displayname "Domain Name Server (TCP-IN)"|Get-NetFirewallAddressFilter | Set-NetFirewallAddressFilter -LocalAddress $DNS64IP
Get-NetFirewallrule -PolicyStore $GpoName -Displayname "Domain Name Server (UDP-IN)"|Get-NetFirewallAddressFilter | Set-NetFirewallAddressFilter -LocalAddress $DNS64IP

# Configure the name resolution policy settings for the DirectAccess server, replace the DNS suffix below with the one in your domain
$Suffix = '.' + $InternalDomain
set-daclientdnsconfiguration -DNSsuffix $Suffix -DNSIPAddress $DNS64IP

# Change the DNS64 configuration to listen to IP-HTTPS interface
Set-NetDnsTransitionConfiguration -AcceptInterface IPHTTPSInterface

# Copy the necessary files to NLS site folder
XCOPY 'C:\inetpub\wwwroot' 'C:\Program Files\Windows Server\Bin\WebApps\Site\insideoutside' /E /Y
XCOPY 'C:\Program Files\Windows Server\Bin\WebApps\Site\Default.aspx' 'C:\Program Files\Windows Server\Bin\WebApps\Site\insideoutside' /Y

# Reserve ports for the WinNat service
Set-NetNatTransitionConfiguration -IPv4AddressPortPool @("192.168.1.100, 10000-47000")

# Restart the WinNat service
Restart-Service winnat
```

## <a name="additional-references"></a>其他参考

-   [管理随处访问](Manage-Anywhere-Access-in-Windows-Server-Essentials.md)

-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)
