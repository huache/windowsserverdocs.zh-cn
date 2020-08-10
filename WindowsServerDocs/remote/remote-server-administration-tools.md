---
title: 远程服务器管理工具
description: 远程服务器管理工具的深入主题
ms.topic: get-started-article
ms.assetid: d54a1f5e-af68-497e-99be-97775769a7a7
author: coreyp-at-msft
ms.author: coreyp
manager: dansimp
ms.openlocfilehash: 49a86a24b3637a701d6857af246eaa2852f1c73f
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87948770"
---
# <a name="remote-server-administration-tools"></a>远程服务器管理工具

>适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本主题支持适用于 Windows 10 的远程服务器管理工具。

> [!IMPORTANT]
> 从 Windows 10 2018 年 10 月更新开始，RSAT 作为一组“按需功能”包含在 Windows 10 中。 有关安装说明，请参阅下面的“何时使用何种 RSAT 版本”。

RSAT 允许 IT 管理员从 Windows 10 PC 管理 Windows Server 角色和功能。

远程服务器管理工具包括服务器管理器、Microsoft 管理控制台 (mmc) 管理单元、控制台、Windows PowerShell cmdlet 和提供程序，以及一些用于管理 Windows Server 上运行的角色和功能的命令行工具。

远程服务器管理工具包括 Windows PowerShell cmdlet 模块，它们可用于管理在远程服务器上运行的角色和功能。 虽然 Windows Server 2016 上默认启用了 Windows PowerShell 远程管理，但 Windows 10 上并未默认启用它。 若要针对远程服务器运行作为远程服务器管理工具一部分的 cmdlet，请在安装远程服务器管理工具后，在 Windows 客户端计算机上以提升的用户权限（即以管理员身份运行）打开 Windows PowerShell 会话，然后在其中运行 `Enable-PSremoting`。

## <a name="remote-server-administration-tools-for-windows-10"></a><a name="BKMK_Thresh"></a>适用于 Windows 10 的远程服务器管理工具
使用适用于 Windows 10 的远程服务器管理工具管理运行 Windows Server 2019、Windows Server 2016、Windows Server 2012 R2（在有限的情况下，Windows Server 2012 或 Windows Server 2008 R2）的计算机上的特定技术。

适用于 Windows 10 的远程服务器管理工具包括对运行服务器核心安装选项或 Windows Server 2016 和 Windows Server 2012 R2 的最小服务器界面配置（在有限情况下，Windows Server 2012 的服务器核心安装选项）的计算机的远程管理支持。 不过，适用于 Windows 10 的远程服务器管理工具不能在任何版本的 Windows Server 操作系统上安装。

