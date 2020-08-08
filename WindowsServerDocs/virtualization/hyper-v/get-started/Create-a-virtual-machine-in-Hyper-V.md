---
title: 在 Hyper-V 中创建虚拟机
description: 提供有关使用 Hyper-v 管理器或 Windows PowerShell 创建虚拟机的说明
manager: dongill
ms.topic: get-started-article
ms.assetid: 59297022-a898-456c-b299-d79cd5860238
author: kbdazure
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: 22dc2e83f1c7370bfd6f97d821a83041a9c528fe
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87996607"
---
# <a name="create-a-virtual-machine-in-hyper-v"></a>在 Hyper-V 中创建虚拟机

>适用于： Windows 10、Windows Server 2016、Microsoft Hyper-V Server 2016、Windows Server 2019、Microsoft Hyper-V Server 2019

了解如何使用 Hyper-v 管理器和 Windows PowerShell 创建虚拟机，以及在 Hyper-v 管理器中创建虚拟机时使用的选项。

## <a name="create-a-virtual-machine-by-using-hyper-v-manager"></a>使用 Hyper-v 管理器创建虚拟机

1.  打开**Hyper-v 管理器**。

2.  在 "**操作**" 窗格中，单击 "**新建**"，然后单击 "**虚拟机**"。

3.  在**新建虚拟机向导**中，单击 "**下一步**"。

