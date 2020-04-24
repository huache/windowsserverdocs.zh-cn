---
title: 配置用户访问控制和权限
description: 了解如何使用 Active Directory 或 Azure AD (Project Honolulu) 配置用户访问控制和权限
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 06/07/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 39af45506ff7023cebe437992e90f6d4ec051333
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "79323589"
---
# <a name="configure-user-access-control-and-permissions"></a>配置用户访问控制和权限

> 适用于：Windows Admin Center、Windows Admin Center 预览版

请自行熟悉 [Windows Admin Center 中的用户访问控制选项](../plan/user-access-options.md)（如果还不熟悉的话）

> [!NOTE]
> 在 Windows Admin Center 中进行基于组的访问这一功能在工作组环境或不受信任的域中不受支持。

## <a name="gateway-access-role-definitions"></a>网关访问角色定义

可以通过两个角色来访问 Windows Admin Center 网关服务：

**网关用户**可以连接到 Windows Admin Center 网关服务，以便通过该网关管理服务器，但他们不能更改访问权限，也不能更改身份验证机制（用于向网关进行身份验证）。

**网关管理员**可以对谁获得访问权限以及用户如何向网关进行身份验证进行配置。 仅网关管理员可以在 Windows Admin Center 中查看和配置“访问设置”。 网关计算机上的本地管理员始终是 Windows Admin Center 网关服务的管理员。

> [!NOTE]
> 可以访问网关并不意味着可以访问对网关可见的托管服务器。 若要管理目标服务器，连接用户必须使用可以对该目标服务器进行管理性访问的凭据（不管是使用传递型 Windows 凭据，还是使用通过“管理身份”操作在 Windows Admin Center 会话中提供的凭据  ）。

## <a name="active-directory-or-local-machine-groups"></a>Active Directory 或本地计算机组

默认情况下，Active Directory 或本地计算机组用于控制网关访问。 如果有 Active Directory 域，则可在 Windows Admin Center 界面中管理网关用户和管理员的访问。

在“用户”选项卡上，可以控制谁可以作为网关用户访问 Windows Admin Center。  默认情况下，如果不指定安全组，则任何能够访问网关 URL 的用户都可以进行访问。 向用户列表添加一个或多个安全组以后，仅限这些组的成员进行访问。

如果不使用环境中的 Active Directory 域，则由 Windows Admin Center 网关计算机上的 `Users` 和 `Administrators` 本地组控制访问权限。

### <a name="smartcard-authentication"></a>智能卡身份验证

可以强制实施**智能卡身份验证**，方法是：为基于智能卡的安全组指定另一个必需的组。  在你添加基于智能卡的安全组以后，用户访问 Windows Admin Center 服务的前提是：他/她必须是安全组的成员且用户列表中必须包含一个智能卡组。

在“管理员”选项卡上，可以控制谁可以作为网关管理员访问 Windows Admin Center。  计算机上的本地管理员组将始终拥有完全的管理员访问权限，不能将该组从列表中删除。 添加安全组后，这些组的成员就会获得更改 Windows Admin Center 网关设置的特权。 管理员列表支持智能卡身份验证的方式与用户列表一样：采用安全组和智能卡组的 AND 条件。

## <a name="azure-active-directory"></a>Azure Active Directory

如果你的组织使用 Azure Active Directory (Azure AD)，你可以选择要求通过 Azure AD 身份验证来访问网关，向 Windows Admin Center 添加**额外的**安全层。 若要访问 Windows Admin Center，用户的 **Windows 帐户**必须也能够访问网关服务器（即使使用 Azure AD 身份验证）。 使用 Azure AD 时，将通过 Azure 门户而不是 Windows Admin Center UI 管理 Windows Admin Center 用户和管理员访问权限。

### <a name="accessing-windows-admin-center-when-azure-ad-authentication-is-enabled"></a>在启用 Azure AD 身份验证的情况下访问 Windows Admin Center

