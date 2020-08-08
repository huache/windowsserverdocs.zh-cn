---
title: Configure Features on Demand in Windows Server
description: 服务器管理器
ms.topic: article
ms.assetid: e663bbea-d025-41fa-b16c-c2bff00a88e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ffe38a896e7913d03cc8f4ad62d1e520cec6a0c2
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87991927"
---
# <a name="configure-features-on-demand-in-windows-server"></a>Configure Features on Demand in Windows Server

>适用于：Windows Server 2016

本主题描述了如何使用 Uninstall-WindowsFeature cmdlet 在“按需功能”配置中删除功能文件。

"按需功能" 是 Windows 8 和 Windows Server 2012 中引入的一项功能，可用于从操作系统中删除角色和功能文件（有时称为功能*负载*)  (），以节省磁盘空间，并从远程位置或安装媒体而非本地计算机安装角色和功能。 你可以从运行中的物理或虚拟计算机删除功能文件。 你也可以对 Windows 映像 (WIM) 文件或脱机虚拟硬盘 (VHD) 进行添加或删除功能文件，为“按需功能”配置创建一个可复制的副本。

在 "按需功能" 配置中，当功能文件在计算机上不可用时，如果安装需要这些功能文件，则可以将 Windows Server 2012 R2 或 Windows Server 2012 定向到从并行功能存储区获取文件 (包含功能文件的共享文件夹，并可用于网络上的计算机) 、从 Windows 更新或从安装媒体中获取。 默认情况下，当功能文件不在目标服务器上时，“按需功能”就会按照所示顺序执行下列任务，来搜索丢失的功能文件。

1.  在 "添加角色和功能向导" 或 DISM 安装命令的用户指定的位置搜索

2.  评估组策略设置的配置、**用于可选组件安装和组件修复的计算机配置 \ \ 设置**

3.  搜索 Windows 更新

你可以采用下列任意方法覆盖默认的“按需功能”行为。

-   通过添加 `Install-WindowsFeature` 参数指定一个备用源路径，作为 `Source` cmdlet 的一部分

-   使用 "添加角色和功能向导" 安装功能时，在 "**确认安装选项**" 页上指定备用源路径

-   配置“组策略”设置，“指定可选组件安装和组件修复的设置”****

本主题包含以下各节：

-   [创建功能文件或并排存储区](#BKMK_store)

-   [删除功能文件的方法](#BKMK_methods)

-   [使用 Uninstall-WindowsFeature 删除功能文件](#BKMK_remove)

## <a name="create-a-feature-file-or-side-by-side-store"></a><a name=BKMK_store></a>创建功能文件或并排存储区
本部分介绍如何设置远程功能文件共享文件夹 (也称为并排存储) ，用于存储在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装角色、角色服务和功能所需的文件。 设置功能存储区后，可以在运行这些操作系统的服务器上安装角色、角色服务和功能，并将功能存储指定为安装源文件的位置。

#### <a name="to-create-a-feature-file-store"></a>创建功能文件存储区的步骤

1.  在网络的服务器上创建一个共享文件夹。 例如， * \\ \network\share\sxs*。

2.  验证是否给功能存储区分配了恰当的权限。 源路径或文件共享必须向**Everyone**组授予 "**读取**" 权限 (出于安全原因，不建议这样做) ，或授予*DOMAIN* \\ 你计划使用此功能存储区安装功能的服务器的计算机帐户 (DOMAIN*SERverNAME*$) ; 授予用户帐户访问权限是不够的。

    你可以通过在 Windows 桌面上进行以下任意一种操作，来访问文件共享和权限设置。

    -   右键单击共享文件夹，单击“属性”****，然后在“安全”**** 选项卡上更改允许的用户及其访问文件夹的权限。

    -   右键单击共享文件夹，指向“共享给”****，然后单击“特定用户”****。

    > [!NOTE]
    > 即使工作组服务器的计算机帐户具有外部共享“读取”**** 权限，位于工作组中的服务器也无法访问外部文件共享。 为工作组服务器服务的备用源位置包括安装媒体、Windows 更新和存储在本地工作组服务器上的 VHD 或 WIM 文件。

3.  将 **Sources\SxS** 文件夹从 Windows Server 安装媒体复制到步骤 1 中创建的共享文件夹中。

## <a name="methods-of-removing-feature-files"></a><a name=BKMK_methods></a>删除功能文件的方法
在“按需功能”配置中，有两种方法可用来从 Windows Server 删除功能文件。

-   使用 `remove` cmdlet 的参数 `Uninstall-WindowsFeature` ，你可以从运行 Windows Server 2012 R2 或 windows server 2012 (VHD) 的服务器或脱机虚拟硬盘中删除功能文件。 参数的有效值为 `remove` 角色、角色服务和功能的名称。

-   部署映像服务和管理 (DISM) 命令让你创建自定义 WIM 文件，通过删除不需要的或是可从其他远程数据源获取的功能文件，来节省磁盘空间。 有关使用 DISM 准备自定义映像的详细信息，请参阅 [如何启用或禁用 Windows 功能](/previous-versions/windows/it-pro/windows-8.1-and-8/hh824822(v=win.10))。

## <a name="remove-feature-files-by-using-uninstall-windowsfeature"></a><a name=BKMK_remove></a>使用 Uninstall-WindowsFeature 删除功能文件
可以使用 Add-windowsfeature cmdlet 从运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器和脱机 Vhd 中卸载角色、角色服务和功能，并删除功能文件。 如果需要，可以在同一命令中同时卸载和删除相同的角色、角色服务和功能。

> [!IMPORTANT]
> 删除角色、角色服务或功能的功能文件时，依赖于要删除的文件的角色、角色服务和功能也将被删除。 如果你要删除一个角色服务或子功能的功能文件，而父角色或父功能下没有安装其他的角色服务或子功能，那么整个父角色或父功能的文件都将被删除。 若要查看将由 `Uninstall-WindowsFeature -remove` 命令删除的所有功能文件，请将 `whatif` 参数添加到命令，再运行命令并查看结果，无需真正删除功能文件。

#### <a name="to-remove-role-and-feature-files-by-using-uninstall-windowsfeature"></a>使用 Uninstall-WindowsFeature 删除角色和功能文件的步骤

1.  使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。

    > [!NOTE]
    > 如果要从远程服务器中卸载角色和功能，则无需使用提升的用户权限运行 Windows PowerShell。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell****，然后单击“以管理员身份运行”****。

    -   在 Windows 的 "**开始**" 屏幕上，右键单击 "windows PowerShell" 磁贴，然后单击应用栏上的 "以**管理员身份运行**"。

    -   在运行服务器核心安装选项的服务器上，在命令提示符下键入**PowerShell** ，然后按**enter**。

2.  键入以下命令，然后按 Enter****。

    ```
    Uninstall-WindowsFeature -Name <feature_name> -computerName <computer_name> -remove
    ```

    **例如：**“远程桌面授权”是“远程桌面服务”中安装的最后一个角色服务。 此命令卸载“远程桌面授权”，然后从指定的服务器 *contoso_1* 上删除整个“远程桌面服务”角色的功能文件。

    ```
    Uninstall-WindowsFeature -Name rdS-Licensing -computerName contoso_1 -remove
    ```

    **示例：** 在以下示例中，该命令将从脱机 VHD 中删除 active directory 域服务并组策略管理。 首先卸载角色和功能，然后从离线 VHD *Contoso.vhd* 完全删除其功能文件。

    > [!NOTE]
    > `computerName`如果正在运行 Windows 8.1 或 Windows 8 的计算机运行该 cmdlet，则必须添加该参数。
    >
    > 如果从网络共享输入 VHD 文件的名称，则该共享必须向你选择用于装载 VHD 的服务器的计算机帐户授予 "**读取**" 和 "**写入**" 权限。 仅用户帐户访问权限是不够的。 该共享可向 **“所有人”** 组授予 **“读取”** 和 **“写入”** 权限，以允许访问 VHD，但出于安全原因，不建议这样做。

    ```
    Uninstall-WindowsFeature -Name AD-Domain-Services,GPMC -VHD C:\WS2012VHDs\Contoso.vhd -computerName ContosoDC1
    ```

## <a name="see-also"></a>另请参阅
[安装或卸载角色、角色服务或功能](install-or-uninstall-roles-role-services-or-features.md) 
[Windows Server 安装选项](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831786(v=ws.11)) 
[如何启用或禁用 Windows 功能](/previous-versions/windows/it-pro/windows-8.1-and-8/hh824822(v=win.10)) 
[部署映像服务和管理 (DISM) 概述](/previous-versions/windows/it-pro/windows-8.1-and-8/hh825236(v=win.10))