4.  在每个页面上为虚拟机进行适当的选择。 有关详细信息，请参阅本主题后面的[Hyper-v 管理器中的新虚拟机选项和默认值](#options-in-hyper-v-manager-new-virtual-machine-wizard)。

5.  在 "**摘要**" 页中验证你的选择后，单击 "**完成**"。

6.  在 "Hyper-v 管理器" 中，右键单击虚拟机，然后选择 "**连接**"。

7.  在 "虚拟机连接" 窗口中，选择 "**操作**  >  **启动**"。

## <a name="create-a-virtual-machine-by-using-windows-powershell"></a>使用 Windows PowerShell 创建虚拟机

1. 在 Windows 桌面上，单击“开始”按钮并键入名称 **Windows PowerShell** 的任一部分。

2. 右键单击“Windows PowerShell”，然后选择“以管理员身份运行”。

3. 使用[获取-VMSwitch](/powershell/module/hyper-v/get-vmswitch?view=win10-ps)获取虚拟机要使用的虚拟交换机的名称。  例如，应用于对象的

   ```
   Get-VMSwitch  * | Format-Table Name
   ```

4. 使用[新的-VM](/powershell/module/hyper-v/new-vm?view=win10-ps) cmdlet 来创建虚拟机。  请参阅以下示例。

   > [!NOTE]
   > 如果可以将此虚拟机移动到运行 Windows Server 2012 R2 的 Hyper-v 主机，请将-Version 参数与[New-VM](/powershell/module/hyper-v/new-vm?view=win10-ps)一起使用，将虚拟机配置版本设置为5。 Windows server 2012 R2 或更低版本不支持 Windows Server 2016 的默认虚拟机配置版本。 创建虚拟机后，无法更改虚拟机配置版本。 有关详细信息，请参阅[支持的虚拟机配置版本](../deploy/Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md#supported-virtual-machine-configuration-versions)。

   - **现有虚拟硬盘**-若要使用现有的虚拟硬盘创建虚拟机，可以使用以下命令，其中，
     - **-Name** 是为你要创建的虚拟机提供的名称。
     - **-MemoryStartupBytes** 是启动时可供虚拟机使用的内存量。
     - **-BootDevice**是虚拟机在启动时启动到的设备，如网络适配器 (网络适配器) 或虚拟硬盘 (VHD) 。
     - **-VHDPath** 是要使用的虚拟机磁盘的路径。
     - **-Path** 是存储虚拟机配置文件的路径。
     - **-Generation** 是虚拟机代系。 对于 VHD，请使用第 1 代；对于 VHDX，请使用第 2 代。 请参阅[应在 hyper-v 中创建第1代还是第2代虚拟机？。](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md)
     - **-Switch** 是你希望虚拟机用来连接其他虚拟机或网络的虚拟交换机的名称。 请参阅[创建用于 hyper-v 虚拟机的虚拟交换机](Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)。

       ```
       New-VM -Name <Name> -MemoryStartupBytes <Memory> -BootDevice <BootDevice> -VHDPath <VHDPath> -Path <Path> -Generation <Generation> -Switch <SwitchName>
       ```

       例如：

       ```
       New-VM -Name Win10VM -MemoryStartupBytes 4GB -BootDevice VHD -VHDPath .\VMs\Win10.vhdx -Path .\VMData -Generation 2 -Switch ExternalSwitch
       ```

       这将创建一个名为 Win10VM 的第2代虚拟机，内存为4GB。 它从当前目录中的 VMs\Win10.vhdx 文件夹引导，并使用名为 ExternalSwitch 的虚拟交换机。 虚拟机配置文件存储在 VMData 文件夹中。

   - **新虚拟硬盘**-若要使用新的虚拟硬盘创建虚拟机，请将上述示例中的 **-VHDPath**参数替换为 **-NewVHDPath** ，并添加 **-NewVHDSizeBytes**参数。 例如，应用于对象的

     ```
     New-VM -Name Win10VM -MemoryStartupBytes 4GB -BootDevice VHD -NewVHDPath .\VMs\Win10.vhdx -Path .\VMData -NewVHDSizeBytes 20GB -Generation 2 -Switch ExternalSwitch
     ```

   - **用于启动到操作系统映像的新虚拟硬盘**-若要使用启动到操作系统映像包的新虚拟磁盘创建虚拟机，请参阅在[Windows 10 上创建虚拟机演练](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)中的 PowerShell 示例。

5. 使用[启动 VM](/powershell/module/hyper-v/start-vm?view=win10-ps) cmdlet 启动虚拟机。 运行以下 cmdlet，其中 Name 是你创建的虚拟机的名称。

   ```
   Start-VM -Name <Name>
   ```

   例如：

   ```
   Start-VM -Name Win10VM
   ```

6. 使用 (VMConnect) 的虚拟机连接连接到虚拟机。

   ```
   VMConnect.exe
   ```

## <a name="options-in-hyper-v-manager-new-virtual-machine-wizard"></a>Hyper-v 管理器新建虚拟机向导中的选项
下表列出了在 Hyper-v 管理器中创建虚拟机时可以选取的选项，以及每个虚拟机的默认值。

|页面|Windows Server 2016 和 Windows 10 的默认值|其他选项|
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|**指定名称和位置**|名称：新虚拟机。<p>位置： **C:\ProgramData\Microsoft\Windows\Hyper-V \\ **。|你还可以输入自己的名称，并为虚拟机选择另一个位置。<p>这是将存储虚拟机配置文件的位置。|
|**指定生成**|第 1 代|你还可以选择创建第2代虚拟机。 有关详细信息，请参阅是否[应在 hyper-v 中创建第1代或第2代虚拟机？。](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md)|
|**分配内存**|启动内存： 1024 MB<p>动态内存：**未选择**|可以将启动内存从32MB 设置为5902MB。<p>你还可以选择使用动态内存。 有关详细信息，请参阅[hyper-v 动态内存概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831766(v=ws.11))。|
|**配置网络**|未连接|你可以从现有虚拟交换机列表中选择虚拟机要使用的网络连接。 请参阅[创建用于 hyper-v 虚拟机的虚拟交换机](Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)。|
|**连接虚拟硬盘**|创建虚拟硬盘<p>名称： <*vmname*> .vhdx<p>**位置**： **C:\Users\Public\Documents\Hyper-V\Virtual \\ 硬盘**<p>**大小**：127GB|你还可以选择使用现有的虚拟硬盘，或者等待并在以后附加虚拟硬盘。|
|**安装选项**|稍后安装操作系统|这些选项将更改虚拟机的启动顺序，以便可以从 .iso 文件、可启动软盘或网络安装服务（如 Windows 部署服务 (WDS) 安装。|
|**摘要**|显示您选择的选项，以便您可以验证它们是否正确。<p>-   Name<br />-生成<br />-   内存<br />-网络<br />-硬盘<br />-操作系统|**提示：** 可以从页面复制摘要，并将其粘贴到电子邮件或其他地方，以帮助跟踪虚拟机。|

## <a name="additional-references"></a>其他参考

- [新 VM](/powershell/module/hyper-v/new-vm?view=win10-ps)

- [支持的虚拟机配置版本](../deploy/Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md#supported-virtual-machine-configuration-versions)

-   [是否应在 Hyper-V 中创建第 1 代或第 2 代虚拟机？](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md)

-   [为 Hyper-V 虚拟机创建虚拟交换机](Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)