根据所用浏览器的不同，某些用户在配置 Azure AD 身份验证的情况下访问 Windows Admin Center 时，会**从浏览器**收到一个额外的提示，他们需在浏览器中针对安装了 Windows Admin Center 的计算机提供自己的 Windows 帐户凭据。 输入该信息以后，用户会收到这个额外的 Azure Active Directory 身份验证提示，该提示要求用户提供已在 Azure 的 Azure AD 应用程序中获得访问权限的 Azure 帐户的凭据。

> [!NOTE]
> 如果用户的 Windows 帐户已在网关计算机上获得**管理员权限**，系统不会提示其进行 Azure AD 身份验证。

### <a name="configuring-azure-active-directory-authentication-for-windows-admin-center-preview"></a>针对 Windows Admin Center 预览版配置 Azure Active Directory 身份验证

请转到 Windows Admin Center 的“设置”   >   “访问权限”，通过切换开关启用“使用 Azure Active Directory 向网关添加安全层”功能。 如果尚未将网关注册到 Azure，系统此时会引导你那样做。

默认情况下，Azure AD 租户的所有成员都有 Windows Admin Center 网关服务的用户访问权限。 仅网关计算机上的本地管理员具有 Windows Admin Center 网关的管理员访问权限。 请注意，网关计算机上本地管理员的权限不受限制 - 本地管理员可以执行任何操作，与是否使用 Azure AD 进行身份验证无关。

若要为特定 Azure AD 用户或组网关用户或网关管理员提供 Windows Admin Center 服务的访问权限，必须执行以下操作：

1.  使用“访问设置”中提供的超链接转到 Azure 门户中的 Windows Admin Center Azure AD 应用程序。 请注意，该超链接仅在启用 Azure Active Directory 身份验证的情况下可用。 
    -   也可在 Azure 门户中找到应用程序，方法是：转到“Azure Active Directory”   > “企业应用程序”   >   “所有应用程序”，搜索 **WindowsAdminCenter**（Azure AD 应用将以 WindowsAdminCenter-<gateway name> 命名）。 如果没有获得任何搜索结果，请确保将“显示”设置为“所有应用程序”，将“应用程序状态”设置为“任意”并单击“应用”，然后尝试搜索。     找到应用程序以后，请转到“用户和组” 
2.  在“属性”选项卡中，将“需要用户分配”设置为“是”。 
    这样做以后，将只有“用户和组”选项卡中列出的成员能够访问 Windows Admin Center 网关。 
3.  在“用户和组”选项卡中，选择“添加用户”  。 必须为每个添加的用户/组分配网关用户或网关管理员角色。

启用 Azure AD 身份验证以后，网关服务会重启，你必须刷新浏览器。 可以随时在 Azure 门户中更新 SME Azure AD 应用程序的用户访问权限。

当用户尝试访问 Windows Admin Center 网关 URL 时，系统会提示其使用 Azure Active Directory 标识登录。 请记住，用户还必须是网关服务器上“本地用户”的成员才能访问 Windows Admin Center。

用户和管理员可以在 Windows Admin Center 设置的“帐户”选项卡中查看当前登录的帐户以及注销该 Azure AD 帐户。 

### <a name="configuring-azure-active-directory-authentication-for-windows-admin-center"></a>针对 Windows Admin Center 配置 Azure Active Directory 身份验证

[若要设置 Azure AD 身份验证，必须先将网关注册到 Azure](azure-integration.md)（对于 Windows Admin Center 网关，只需这样做一次）。 此步骤创建一个 Azure AD 应用程序，可以在其中管理网关用户和网关管理员的访问。

若要为特定 Azure AD 用户或组网关用户或网关管理员提供 Windows Admin Center 服务的访问权限，必须执行以下操作：

1.  转到 Azure 门户中的 SME Azure AD 应用程序。 
    -   在 Windows Admin Center 的“访问设置”中单击“更改访问控制”并选择“Azure Active Directory”时，可以使用 UI 中提供的超链接来访问 Azure 门户中的 Azure AD 应用程序。   在单击“保存”并选择 Azure AD 作为访问控制标识提供程序之后，此超链接也在“访问设置”中提供。
    -   也可在 Azure 门户中找到应用程序，方法是：转到“Azure Active Directory”   > “企业应用程序”   >   “所有应用程序”，搜索 **SME**（Azure AD 应用将以 SME-<gateway> 命名）。 如果没有获得任何搜索结果，请确保将“显示”设置为“所有应用程序”，将“应用程序状态”设置为“任意”并单击“应用”，然后尝试搜索。     找到应用程序以后，请转到“用户和组” 
