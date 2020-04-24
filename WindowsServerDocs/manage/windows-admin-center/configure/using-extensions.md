---
title: 安装和管理扩展
description: 在 Windows Admin Center (Project Honolulu) 中安装和管理扩展
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 2b8a9f5ebab22891b8b97c9c56bba3837cbb9371
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "81269294"
---
# <a name="install-and-manage-extensions"></a>安装和管理扩展

>适用于：Windows Admin Center、Windows Admin Center 预览版

Windows Admin Center 是作为可扩展的平台构建的，其中的每个连接类型和工具都是可以单独安装、卸载和更新的扩展。 可以搜索由 Microsoft 和其他开发者发布的新扩展，单独安装和更新它们，不需更新整个 Windows Admin Center 安装。 也可配置单独的 NuGet 源或文件共享，然后分发在组织内部使用的扩展。

## <a name="installing-an-extension"></a>安装扩展

Windows Admin Center 会显示指定的 NuGet 源提供的扩展。 默认情况下，Windows Admin Center 指向 Microsoft 官方 NuGet 源，其中托管由 Microsoft 和其他开发者发布的扩展。

1. 单击右上角的“设置”按钮，  然后在左窗格中单击“扩展”。  
2. “可用扩展”选项卡会列出源上可供安装的扩展。 
3. 单击某个扩展，在“详细信息”窗格中查看扩展说明、版本、发布者和其他信息。 
4. 单击“安装”，安装某个扩展。  如果网关必须在提升模式下运行才能进行此更改，则会显示 UAC 提升提示。 安装完成后，系统会自动刷新浏览器，并会使用已安装的新扩展重新加载 Windows Admin Center。 如果你尝试安装的扩展是对以前安装的扩展的更新，则可单击“更新到最新”按钮来安装该更新。  也可转到“已安装的扩展”选项卡来查看已安装的扩展，以及查看某个更新在“状态”列中是否可用。  

## <a name="installing-extensions-from-a-different-feed"></a>从另一源安装扩展

Windows Admin Center 支持多个源，你可以一次从多个源查看和管理包。 可以将任何支持 NuGet V2 API 或文件共享的 NuGet 源添加到 Windows Admin Center，方便从其安装扩展。

1. 单击右上角的“设置”按钮，  然后在左窗格中单击“扩展”。 
2. 在右窗格中，单击“源”  选项卡。
3. 单击“添加”按钮以添加另一源。  对于 NuGet 源，请输入 NuGet V2 源 URL。 NuGet 源提供者或管理员应该能够提供 URL 信息。 对于文件共享，请输入在其中存储扩展包文件 (.nupkg) 的文件共享的完整路径。
4. 单击 **“添加”** 。 如果网关必须在提升模式下运行才能进行此更改，则会显示 UAC 提升提示。 仅当在桌面模式下运行 Windows Admin Center 时才会显示此提示。

“可用扩展”列表会显示所有已注册源提供的扩展。  可以使用“包源”列来查看每个扩展来自哪个源。 

## <a name="uninstalling-an-extension"></a>卸载扩展

可以卸载以前安装的任何扩展，甚至可以卸载在安装 Windows Admin Center 过程中预安装的任何工具。

1. 单击右上角的“设置”按钮，  然后在左窗格中单击“扩展”。  
2. 单击“已安装的扩展”选项卡，查看所有已安装的扩展。 
3. 选择要卸载的扩展，然后单击“卸载”  。

卸载完成后，系统会自动刷新浏览器，并会重新加载 Windows Admin Center，删除该扩展。 如果卸载了作为 Windows Admin Center 一部分预安装的工具，该工具会出现在“可用扩展”选项卡中，可供重新安装。 

## <a name="installing-extensions-on-a-computer-without-internet-connectivity"></a>在未连接 Internet 的情况下在计算机上安装扩展

如果 Windows Admin Center 安装在未连接到 Internet 的计算机上或位于代理后面的计算机上，则可能无法访问和安装 Windows Admin Center 源中的扩展。 可以通过手动方式或 PowerShell 脚本方式下载扩展包，并将 Windows Admin Center 配置为从文件共享或本地驱动器检索包。

### <a name="manually-downloading-extension-packages"></a>手动下载扩展包

1. 在另一台具有 Internet 连接的计算机上，打开 Web 浏览器并导航到以下 URL：[https://msft-sme.myget.org/gallery/windows-admin-center-feed](https://msft-sme.myget.org/gallery/windows-admin-center-feed) 

   * 若要查看扩展包，可能需要在 msft-sme.myget.org 上创建一个帐户并登录。

2. 单击要安装的包的名称，查看包详细信息页。
3. 单击包详细信息页的右侧窗格中的“下载”链接，下载该扩展的 .nupkg 文件。 
4. 对所有需要下载的包重复步骤 2 和 3。
5. 将包文件复制到可以从安装了 Windows Admin Center 的计算机访问的某个文件共享，或者复制到计算机的本地磁盘。
6. [按说明从另一源安装扩展](#installing-extensions-from-a-different-feed)。

### <a name="downloading-packages-with-a-powershell-script"></a>通过 PowerShell 脚本下载包

可以使用 Internet 上提供的许多脚本从 NuGet 源下载 NuGet 包。 我们将使用 Microsoft 高级项目经理 [Jon Galloway 提供的脚本](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell)。

1. 如[博客文章](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell)中所述，将脚本作为 NuGet 包安装，或者将脚本复制并粘贴到 PowerShell ISE 中。
2. 将脚本的第一行编辑成你的 NuGet 源的 v2 URL。 如果从 Windows Admin Center 官方源下载包，请使用下面的 URL。

```powershell
$feedUrlBase = "https://aka.ms/sme-extension-feed"
```

3. 运行脚本，脚本会将源中的所有 NuGet 包下载到以下本地文件夹：%USERPROFILE%\Documents\NuGetLocal
4. [按说明从另一源安装扩展](#installing-extensions-from-a-different-feed)。

## <a name="manage-extensions-with-powershell"></a>使用 PowerShell 管理扩展

Windows Admin Center 预览版包含一个用于管理网关扩展的 PowerShell 模块。

[!INCLUDE [ps-extensions](../includes/ps-extensions.md)]

### <a name="learn-more-about-building-an-extension-with-the-windows-admin-center-sdk"></a>[详细了解如何使用 Windows Admin Center SDK 构建扩展](../extend/extensibility-overview.md)。