### <a name="tools-available-in-this-release"></a>此版本中的可用工具
有关适用于 Windows 10 的远程服务器管理工具中提供的工具列表，请参阅[适用于 Windows 操作系统的远程服务器管理工具 (RSAT)](https://support.microsoft.com/help/2693643/remote-server-administration-tools-rsat-for-windows-operating-systems) 中的表。

### <a name="system-requirements"></a>系统要求
仅可在运行 Windows 10 的计算机上安装适用于 Windows 10 的远程服务器管理工具。 远程服务器管理工具无法安装在运行 Windows RT 8.1 的计算机上或其他片上系统设备上。

适用于 Windows 10 的远程服务器管理工具可在基于 x86 和基于 x64 版本的 Windows 10 上运行。

> [!IMPORTANT]
> 适用于 Windows 10 的远程服务器管理工具不应该在运行 Windows 8.1、Windows 8、Windows Server 2008 R2、Windows Server 2008、Windows Server 2003 或 Windows 2000 Server 管理工具包的计算机上安装。 删除计算机中所有旧版本的管理工具包或者远程服务器管理工具（包括较早的预发布版本和不同语言或区域设置的工具版本），然后安装适用于 Windows 10 的远程服务器管理工具。

若要使用此版本的服务器管理器来访问和管理运行 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 的远程服务器，则必须安装一些更新，以便可通过使用服务器管理器管理旧版本的 Windows Server 操作系统。 有关如何通过使用适用于 Windows 10 的远程服务器管理工具中的服务器管理器为管理准备 Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2008 R2 的详细信息，请参阅[使用服务器管理器管理多台远程服务器](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831456(v=ws.11))。

必须在远程服务器上启用 Windows PowerShell 和服务器管理器远程管理，以便使用适用于 Windows 10 的远程服务器管理工具中的工具管理它们。 默认情况下，在运行 Windows Server 2016、Windows Server 2012 R2 和 Windows Server 2012 的服务器上启用远程管理。 有关如何在已禁用远程管理的情况下启用它的详细信息，请参阅 [使用服务器管理器管理多台远程服务器](https://go.microsoft.com/fwlink/p/?LinkId=241358)。

## <a name="install-uninstall-and-turn-offon-rsat-tools"></a>安装、卸载和关闭/启用 RSAT 工具

### <a name="use-features-on-demand-fod-to-install-specific-rsat-tools-on-windows-10-october-2018-update-or-later"></a>使用按需功能 (FoD) 在 Windows 10 2018 年 10 月更新或更高版本上安装特定的 RSAT 工具。

从 Windows 10 2018 年 10 月更新开始，RSAT 作为一组“按需功能”直接包含在 Windows 10 中。 现在，不用下载 RSAT 包，只需转到“设置”中的“管理可选功能”，然后单击“添加功能”，即可查看可用的 RSAT 工具列表  。 选择并安装所需的特定 RSAT 工具。 若要查看安装进度，请单击“后退”按钮，在“管理可选功能”页上查看状态 。

请参阅[由“按需功能”提供的 RSAT 工具列表](/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod#remote-server-administration-tools-rsat)。 除了通过图形“设置”应用进行安装以外，还可以使用 [DISM /Add-Capability](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities#using-dism-add-capability-to-add-or-remove-fods) 通过命令行或自动化来安装特定的 RSAT 工具 。

按需功能的一个好处是，已安装的功能在 Windows 10 版本升级保持不变。

#### <a name="to-uninstall-specific-rsat-tools-on-windows-10-october-2018-update-or-later-after-installing-with-fod"></a>在 Windows 10 2018 年 10 月更新或更高版本（安装 FoD 后）上卸载特定的 RSAT 工具

在 Windows 10 上，打开“设置”应用，转到“管理可选功能”，选择并卸载要移除的特定 RSAT 工具 。 请注意，在某些情况下‘需要手动卸载依赖项。 具体来说，如果 RSAT 工具 B 需要 RSAT 工具 A，并且仍旧安装了 RSAT 工具 B，则选择卸载 RSAT 工具 A 将失败。 在这种情况下，请先卸载 RSAT 工具 B，然后卸载 RSAT 工具 A。另请注意，在某些情况下，即使仍安装了该工具，卸载 RSAT 工具也可能会成功。 在这种情况下，重启计算机将完成此工具的移除。

请参阅[包含依赖项的 RSAT 工具列表](/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod#remote-server-administration-tools-rsat)。 除了通过图形“设置”应用进行卸载以外，还可以使用 [DISM /Remove-Capability](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities#using-dism-add-capability-to-add-or-remove-fods) 通过命令行或自动化来卸载特定的 RSAT 工具。

### <a name="when-to-use-which-rsat-version"></a>何时使用何种 RSAT 版本

如果你的 Windows 10 版本早于 2018 年 10 月更新 (1809)，则将无法使用“按需功能”。 你需要下载并安装 RSAT 包。

- 如上所述，直接从 Windows 10 安装 RSAT FOD：为管理 Windows Server 2019 或早期版本，在 Windows 10 2018 年 10 月更新 (1809) 或更高版本上安装时。

- 如下所述，下载并安装 WS_1803 RSAT 包：为管理版本 1803 或版本 1709 的 Windows Server，在 Windows 10 2018 年 4 月更新 (1803) 或更早版本上安装时。

- 如下所述，下载并安装 WS2016 RSAT 包：为管理 Windows Server 2016 或早期版本，在 Windows 10 2018 年 4 月更新 (1803) 或更早版本上安装时。

#### <a name="download-the-rsat-package-to-install-remote-server-administration-tools-for-windows-10"></a><a name="BKMK_installthresh"></a>下载用于安装适用于 Windows 10 远程服务器管理工具的 RSAT 包

1.  从 [Microsoft 下载中心](https://go.microsoft.com/fwlink/?LinkID=404281)下载适用于 Windows 10 的远程服务器管理工具包。 你可以从下载中心网站运行安装程序，或者将下载包保存到本地计算机或共享。

    > [!IMPORTANT]
    > 只能在运行 Windows 10 的计算机上安装适用于 Windows 10 的远程服务器管理工具。 远程服务器管理工具无法安装在运行 Windows RT 8.1 的计算机上或其他片上系统设备上。

2.  如果你将下载包保存到本地计算机或共享，则根据要安装工具的计算机的体系结构，双击安装程序 **WindowsTH-KB2693643-x64.msu** 或 **WindowsTH-KB2693643-x86.msu**。

3.  当 **“Windows 更新独立安装程序”** 对话框提示你安装更新时，单击 **“是”** 。

4.  阅读并接受许可条款。 单击 **“我接受”** 。

5.  安装需要几分钟才能完成。

##### <a name="to-uninstall-remote-server-administration-tools-for-windows-10-after-rsat-package-install"></a>卸载适用于 Windows 10 的远程服务器管理工具（在 RSAT 包安装后）的具体步骤

1. 在桌面上，依次单击“开始” 、“所有应用” 、“Windows 系统” 和“控制面板” 。

2. 在“程序” 下，单击“卸载程序” 。

3. 单击 **“查看已安装的更新”** 。

4. 右键单击“Microsoft Windows 的更新(KB2693643)” ，然后单击“卸载” 。

5. 当系统询问你是否确定要卸载更新时，单击 **“是”** 。
   S
   ##### <a name="to-turn-off-specific-tools-after-rsat-package-install"></a>关闭特定工具（在 RSAT 包安装后）

6. 在桌面上，依次单击“开始” 、“所有应用” 、“Windows 系统” 和“控制面板” 。

7. 单击 **“程序”** ，然后在 **“程序和功能”** 中单击 **“打开或关闭 Windows 功能”** 。

8. 在 **“Windows 功能”** 对话框中，展开 **“远程服务器管理工具”** ，然后展开 **“角色管理工具”** 或 **“功能管理工具”** 。

9. 清除要关闭的工具对应的复选框。

   > [!NOTE]
   > 如果关闭服务器管理器，则计算机必须重新启动，并且可从服务器管理器的“工具”菜单中访问的工具必须从“管理工具”文件夹打开 。

10. 关闭完不使用的工具后，单击 **“确定”** 。

### <a name="run-remote-server-administration-tools"></a>运行远程服务器管理工具

> [!NOTE]
> 安装适用于 Windows 10 的远程服务器管理工具后，“管理工具”文件夹将显示在“开始”菜单上 。 可以从以下位置访问这些工具。
>
> -   服务器管理器控制台中的“工具”菜单。
> -   “控制面板”\“系统和安全”\“管理工具”。
> -   从“管理工具”  文件夹保存到桌面的快捷方式（若要创建此快捷方式，请右键单击“控制面板”\“系统和安全”\“管理工具”  链接，然后单击“创建快捷方式” ）。

无法将作为适用于 Windows 10 的远程服务器管理工具的一部分安装的工具用于管理本地客户端计算机。 不管运行什么工具，必须指定一台或多台远程服务器来运行该工具。 因为大多数工具都与服务器管理器集成，所以可以将要管理的远程服务器添加到服务器管理器的服务器池，然后使用“工具”菜单中的工具管理该服务器。 有关如何将服务器添加到服务器池并创建服务器的自定义组的详细信息，请参阅 [将服务器添加到服务器管理器](https://go.microsoft.com/fwlink/p/?LinkId=241353) 和 [创建和管理服务器组](https://go.microsoft.com/fwlink/?LinkId=247328)。

在适用于 Windows 10 的远程服务器管理工具中，所有基于 GUI 的服务器管理工具（如 mmc 管理单元和对话框）都可以从服务器管理器控制台的“工具”菜单中进行访问。 虽然运行适用于 Windows 10 的远程服务器管理工具的计算机运行基于客户端的操作系统，但安装这些工具后，适用于 Windows 10 的远程服务器管理工具中的随附的服务器管理器将在客户端计算机上默认自动打开。 请注意，在客户端计算机上运行的服务器管理器控制台中没有“本地服务器”页。

##### <a name="to-start-server-manager-on-a-client-computer"></a>在客户端计算机上启动服务器管理器的步骤

1.  在“开始”  菜单中，单击“所有应用” ，然后单击“管理工具” 。

2.  在“管理工具”  文件夹中，单击“服务器管理器” 。

虽然未在服务器管理器控制台“工具”菜单中列出，但 Windows PowerShell cmdlet 和命令提示符管理工具也作为远程服务器管理工具的一部分为角色和功能安装。 例如，如果你使用提升的用户权限（以管理员身份运行）打开 PowerShell 会话并运行 cmdlet `Get-Command -Module RDManagement`，则结果包含一个远程桌面服务 cmdlet 列表。只要 cmdlet 针对的是运行全部或部分远程桌面服务角色的远程服务器，安装远程服务器管理工具后，远程桌面服务 cmdlet 可以在本地计算机上运行。

##### <a name="to-start-windows-powershell-with-elevated-user-rights-run-as-administrator"></a>使用提升的用户权限启动 Windows PowerShell（以管理员身份运行）

1.  在“开始”  菜单中，依次单击“所有应用” 、“Windows 系统” 和“Windows PowerShell” 。

2.  若要从桌面以管理员身份运行 Windows PowerShell，请右键单击“Windows PowerShell”快捷方式，然后单击“以管理员身份运行” 。

> [!NOTE]
> 你还可以启动针对特定服务器的 Windows PowerShell 会话，方法是右键单击服务器管理器中角色或组页中的托管服务器，然后单击“Windows PowerShell”。


## <a name="known-issues"></a>已知问题

### <a name="issue-rsat-fod-installation-fails-with-error-code-0x800f0954"></a>**问题**：RSAT FOD 安装失败，错误代码为 0x800f0954

> **影响**：WSUS/配置管理器环境中 Windows 10 1809（2018 年 10 月更新）上的 RSAT FOD
>
> **解决方法**：若要在通过 WSUS 或配置管理器接收更新且已加入域的计算机上安装 FOD，你需要更改“组策略”设置，以允许直接从 Windows 更新或本地共享下载 FOD。 有关如何更改该设置的更多详细信息和说明，请参阅[使用 WSUS/SCCM 时，如何使按需功能和语言包可用](/windows/deployment/update/fod-and-lang-packs)。

---

### <a name="issue-rsat-fod-installation-via-settings-app-does-not-show-statusprogress"></a>**问题**：通过“设置”应用进行的 RSAT FOD 安装不显示状态/进度

> **影响**：Windows 10 1809（2018 年 10 月更新）上的 RSAT FOD
>
> **解决方法**：若要查看安装进度，请单击“后退”按钮，在“管理可选功能”页上查看状态 。

---

### <a name="issue-rsat-fod-uninstallation-via-settings-app-may-fail"></a>**问题**：通过“设置”应用进行的 RSAT FOD 卸载可能会失败

> **影响**：Windows 10 1809（2018 年 10 月更新）上的 RSAT FOD
>
> **解决方法**：在某些情况下，卸载失败的原因是需要手动卸载依赖项。 具体来说，如果 RSAT 工具 B 需要 RSAT 工具 A，并且仍旧安装了 RSAT 工具 B，则选择卸载 RSAT 工具 A 将失败。 在这种情况下，请先卸载 RSAT 工具 B，然后卸载 RSAT 工具 A。请参阅包含依赖项的 RSAT FOD 列表。

---

### <a name="issue-rsat-fod-uninstallation-appears-to-succeed-but-the-tool-is-still-installed"></a>**问题**：RSAT FOD 卸载似乎已成功，但工具仍为安装状态

> **影响**：Windows 10 1809（2018 年 10 月更新）上的 RSAT FOD
>
> **解决方法**：重启计算机将完成此工具的移除。

---

### <a name="issue-rsat-missing-after-windows-10-upgrade"></a>**问题**：Windows 10 升级后，RSAT 丢失

> **影响**：无法自动重新安装任何 RSAT .MSU 安装包（在 RSAT FOD 之前）
>
> **解决方法**：由于 RSAT .MSU 作为 Windows 更新包提供，因此 RSAT 安装不能在操作系统升级期间保留。 请在升级 Windows 10 后再次安装 RSAT。 请注意，此限制是我们从 Windows 10 1809 开始迁移到 FOD 的原因之一。 在未来的 Windows 10 版本升级中，已安装的 RSAT FOD 将保持不变。

## <a name="see-also"></a>另请参阅
>- [适用于 Windows 10 的远程服务器管理工具](https://go.microsoft.com/fwlink/?LinkID=404281)
>- [适用于 Windows Vista、Windows 7、Windows 8、Windows Server 2008、Windows Server 2008 R2、Windows Server 2012 和 Windows Server 2012 R2 的远程服务器管理工具 (RSAT)](https://go.microsoft.com/fwlink/p/?LinkID=221055)