2.  在“属性”选项卡中，将“需要用户分配”设置为“是”。 
    这样做以后，将只有“用户和组”选项卡中列出的成员能够访问 Windows Admin Center 网关。 
3.  在“用户和组”选项卡中，选择“添加用户”  。 必须为每个添加的用户/组分配网关用户或网关管理员角色。

在“更改访问控制”窗格中保存 Azure AD 访问控制以后，网关服务会重启，你必须刷新浏览器。  可以随时在 Azure 门户中更新 Windows Admin Center Azure AD 应用程序的用户访问权限。 

当用户尝试访问 Windows Admin Center 网关 URL 时，系统会提示其使用 Azure Active Directory 标识登录。 请记住，用户还必须是网关服务器上“本地用户”的成员才能访问 Windows Admin Center。 

使用 Windows Admin Center 常规设置的“Azure”选项卡，用户和管理员可以查看当前登录的帐户以及注销该 Azure AD 帐户。 

### <a name="conditional-access-and-multi-factor-authentication"></a>条件访问和多重身份验证

使用 Azure AD 作为额外的安全层来控制 Windows Admin Center 网关访问权限的好处之一是：你可以利用 Azure AD 的强大安全功能，如条件访问和多重身份验证。 

[详细了解如何使用 Azure Active Directory 配置条件访问。](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)

## <a name="configure-single-sign-on"></a>配置单一登录

**在部署为 Windows Server 上的服务的情况下进行的单一登录**

在 Windows 10 上安装 Windows Admin Center 后，即可使用单一登录。 但是，若要在 Windows Server 上使用 Windows Admin Center，需在环境中设置某种形式的 Kerberos 委托，然后才能使用单一登录。 该委托会将网关计算机配置为值得信任，可以委托到目标节点。 

