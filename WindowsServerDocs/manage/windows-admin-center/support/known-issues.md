---
title: Windows Admin Center 已知问题
description: Windows Admin Center 已知问题 (Project Honolulu)
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.date: 06/07/2019
ms.openlocfilehash: b4d7d039c775b85321d168f8de7415de6b92e784
ms.sourcegitcommit: 97a65d8f52514848963e8917021bd9a1f6ee3b19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89287819"
---
# <a name="windows-admin-center-known-issues"></a>Windows Admin Center 已知问题

> 适用于：Windows Admin Center、Windows Admin Center 预览版

如果遇到此页中未列出的问题，请[告诉我们](https://aka.ms/WACfeedback)。

## <a name="installer"></a>Installer

- 使用你自己的证书安装 Windows Admin Center 时，请注意，如果你从证书管理器 MMC 工具中复制指纹，[指纹开头将包含无效字符。](https://support.microsoft.com/help/2023835/certificate-thumbprint-displayed-in-mmc-certificate-snap-in-has-extra) 解决方法是键入指纹的第一个字符，然后复制/粘贴其余字符。

- 不支持使用低于1024的端口。 在服务模式下，你可以选择配置端口80以重定向到指定的端口。

## <a name="general"></a>常规

- 在 Windows 管理中心的1910.2 版本中，你可能无法连接到特定硬件上的 Hyper-v 服务器。 如果已阻止此问题， [请下载以前的版本](https://aka.ms/wacprevious)。

- 如果你已在 **Windows Server 2016** 上将 windows 管理中心作为网关安装，则该服务可能会崩溃，并在包含和的事件日志中出现错误 ```Faulting application name: sme.exe``` ```Faulting module name: WsmSvc.dll``` 。 这是由 Windows Server 2019 中已修复的 bug 引起的。 Windows Server 2016 的修补程序包含在 2 2019 月的累积更新（ [KB4480977](https://www.catalog.update.microsoft.com/Search.aspx?q=4480977)）。

- 如果已将 Windows 管理中心作为网关安装，且连接列表似乎已损坏，请执行以下步骤：

   > [!WARNING]
   >这会删除网关上所有 Windows 管理中心用户的连接列表和设置。

  1. 卸载 Windows Admin Center
  2. 删除 **C:\Windows\ServiceProfiles\NetworkService\AppData\Roaming\Microsoft** 下面的 **Server Management Experience** 文件夹
  3. 重新安装 Windows Admin Center

- 如果长期让工具保持打开和空闲状态，则可能会出现一些**错误：运行空间状态对此操作无效**错误。 如果出现这种情况，请刷新浏览器。 如果遇到这种情况，请 [向我们发送反馈](https://aka.ms/WACfeedback)。

- Windows 管理中心模块中运行的 OSS 版本号与第三方软件通知中列出的版本之间可能存在细微的差异。

### <a name="extension-manager"></a>扩展管理器

- 更新 Windows 管理中心时，必须重新安装扩展。
- 如果添加不可访问的扩展源，则不会出现警告。 [14412861]

## <a name="browser-specific-issues"></a>特定于浏览器的问题

### <a name="microsoft-edge"></a>Microsoft Edge

- 如果已将 Windows 管理中心部署为服务，并使用 Microsoft Edge 作为浏览器，则在生成新的浏览器窗口后，将网关连接到 Azure 可能会失败。 尝试解决此问题，方法是将 https://login.microsoftonline.com 、 https://login.live.com 和网关的 URL 添加为客户端浏览器的 "受信任的站点" 和 "允许的站点" 弹出窗口阻止程序设置。 有关解决此问题的更多指导，请查看 [故障排除指南](troubleshooting.md#azure-features-dont-work-properly-in-edge)。 [17990376]

### <a name="google-chrome"></a>Google Chrome

- 早于10月 (发布70版之前，2018) Chrome 有一个有关 websocket 协议和 NTLM 身份验证的 [bug](https://bugs.chromium.org/p/chromium/issues/detail?id=423609) 。 这会影响以下工具：事件、PowerShell、远程桌面。

- Chrome 可能会弹出多个凭据提示，尤其是在**工作组**（非域）环境中添加连接体验期间。

- 如果已将 Windows 管理中心部署为服务，则需要为要运行的任何 Azure 集成功能启用网关 URL 中的弹出窗口。

### <a name="mozilla-firefox"></a>Mozilla Firefox

未用 Mozilla Firefox 对 Windows Admin Center 进行测试，但大多数功能应该会正常工作。

- Windows 10 安装： Mozilla Firefox 具有自己的证书存储区，因此必须将证书导入到 ```Windows Admin Center Client``` Firefox，才能在 windows 10 上使用 Windows 管理中心。

## <a name="websocket-compatibility-when-using-a-proxy-service"></a>使用代理服务时的 WebSocket 兼容性

Windows Admin Center 中的远程桌面、PowerShell 和事件模块使用 WebSocket 协议，使用代理服务时通常不支持该协议。

## <a name="support-for-windows-server-versions-before-2016-2012-r2-2012-2008-r2"></a>支持 2016 (2012 R2、2012、2008 R2 之前的 Windows Server 版本) 

> [!NOTE]
> Windows 管理中心需要未包含在 Windows Server 2012 R2、2012或 2008 R2 中的 PowerShell 功能。 如果你将通过 Windows 管理中心管理 Windows Server，你将需要在这些服务器上安装 WMF 版本5.1 或更高版本。

在 PowerShell 中键入 `$PSVersiontable`，以验证是否安装了 WMF 并且版本是否为 5.1 或更高版本。

如果未安装，可以[下载并安装 WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616)。

## <a name="role-based-access-control-rbac"></a>基于角色的访问控制 (RBAC)

- 在配置为使用 Windows Defender 应用程序控制（WDAC，以前称为“代码完整性”）的计算机上，RBAC 部署将不会成功 [16568455]

- 若要在群集中使用 RBAC，必须将配置分别部署到每个成员节点。

- 部署 RBAC 后，你可能会遇到未授权错误，这些错误被错误地归因于 RBAC 配置。 [16369238]

## <a name="server-manager-solution"></a>服务器管理器解决方案

### <a name="certificates"></a>证书

- 无法将 .PFX 加密证书导入到当前用户存储。 [11818622]

### <a name="events"></a>事件

- [使用代理服务时的 WebSocket 兼容性](#websocket-compatibility-when-using-a-proxy-service)会影响事件。

- 导出大日志文件时，你可能会遇到一个引用“数据包大小”的错误。

  - 若要解决此问题，请在网关计算机上的权限提升的命令提示符中使用以下命令： ```winrm set winrm/config @{MaxEnvelopeSizekb="8192"}```

### <a name="files"></a>文件

- 仍不支持上载或下载大文件。  (\~ 100mb 限制) [12524234]

### <a name="powershell"></a>PowerShell

- [使用代理服务时的 WebSocket 兼容性](#websocket-compatibility-when-using-a-proxy-service)会影响 PowerShell

- 像在桌面 PowerShell 控制台中那样通过一次右键单击进行粘贴不起作用。 系统会改为向你呈现浏览器的上下文菜单，你可以在其中选择“粘贴”。 Ctrl-V 也可以正常使用。

- 用 Ctrl-C 进行复制不起作用，系统始终将向控制台发送 Ctrl-C 中断命令。 右键单击上下文菜单中的“复制”可以正常使用。

- 缩小 Windows Admin Center 窗口时，终端内容将重新排列，但是再次将其放大时，内容可能不会恢复为之前的状态。 如果内容变得杂乱，你可以尝试使用 Clear-Host，或者使用终端上面的按钮断开连接并重新连接。

### <a name="registry-editor"></a>注册表编辑器

- 未实现搜索功能。 [13820009]

### <a name="remote-desktop"></a>远程桌面

- 将 Windows 管理中心部署为服务时，在将 Windows 管理中心服务更新到新版本后，可能无法加载远程桌面工具。 若要解决此问题，请清除浏览器缓存。   [23824194]

- 在管理 Windows Server 2012 时，"远程桌面" 工具可能无法连接。 [20258278]

- 使用远程桌面连接到未加入域的计算机时，你必须以格式输入你的帐户 ```MACHINENAME\USERNAME``` 。

- 某些配置可以通过组策略阻止 Windows 管理中心的远程桌面客户端。 如果遇到这种情况，请 ```Allow users to connect remotely by using Remote Desktop Services``` 在 ```Computer Configuration/Policies/Administrative Templates/Windows Components/Remote Desktop Services/Remote Desktop Session Host/Connections```

- 远程桌面受 [websocket 兼容性影响。](#websocket-compatibility-when-using-a-proxy-service)

- 远程桌面工具当前不支持在本地桌面和远程会话之间复制/粘贴任何文本、图像或文件。

- 要在远程会话中进行任何复制/粘贴，你可以正常复制（右键单击并选择“复制”或按 Ctrl+C），但粘贴时需要右键单击并选择“粘贴”（Ctrl+V 不起作用）

- 你无法将以下键命令发送到远程会话
  - Alt+Tab
  - 功能键
  - Windows 键
  - PrtScn

### <a name="roles-and-features"></a>角色和功能

- 选择安装源不可用的角色或功能时，将跳过它们。 [12946914]

- 如果你选择在安装角色后不自动重新启动，我们将不会再次询问。 [13098852]

- 如果你选择自动重新启动，则将在状态更新为 100% 之前重新启动。 [13098852]

### <a name="storage"></a>存储

- 下层：DVD/CD/软盘驱动器在下层未显示为卷。

- 下层：卷和磁盘中的某些属性在下层不可用，因此它们在详细信息面板中显示为未知或空白。

- 下层：创建新卷时，ReFS 在 Windows 2012 和 2012 R2 计算机上仅支持 64K 的分配单元大小。 如果在下层目标上使用较小的分配单元大小创建了 ReFS 卷，则文件系统格式化将失败。 新卷将无法使用。 解决方法是删除卷并使用 64K 分配单元大小。

### <a name="updates"></a>更新

- 安装更新后，可能会缓存安装状态并需要浏览器进行刷新。

- 尝试设置 Azure 更新管理时，可能会遇到以下错误： "键集不存在"。 在这种情况下，请在托管节点上尝试以下更正步骤-
    1. 停止 "加密服务" 服务。
    2. 如果需要) ，请更改文件夹选项以显示隐藏的文件 (。
    3. 已到达 "%allusersprofile%\Microsoft\Crypto\RSA\S-1-5-18" 文件夹并删除其所有内容。
    4. 重新启动 "加密服务" 服务。
    5. 重复设置 Windows 管理中心更新管理

### <a name="virtual-machines"></a>虚拟机

- 在 Windows Server 2012 主机上管理虚拟机时，浏览器内 VM 连接工具将无法连接到 VM。 下载用于连接到 VM 的 .rdp 文件应该仍然有效。 [20258278]

- Azure Site Recovery –如果 ASR 是在 WAC 之外的主机上设置的，则你将无法在 WAC 中保护 VM [18972276]

- 目前不支持 Hyper-V 管理器中提供的高级功能，如虚拟 SAN 管理器、移动虚拟机、导出虚拟机、虚拟机复制。

### <a name="virtual-switches"></a>虚拟交换机

- 交换机嵌入式组合 (SET)：将 NIC 添加到组时，它们必须位于同一子网上。

## <a name="computer-management-solution"></a>计算机管理解决方案

计算机管理解决方案包含服务器管理器解决方案中的一部分工具，因此存在相同的已知问题，以及以下计算机管理解决方案特定问题：

- 如果使用 Microsoft 帐户 ([MSA](https://account.microsoft.com/account/)) 或者使用 AZURE ACTIVE DIRECTORY (AAD) 登录到 Windows 10 计算机，则必须使用 "管理身份" 来提供本地管理员帐户的凭据 [16568455]

- 尝试管理 localhost 时，将提示你提升网关进程。 如果单击后面的 "用户帐户控制" 弹出窗口中的 " **否** "，则必须取消连接尝试并重新启动。

- 默认情况下，Windows 10 不会启用 WinRM/PowerShell 远程处理。

  - 要启用 Windows 10 客户端管理，必须利用提升的 PowerShell 提示符发出 ```Enable-PSRemoting``` 命令。

  - 你可能还需要通过 ```Set-NetFirewallRule -Name WINRM-HTTP-In-TCP -RemoteAddress Any``` 来更新防火墙以允许从本地子网外部的连接。 有关限制性更强的网络方案，请参阅[本文档](/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1)。

## <a name="cluster-deployment"></a>群集部署

### <a name="step-12"></a>步骤1。2
添加服务器时，当前不支持混合工作组计算机。 用于群集的所有计算机都需要属于同一工作组。 否则，"下一步" 按钮将被禁用，并且将显示以下错误： "无法在不同 Active Directory 域中创建具有服务器的群集。 验证服务器名称是否正确。 将所有服务器移动到相同的域中，然后重试。 "

### <a name="step-14"></a>步骤1。4
Hyper-v 需要安装在运行 Azure Stack HCI OS 的虚拟机上。 尝试为这些虚拟机启用 Hyper-v 功能将失败，并出现以下错误：

![Hyper-v 启用错误的屏幕截图](../media/cluster-create-install-hyperv.png)

若要在运行 Azure Stack HCI OS 的虚拟机上安装 Hyper-v，请运行以下命令：

```PowerShell
Enable-WindowsOptionalFeature -Online -FeatureName 'Microsoft-Hyper-V'
```

### <a name="step-17"></a>步骤1。7
有时，在安装更新后，服务器的重启时间比预期要长。 Windows 管理中心群集部署向导将定期检查服务器重新启动状态，以了解是否已成功重新启动服务器。 但是，如果用户手动在向导外重新启动服务器，则向导无法以适当的方式捕获服务器状态。

如果要手动重新启动服务器，请退出当前向导会话。 重新启动服务器后，您可以重新启动该向导。

### <a name="stretch-cluster-creation"></a>Stretch 群集创建
建议在创建 stretch 群集时使用已加入域的服务器。 由于 WinRM 限制，尝试将工作组计算机用于 stretch 群集部署时出现网络分段问题。

### <a name="undo-and-start-over"></a>撤消并重新开始
如果为群集部署重复使用相同的计算机，则在同一组计算机中进行成功的群集部署非常重要。 有关如何清理群集的说明，请参阅 [部署超聚合基础结构](../use/deploy-hyperconverged-infrastructure.md#undo-and-start-over) 页。

### <a name="credssp"></a>CredSSP
Windows 管理中心群集部署向导在多个位置使用 CredSSP。 在向导过程中遇到此错误消息 (在验证群集步骤) 中最常见的情况：

![群集创建 CredSSP 错误的屏幕截图](../media/cluster-create-credssp-error.jpg)

你可以使用以下步骤来解决问题：

1. 在所有节点和 Windows 管理中心网关计算机上禁用 CredSSP 设置。 在网关计算机上运行第一个命令，并在群集中的所有节点上运行第二个命令：

```PowerShell
Disable-WsmanCredSSP -Role Client
```
```PowerShell
Disable-WsmanCredSSP -Role Server
```
2. 在所有节点上修复信任。 在所有节点上运行以下命令：
```PowerShell
Test-ComputerSecureChannel -Verbose -Repair -Credential <account name>
```

3. 使用命令重置组策略传播数据
```Command Line
gpupdate /force
```

4. 重新启动节点。 重新启动后，使用以下命令测试网关计算机和目标节点之间的连接以及节点之间的连接：
```PowerShell
Enter-PSSession -computername <node fqdn>
```

### <a name="nested-virtualization"></a>嵌套虚拟化
验证虚拟机上 Azure Stack HCI OS 群集部署时，需要在使用以下 powershell 命令启用角色/功能之前启用嵌套虚拟化：

```PowerShell
Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
```

  > [!Note]
  > 要使虚拟交换机组合在虚拟机环境中取得成功，需要在创建虚拟机后不久在该主机上在 PowerShell 中运行以下命令： Get-vm |% {VMNetworkAdapter-VMName $ _。名称-MacAddressSpoofing On-AllowTeaming on}

如果是使用 Azure Stack HCI OS 部署群集，则还需要额外的要求。 必须为 VM 启动虚拟硬盘预安装 Hyper-v 功能。 为此，请在创建虚拟机之前运行以下命令：

```PowerShell
Install-WindowsFeature –VHD <Path to the VHD> -Name Hyper-V, RSAT-Hyper-V-Tools, Hyper-V-PowerShell
```

### <a name="support-for-rdma"></a>支持 RDMA
Windows 管理中心版本2007中的群集部署向导不为 RDMA 配置提供支持。

## <a name="failover-cluster-manager-solution"></a>故障转移群集管理器解决方案

- 管理群集（是超聚合还是传统？）时可能会遇到**找不到 Shell** 错误。 如果发生这种情况，请重新加载浏览器，或导航到其他工具并返回。 [13882442]

- 管理尚未完全配置的下层（Windows Server 2012 或 2012 R2）群集时，可能会出现问题。 此问题的解决方法是确保已在群集的**每个成员节点**上安装并启用了 Windows 功能 **RSAT-Clustering-PowerShell**。 要使用 PowerShell 执行此操作，请在所有群集节点上输入命令 `Install-WindowsFeature -Name RSAT-Clustering-PowerShell`。 [12524664]

- 可能需要添加群集与整个 FQDN 才能正确被发现。

- 使用安装为网关的 Windows Admin Center 连接到群集并提供显式用户名/密码进行身份验证时，必须选择 **Use these credentials for all connections** 以便可使用凭据查询成员节点。

## <a name="hyper-converged-cluster-manager-solution"></a>超聚合群集管理器解决方案

- 诸如**驱动器 - 更新固件**、**服务器 - 删除**和**卷 - 打开**之类的某些命令被禁用并且当前不受支持。

## <a name="azure-services"></a>Azure 服务

### <a name="azure-file-sync-permissions"></a>Azure 文件同步权限

Azure 文件同步需要 Azure 中的权限，但 Windows 管理中心未在版本1910之前提供。 如果使用早于 Windows 管理中心版本1910的版本向 Azure 注册了 Windows 管理中心网关，则需要更新 Azure Active Directory 应用程序，以获取最新版本的 Windows 管理中心中的 Azure 文件同步的正确权限。 其他权限允许 Azure 文件同步按本文中所述执行存储帐户访问的自动配置： [确保 Azure 文件同步有权访问存储帐户](/azure/storage/files/storage-sync-files-troubleshoot?tabs=portal1%2cazure-portal#tabpanel_CeZOj-G++Q-5_azure-portal)。

若要更新 Azure Active Directory 应用，可以执行以下两项操作之一
1. 请参阅**Settings**  >  "**azure**  >  **注销**" 设置，然后再次向 azure 注册 Windows 管理中心，确保你选择创建新的 Azure Active Directory 应用程序。
2. 中转到 Azure Active Directory 应用程序，并手动添加向 Windows 管理中心注册的现有 Azure Active Directory 应用所需的权限。 为此，请**Settings**  >  **Azure**  >  **在 azure 中**中转到 "设置" "azure 视图"。 从 Azure 中的 " **应用注册** " 边栏选项卡中转到 " **API 权限**"，选择 " **添加权限**"。 向下滚动以选择 **Azure Active Directory 关系图**，选择 " **委托的权限**"，展开 " **目录**"，然后选择 " **AccessAsUser**"。 单击 " **添加权限** "，将更新保存到应用中。

### <a name="options-for-setting-up-azure-management-services"></a>用于设置 Azure 管理服务的选项

Azure 管理服务（包括 Azure Monitor、Azure 更新管理和 Azure 安全中心）为本地服务器使用同一代理： Microsoft Monitoring Agent。 Azure 更新管理包含一组受支持的受支持区域，需要将 Log Analytics 工作区链接到 Azure 自动化帐户。 由于此限制，如果想要在 Windows 管理中心中设置多个服务，则必须首先设置 Azure 更新管理，然后设置 Azure 安全中心或 Azure Monitor。 如果已配置任何使用 Microsoft Monitoring Agent 的 Azure 管理服务，然后尝试使用 Windows 管理中心设置 Azure 更新管理，则在链接到 Microsoft Monitoring Agent 的现有资源支持 Azure 更新管理时，Windows 管理中心将仅允许配置 Azure 更新管理。 如果不是这种情况，则有两个选择：

1. 请通过 "控制面板" > Microsoft Monitoring Agent 断开服务器与 Azure Monitor 或 Azure 安全) 中心等 ([的现有 Azure 管理解决方案的连接](/azure/azure-monitor/platform/log-faq#q-how-do-i-stop-an-agent-from-communicating-with-log-analytics) 。 然后在 Windows 管理中心中设置 Azure 更新管理。 之后，你可以返回到通过 Windows 管理中心设置其他 Azure 管理解决方案，而不会出现问题。
2. 可以 [手动设置 azure 更新管理所需的 azure 资源](/azure/automation/automation-update-management) ，然后在 Windows 管理中心) 外部 [手动更新 Microsoft Monitoring Agent](/azure/azure-monitor/platform/agent-manage#adding-or-removing-a-workspace) (，以添加与要使用的更新管理解决方案相对应的新工作区。
