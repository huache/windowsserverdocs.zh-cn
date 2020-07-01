---
title: 从 Windows Server Essentials 转换到 Windows Server 2012 Standard
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 51bcf124-c215-4e9d-9fa8-a90fa2c2fa22
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2477cac206af4e70d10e28d7b1da637b7b7accff
ms.sourcegitcommit: 457e88e5aa6be13a2bffdb8e434a8efc3698678f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548811"
---
# <a name="transition-from-windows-server-essentials-to-windows-server-2012-standard"></a>从 Windows Server Essentials 转换到 Windows Server 2012 Standard

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 Windows Server &reg; 2012 Essentials 支持最多25个用户和50个设备。 当你的业务需求超过限制时，你可以执行从 Windows Server Essentials 到 Windows Server 2012 Standard 的就地许可转换，以保持许可证合规。

## <a name="how-the-transition-affects-user-and-device-limits"></a>转换如何影响用户和设备限制
 过渡到 Windows Server 2012 Standard 后，用户帐户和设备限制将被删除，但 Windows Server Essentials 独有的功能（如仪表板、远程 Web 访问和客户端计算机备份）仍然可用。 但是，由于这些功能在技术上的限制，最多只能支持 75 个用户帐户和 75 台设备。 如果需要添加超过75个用户帐户或设备，则应关闭 Windows Server Essentials 功能并使用 Windows Server 2012 标准本机工具来管理用户帐户和设备。

> [!IMPORTANT]
>   Windows Server 2012 Standard 需要为环境中的每个用户或设备提供客户端访问许可证（CAL）。 这不同于 Windows Server Essentials，后者不使用 CAL 模式，也不包含任何 Cal。  从 Windows Server Essentials 转换到 Windows Server 2012 Standard 时，需要为环境购买适当数量和类型的 Cal （大多数客户购买用户 Cal）。

## <a name="before-the-transition"></a>转换前

-   在从 Windows Server Essentials 转换到 Windows Server 2012 Standard 之前，你应该完全备份服务器数据。

    > [!IMPORTANT]
    >  如果不完整备份服务器数据，则无法将服务器还原到转换前的状态。

-   此外，请确保阅读并了解适用于 Windows Server 2012 Standard 的最终用户许可协议（EULA）。 查看 EULA 的步骤：

    1.  以管理员身份打开命令窗口。

    2.  运行以下命令：

         **dism/online/set-edition： ServerStandard/geteula： eula 路径**

         其中 **eula path** 表示希望用来保存 EULA 文件的位置。 例如，C:\ws8std_eula.rtf。  请务必使用 .rtf 作为文件后缀名。

    3.  打开保存该文件的位置，然后双击打开该文件。

## <a name="transition-to--windows-server-2012-standard"></a>过渡到 Windows Server 2012 标准版
 确定从 Windows Server Essentials 转换到 Windows Server 2012 Standard 后，请完成以下两个步骤：

1. 购买适用于你的环境的 Windows Server 2012 Standard 许可证以及适当数量的用户和/或设备客户端访问许可证。

    你可以从零售输出口、分销商处购买 Windows Server 2012 Standard 的许可证，也可以通过[Microsoft 合作伙伴](https://pinpoint.microsoft.com/SelectCulture.aspx)的帮助。

   > [!NOTE]
   >  如果最初购买 Windows Server 2012 Standard 并执行降级权限，将两个虚拟实例之一安装为 Windows Server Essentials，则无需再购买任何其他产品。
   >
   >  如果通过批量许可渠道购买 Windows Server 2012 Standard，则可以从批量许可服务中心（VLSC）下载 ISO 映像和 Windows Server 2012 Standard 的产品密钥。
   >
   >  如果从所有其他渠道购买 Windows Server 2012 Standard，则可以从[TechNet 评估中心](https://technet.microsoft.com/evalcenter/jj659306.aspx)下载适用于 Windows server ESSENTIALS 的 ISO 映像和评估版产品密钥。 下一步中介绍的转换操作会将评估产品转换为完全授权和受支持的产品。

2. 以管理员身份打开 Windows PowerShell，然后运行如下命令。

    **dism /online /set-edition:ServerStandard /accepteula /productkey:** *产品密钥*

    其中*产品密钥*是 Windows Server 2012 Standard 副本的产品密钥。

    服务器将重新启动，完成转换过程。

   转换后，Windows Server Essentials 功能将保留在服务器上，最多支持75用户和75设备。 如果超出了这两个限制，则应使用 Windows Server 2012 标准本机工具来管理用户帐户和设备。

   此外，在转换到 Windows Server 2012 Standard 后，Windows Server Essentials 的媒体功能将不再可用。 这包括远程 Web 访问的媒体功能和仪表板上的媒体设置。

## <a name="turn-off--windows-server-essentials-features"></a>禁用 Windows Server Essentials 功能
 如果不再需要 Windows Server Essentials 仪表板或其他增值功能来管理服务器，则可以关闭这些功能并将其从服务器中删除。

 "**关闭 Windows Server Essentials 功能向导"：**
 
- 帮助你卸载这些功能。 它还清除 Windows Server Essentials 服务器软件创建的文件服务器。  某些清除操作会立即执行，而某些操作则需要等到服务器重新启动之后才会启动。

- 要求你先手动卸载所有加载项，然后才能完成向导。 若要查看已安装加载项的列表，请在仪表板中打开“应用程序”页。 此向导会通知你是否检测到已安装的加载项，如果有则提醒你卸载这些加载项。

- 允许你选择是否在关闭 Windows Server Essentials 功能后保留客户端计算机的备份文件。

 可以通过两种方法从仪表板运行 "关闭**Windows Server Essentials 功能向导**"：

#### <a name="from-the-alert"></a>通过警报运行

1.  在仪表板中打开“警报查看器”。

2.  在 "组织" 列表中，选择在转换后报告有关关闭 Windows Server Essentials 功能的信息的警报。

3.  在警报中，单击 "关闭**Windows Server Essentials 功能**"。

#### <a name="from-the-get-help-and-support-pane"></a>通过“获取帮助和支持”窗格运行

1. 在主页上单击“获取帮助和支持”。

2. 单击 "关闭**Windows Server Essentials 功能向导**"。

   "关闭**Windows Server Essentials 功能向导**" 执行的某些任务可能不会成功完成。 某些情况下，这可能会阻止仪表板的运行。 如果发生此情况，你可以运行以下文件手动启动该向导：

   **%systemdrive%\Program Files\Windows Server\Bin\TurnOffFeaturesWizard.exe**

## <a name="additional-references"></a>其他参考


-   [转换到 Windows Server 2012 R2 Standard](Transition-from-Windows-Server-2012-R2-Essentials-to-Windows-Server-2012-R2-Standard.md)

-   [将服务器数据迁移到 Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