若要在环境中配置[基于资源的受约束委托](https://docs.microsoft.com/windows-server/security/kerberos/kerberos-constrained-delegation-overview)，请使用以下 PowerShell 示例。 此示例演示如何将 Windows Server [node01.contoso.com] 配置为接受来自 contoso.com 域中 Windows Admin Center 网关 [wac.contoso.com] 的委托。

```powershell
Set-ADComputer -Identity (Get-ADComputer node01) -PrincipalsAllowedToDelegateToAccount (Get-ADComputer wac)
```

若要删除此关系，请运行以下 cmdlet：

```powershell
Set-ADComputer -Identity (Get-ADComputer node01) -PrincipalsAllowedToDelegateToAccount $null
```

## <a name="role-based-access-control"></a>基于角色的访问控制

使用基于角色的访问控制，可以为用户提供对计算机的有限访问权限，而不是将其设置为具有完全权限的本地管理员。
[详细阅读基于角色的访问控制和可用角色。](../plan/user-access-options.md#role-based-access-control)

设置 RBAC 包含 2 个步骤：一是在目标计算机上启用支持，二是为用户分配相关角色。

> [!TIP]
> 在计算机上配置对基于角色的访问控制的支持时，请确保你在计算机上具有本地管理员特权。

### <a name="apply-role-based-access-control-to-a-single-machine"></a>对单台计算机应用基于角色的访问控制

单计算机部署模型适用于只需管理数台计算机的简单环境。
为计算机配置对基于角色的访问控制的支持会导致以下变化：

-   会在系统驱动器的 `C:\Program Files\WindowsPowerShell\Modules` 下安装具有 Windows Admin Center 所需功能的 PowerShell 模块。 所有模块都会以 **Microsoft.Sme** 开头
-   Desired State Configuration 会运行一项一次性的配置，用于在计算机上配置名为 **Microsoft.Sme.PowerShell** 的 Just Enough Administration 终结点。 此终结点定义 Windows Admin Center 使用的 3 个角色，并且会在用户连接到它时以临时本地管理员身份运行。
-   将会创建 3 个新的本地组，用于控制向哪些用户分配访问哪些角色的权限：
    -   Windows Admin Center 管理员
    -   Windows Admin Center Hyper-V 管理员
    -   Windows Admin Center 读者

若要在单台计算机上启用对基于角色的访问控制的支持，请执行以下步骤：

1.  打开 Windows Admin Center，使用在目标计算机上具有本地管理员特权的帐户连接到要为其配置基于角色的访问控制的计算机。
2.  在“概览”工具中，  单击“设置”   >   “基于角色的访问控制”。
3.  单击页面底部的“应用”，在目标计算机上启用对基于角色的访问控制的支持。  应用过程涉及在目标计算机上复制 PowerShell 脚本和调用一项配置（使用 PowerShell Desired State Configuration）。 此过程可能需要长达 10 分钟的时间才能完成，并且会导致 WinRM 重启。 这会临时断开 Windows Admin Center 用户、PowerShell 用户和 WMI 用户的连接。
4.  刷新页面，检查基于角色的访问控制的状态。 可以使用时，状态会变为“已应用”。 

应用配置以后，即可为用户分配角色：

1.  打开“本地用户和组”工具，导航到“组”选项卡。  
2.  选择“Windows Admin Center 读者”组。 
3.  在底部的“详细信息”窗格中，单击“添加用户”，然后输入应该通过 Windows Admin Center 对服务器进行只读访问的用户或安全组的名称。   用户和组可以来自本地计算机，也可以来自 Active Directory 域。
4.  对“Windows Admin Center Hyper-V 管理员”组和“Windows Admin Center 管理员”组重复步骤 2-3。  

也可在整个域中一致地填充这些组，方法是：为组策略对象配置[受限组策略设置](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc756802%28v=ws.10%29)。

### <a name="apply-role-based-access-control-to-multiple-machines"></a>对多台计算机应用基于角色的访问控制

在大企业部署中，可以使用现有的自动化工具将基于角色的访问控制功能推送到计算机，只需从 Windows Admin Center 网关下载配置包即可。
配置包按设计应与 PowerShell Desired State Configuration 配合使用，但可以对它进行调整，使之适用于首选的自动化解决方案。

#### <a name="download-the-role-based-access-control-configuration"></a>下载基于角色的访问控制配置

若要下载基于角色的访问控制配置包，需要有权访问 Windows Admin Center 和 PowerShell 提示符。

如果在 Windows Server 上以服务模式运行 Windows Admin Center 网关，请使用以下命令下载配置包。
请务必将网关地址更新为对环境来说正确的地址。

```powershell
$WindowsAdminCenterGateway = 'https://windowsadmincenter.contoso.com'
Invoke-RestMethod -Uri "$WindowsAdminCenterGateway/api/nodes/all/features/jea/endpoint/export" -Method POST -UseDefaultCredentials -OutFile "~\Desktop\WindowsAdminCenter_RBAC.zip"
```

如果在 Windows 10 计算机上运行 Windows Admin Center 网关，请改为运行以下命令：

```powershell
$cert = Get-ChildItem Cert:\CurrentUser\My | Where-Object Subject -eq 'CN=Windows Admin Center Client' | Select-Object -First 1
Invoke-RestMethod -Uri "https://localhost:6516/api/nodes/all/features/jea/endpoint/export" -Method POST -Certificate $cert -OutFile "~\Desktop\WindowsAdminCenter_RBAC.zip"
```

展开 zip 存档后，会看到以下文件夹结构：

- InstallJeaFeatures.ps1
- JustEnoughAdministration（目录）
- Modules（目录）
    - Microsoft.SME.\*（目录）
    - WindowsAdminCenter.Jea（目录）

若要在节点上配置对基于角色的访问控制的支持，需执行以下操作：

1.  将 JustEnoughAdministration、Microsoft.SME.\* 和 WindowsAdminCenter.Jea 模块复制到目标计算机上的 PowerShell 模块目录。 通常情况下，该位置是 `C:\Program Files\WindowsPowerShell\Modules`。
2.  更新 **InstallJeaFeature.ps1** 文件，使之与 RBAC 终结点的所需配置匹配。
3.  运行 InstallJeaFeature.ps1 以编译 DSC 资源。
4.  将 DSC 配置部署到所有计算机以应用该配置。

以下部分介绍如何使用 PowerShell 远程处理来这样做。

#### <a name="deploy-on-multiple-machines"></a>在多台计算机上部署

若要将下载的配置部署到多台计算机，需更新 **InstallJeaFeatures.ps1** 脚本，使之包含适用于环境的安全组，并将文件复制到每台计算机，然后调用配置脚本。
你可以使用首选的自动化工具来完成该操作，但本文将着重介绍单纯的基于 PowerShell 的方法。

默认情况下，该配置脚本将在计算机上创建本地安全组来控制对每个角色的访问。
这适用于已加入工作组和已加入域的计算机，但如果在仅限域的环境中部署，则可能需要将域安全组与每个角色直接关联。
若要更新配置，使之使用域安全组，请打开 **InstallJeaFeatures.ps1** 并进行以下更改：

1.  从文件中删除 3 个 **Group** 资源：
    1.  “Group MS-Readers-Group”
    2.  “Group MS-Hyper-V-Administrators-Group”
    3.  “Group MS-Administrators-Group”
2.  从 JeaEndpoint **DependsOn** 属性中删除 3 个 Group 资源
    1.  “[Group]MS-Readers-Group”
    2.  “[Group]MS-Hyper-V-Administrators-Group”
    3.  “[Group]MS-Administrators-Group”
3.  将 JeaEndpoint **RoleDefinitions** 属性中的组名称更改为所需的安全组。 例如，如果有一个 *CONTOSO\MyTrustedAdmins* 安全组并应向其分配对 Windows Admin Center 管理员角色的访问权限，请将 `'$env:COMPUTERNAME\Windows Admin Center Administrators'` 更改为 `'CONTOSO\MyTrustedAdmins'`。 需更新的三个字符串是：
    1.  '$env:COMPUTERNAME\Windows Admin Center Administrators'
    2.  '$env:COMPUTERNAME\Windows Admin Center Hyper-V Administrators'
    3.  '$env:COMPUTERNAME\Windows Admin Center Readers'

> [!NOTE]
> 请确保针对每个角色使用唯一安全组。 如果将同一安全组分配给多个角色，配置会失败。

接下来，请在 **InstallJeaFeatures.ps1** 文件末尾将以下 PowerShell 行添加到脚本底部：

```powershell
Copy-Item "$PSScriptRoot\JustEnoughAdministration" "$env:ProgramFiles\WindowsPowerShell\Modules" -Recurse -Force
$ConfigData = @{
    AllNodes = @()
    ModuleBasePath = @{
        Source = "$PSScriptRoot\Modules"
        Destination = "$env:ProgramFiles\WindowsPowerShell\Modules"
    }
}
InstallJeaFeature -ConfigurationData $ConfigData | Out-Null
Start-DscConfiguration -Path "$PSScriptRoot\InstallJeaFeature" -JobName "Installing JEA for Windows Admin Center" -Force
```

最后，可以将包含模块、DSC 资源和配置的文件夹复制到每个目标节点，然后运行 **InstallJeaFeature.ps1** 脚本。
若要从管理工作站远程执行该操作，可以运行以下命令：

```powershell
$ComputersToConfigure = 'MyServer01', 'MyServer02'

$ComputersToConfigure | ForEach-Object {
    $session = New-PSSession -ComputerName $_ -ErrorAction Stop
    Copy-Item -Path "~\Desktop\WindowsAdminCenter_RBAC\JustEnoughAdministration\" -Destination "$env:ProgramFiles\WindowsPowerShell\Modules\" -ToSession $session -Recurse -Force
    Copy-Item -Path "~\Desktop\WindowsAdminCenter_RBAC" -Destination "$env:TEMP\WindowsAdminCenter_RBAC" -ToSession $session -Recurse -Force
    Invoke-Command -Session $session -ScriptBlock { Import-Module JustEnoughAdministration; & "$env:TEMP\WindowsAdminCenter_RBAC\InstallJeaFeature.ps1" } -AsJob
    Disconnect-PSSession $session
}
```
