---
ms.assetid: c91c7196-ee0d-4856-8cfb-4c38494ccf1f
title: 工作文件夹概述
ms.topic: article
author: JasonGerend
manager: dougkim
ms.author: jgerend
ms.date: 06/15/2020
description: 工作文件夹概述 - Windows Server 中的一个服务器角色，可为用户访问电脑和设备上的工作文件提供一致的方式。
ms.openlocfilehash: d8dcd07cd9a511cd0283030d048dff93ed02d6f1
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036725"
---
# <a name="work-folders-overview"></a>工作文件夹概述

>适用于： Windows Server (半年频道) 、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows 10、Windows 8.1、Windows 7

本主题介绍工作文件夹，这是运行 Windows Server 的文件服务器的一种角色服务，可为用户访问电脑和设备上的工作文件提供一致的方式。

如果要在 Windows 10、Windows 7 或 Android 或 iOS 设备上下载或使用工作文件夹，请参阅以下内容：

- [适用于 Windows 10 的工作文件夹](https://support.microsoft.com/help/12370/windows-10-work-folders)
- [工作文件夹适用于 Windows 7（64 位下载）](https://www.microsoft.com/download/details.aspx?id=42558)
- [工作文件夹适用于 Windows 7（32 位下载）](https://www.microsoft.com/download/details.aspx?id=42559)
- [IOS 工作文件夹](https://itunes.apple.com/app/work-folders/id950878067)
- [适用于 Android 的工作文件夹](https://play.google.com/store/apps/details?id=com.microsoft.workfolders)

## <a name="role-description"></a>角色描述

 使用工作文件夹，除公司电脑外，用户还可以在个人电脑和个人设备上存储工作文件以及访问这些设备上存储的工作文件，通常称为自带设备办公 (BYOD)。 用户可以在方便的位置存储工作文件，随时随地访问这些文件。 通过在集中管理的文件服务器上存储文件，并有选择地指定用户设备策略（如加密和锁屏密码），组织可以维持对公司数据的控制。

 可以使用现有的文件夹重定向、脱机文件和家庭文件夹部署来部署工作文件夹。 工作文件夹将用户文件存储在名为*同步共享*的服务器上的文件夹中。 你可以指定已经包含用户数据的文件夹，这能使你无需迁移服务器和数据或立即淘汰现有的解决方案就能采用工作文件夹。

## <a name="practical-applications"></a>实际的应用程序

 管理员可以使用工作文件夹为用户提供对其工作文件的访问权限，同时对组织的数据保持集中的存储和控制。 工作文件夹的一些特定应用包括：

-   提供从用户的工作和个人计算机和设备对工作文件的单一访问点

-   在脱机时访问工作文件，然后在电脑或设备有 Internet 或 Intranet 连接时与中央文件服务器同步

-   使用现有的文件夹重定向、脱机文件和家庭文件夹部署进行部署

-   使用现有的文件服务器管理技术（例如，文件分类和文件夹配额）管理用户数据

-   指定安全策略，以指示用户的电脑和设备对工作文件夹进行加密，并使用锁屏界面密码

-   通过工作文件夹使用故障转移群集，提供高可用性解决方案

## <a name="important-functionality"></a>重要功能

 工作文件夹包含以下功能。

| 功能 | 可用性 | 说明 |
| ------------------- | ------------------ | ----------------- |
| 服务器管理器中的工作文件夹角色服务 | Windows Server 2019、Windows Server 2016 或 Windows Server 2012 R2 | 文件和存储服务提供了一种设置同步共享（存储用户的工作文件的文件夹）、监视工作文件夹和管理同步共享和用户访问的方式 |
| 工作文件夹 cmdlet | Windows Server 2019、Windows Server 2016 或 Windows Server 2012 R2 | 一个 Windows PowerShell 模块，包含用于管理工作文件夹服务器的全面 cmdlet |
| 工作文件夹与 Windows 的集成 | Windows 10<p> Windows 8.1<p> Windows RT 8.1<p> Windows 7（需要下载） | 工作文件夹在 Windows 计算机中提供以下功能：<p> -   控制面板项，可设置和监视工作文件夹<br />-   文件资源管理器集成，允许轻松访问工作文件夹中的文件<br />-   同步引擎，可与中央文件服务器来回传输文件，并实现电池使用时间和系统性能的最大化 |
| 设备的工作文件夹应用 | Android<p> Apple iPhone 和 iPad® | 一款应用，允许受欢迎的设备访问工作文件夹中的文件 |

## <a name="new-and-changed-functionality"></a>新功能和更改的功能

下表描述了工作文件夹的某些主要变化。

| 特性/功能 | 新功能或更新的功能？ | 说明 |
| ---------------------------- | --------------------- | ----------------- |
| 改进了日志记录 | Windows Server 2019 中的新增项 | 工作文件夹服务器上的事件日志可用于监视同步活动，并识别失败同步会话的用户。 使用 Microsoft Set-syncshare/operation 事件日志中的事件 ID 4020 来确定哪些用户的同步会话失败。 使用 Microsoft Set-syncshare/Reporting 事件日志中的事件 ID 7000 和事件 ID 7001 来监视成功完成上传和下载同步会话的用户。 |
| 性能计数器 | Windows Server 2019 中的新增项 | 添加了以下性能计数器：下载字节数/秒，已上传的字节数/秒，连接的用户，下载的文件数/秒，上传的文件数/秒，具有更改检测、传入请求数/秒和未完成请求的用户。 |
| 提高服务器性能 | 已在 Windows Server 2019 中更新 | 已改进了每个服务器的多个用户的性能。 每台服务器的限制各不相同，具体取决于文件数量和文件改动。 若要确定每个服务器的限制，用户应分阶段添加到服务器。 |
| 按需文件访问 | 添加到 Windows 10 版本1803 | 使您能够查看和访问您的所有文件。 可以控制哪些文件存储在您的 PC 上并可脱机使用。 文件的其余部分始终可见，无需占用电脑空间，但需要连接到工作文件夹文件服务器来访问这些文件。 |
| Azure AD 应用程序代理支持 | 已添加到 Windows 10 版本 1703、Android、iOS | 远程用户可使用 Azure AD 应用程序代理安全访问工作文件夹服务器上的文件。 |
| 更快更改复制 | 在 Windows 10 和 Windows Server 2016 中进行了更新 | 对于 Windows Server 2012 R2，当文件更改同步到工作文件夹服务器上时，不向客户端通知这一更改并等待 10 分钟获取更新。 使用 Windows Server 2016 时，工作文件夹服务器会立即通知 Windows 10 客户端，文件更改会立即同步。 这是 Windows Server 2016 中的新增功能，需要 Windows 10 客户端。 如果你使用的是较旧客户端或工作文件夹服务器为 Windows Server 2012 R2，则客户端将继续每 10 分钟轮询一次更改。 |
| 与 Windows 信息保护 (WIP) 集成 | 已添加到 Windows 10 版本 1607 | 如果管理员部署 WIP，工作文件夹可以通过加密电脑上的数据实施数据保护。 加密使用与企业 ID 关联的密钥，它可以使用受支持的移动设备管理包（例如 Microsoft Intune）远程擦除。 |

## <a name="software-requirements"></a>软件要求

工作文件夹要求在文件服务器和网络基础结构方面符合以下软件要求：

-   一台运行 Windows Server 2019、Windows Server 2016 或 Windows Server 2012 R2 的服务器，用于托管与用户文件的同步共享

-   一个使用 NTFS 文件系统格式化的卷，用于存储用户文件

-   若要强制在 Windows 7 电脑上执行密码策略，则必须使用组策略密码策略。 你还需要从工作文件夹密码策略（如果你使用它们）排除 Windows 7 电脑。

-   为将要托管工作文件夹的每个文件服务器提供一个服务器证书。 这些证书应该来自用户信任的证书颁发机构 (CA) - 最好是公共 CA。

-    (可选) 具有 Windows Server 2012 R2 中的架构扩展的 Active Directory 域服务林，以便在使用多个文件服务器时支持将电脑和设备自动引用到正确的文件服务器。

若要使用户能够通过 Internet 进行同步，还需要满足以下要求：

-   允许用户在组织的反向代理或网关中创建发布规则，以便通过 Internet 访问服务器

-   （可选）提供一个公开注册的域名，并且能够为该域创建其他的公用 DNS 记录

-   （可选）Active Directory 联合身份验证服务 (AD FS) 基础结构（如果使用 AD FS 身份验证）

工作文件夹要求在客户端计算机方面符合以下软件要求：

-   电脑和设备必须运行下列操作系统之一：

    -   Windows 10

    -   Windows 8.1

    -   Windows RT 8.1

    -   Windows 7

    -   Android 4.4 KitKat 及更高版本

    -   iOS 10.2 及更高版本

-   Windows 7 电脑必须运行下列 Windows 版本操作系统之一：

    -   Windows 7 Professional

    -   Windows 7 旗舰版

    -   Windows 7 Enterprise

-   Windows 7 电脑都必须加入到你的组织域中（它们不能加入到工作组）。

-   NTFS 格式化的本地驱动器中有足够的可用空间用于存储工作文件夹中的所有用户文件。此外，如果工作文件夹位于系统驱动器中（默认设置），则还需要额外提供 6 GB 可用空间。 默认情况下，工作文件夹使用以下位置： **%USERPROFILE%\Work Folders**

     但是，在设置过程中，用户可以更改该位置（使用 NTFS 文件系统格式化的 microSD 卡和 USB 驱动器是受支持的位置，不过，如果移除这些驱动器，同步将会停止）。

     默认情况下，单个文件的最大大小为 10 GB。 每个用户的存储没有限制，不过，管理员可以使用文件服务器资源管理器的配额功能来实施配额。

-   工作文件夹不支持回滚客户端虚拟机的虚拟机状态。 但允许使用系统映像备份或其他备份应用从客户端虚拟机内部执行备份和还原操作。

## <a name="work-folders-compared-to-other-sync-technologies"></a>工作文件夹与其他同步技术对比

下表介绍各种 Microsoft 同步技术的定位以及何时使用。

| | 工作文件夹 | 脱机文件 | OneDrive for Business | OneDrive |
| - | ------------------ | ------------------- | -------------------------- | -------------- |
| **技术摘要** | 同步存储在电脑和设备的文件服务器上的文件 | 同步文件，用具有企业网络访问权限（可替换为工作文件夹）的电脑存储在文件服务器中 | 将 Microsoft 365 或 SharePoint 中存储的文件与公司网络内部或外部的 Pc 和设备同步，并提供文档协作功能 | 同步存储在电脑、Mac 计算机和设备的 OneDrive 中的个人文件 |
| **用于为用提供工作文件的访问权限** | 是 | 是 | 是 | 否 |
| **云服务** | 无 | 无 | Microsoft 365 | Microsoft OneDrive |
| **内部网络服务器** | 运行 Windows Server 2012 R2、Windows Server 2016 和 Windows Server 2019 的文件服务器 | 文件服务器 | SharePoint 服务器（可选） | 无 |
| **支持的客户端** | 电脑、iOS、Android | 企业网络中的电脑，或通过 DirectAccess、VPN 或其他远程访问技术连接的电脑 | 电脑、iOS、Android、Windows Phone | 电脑、Mac 计算机、Windows Phone、iOS、Android |

> [!NOTE]
>  除了上表列出的同步技术外，Microsoft 还提供其他复制技术，包括 DFS 复制（用于服务器到服务器复制）和 BranchCache（设计为分支机构 WAN 加速技术）。 有关详细信息，请参阅 [DFS 命名空间和 DFS 复制](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11))和 [BranchCache 概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831696(v=ws.11))

## <a name="server-manager-information"></a>服务器管理器信息

工作文件夹是文件和存储服务角色的一部分。 你可以使用添加角色和功能向导或 `Install-WindowsFeature` cmdlet 安装工作文件夹。 两种方法均能实现以下目标：

-   在服务器管理器中，将**工作文件夹**页添加到**文件和存储服务**中

-   安装 Windows 同步共享服务，由 Windows Server 用于托管同步共享

-   安装 SyncShare Windows PowerShell 模块管理服务器上的工作文件夹

## <a name="interoperability-with-windows-azure-virtual-machines"></a>与 Windows Azure 虚拟机的互操作性

 你可以在 Windows Azure 中的虚拟机上运行 Windows Server 角色服务。 此方案已在 Windows Server 2012 R2、Windows Server 2016 和 Windows Server 2019 中进行了测试。

若要了解如何开始使用 Windows Azure 虚拟机，请访问 [Windows Azure 网站](https://www.windowsazure.com/documentation/services/virtual-machines)。

## <a name="see-also"></a>请参阅

| 内容类型 | 参考 |
| ------------------ | ---------------- |
| **产品评估** | -   适用[于 Android 的工作文件夹–发布](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) (博客文章) <br />-   [适用于 iOS 的工作文件夹 - iPad 应用版本](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)（博客文章）<br />-   [Windows Server 2012 R2 上的工作文件夹简介](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) (博客文章) <br />-   [工作文件夹简介](https://channel9.msdn.com/posts/Introduction-to-Work-Folders) (第9频道视频) <br />-   [工作文件夹测试实验室部署](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) (博客文章) <br />-   [适用于 Windows 7 的工作文件夹](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) (博客文章)  |
| **部署** | -   [设计工作文件夹实现](plan-work-folders.md)<br />-   [部署工作文件夹](deploy-work-folders.md)<br />-   [使用 AD FS 和 Web 应用程序代理部署工作文件夹 (WAP) ](deploy-work-folders-adfs-overview.md)<br />-   [使用 Azure AD 应用程序代理部署工作文件夹](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)<br />- [脱机文件 (CSC) 到工作文件夹迁移指南](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)<br />-   [工作文件夹部署的性能注意事项](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)<br />-   [适用于 Windows 7 (64 位下载) 的工作文件夹 ](https://www.microsoft.com/download/details.aspx?id=42558)<br />-   [适用于 Windows 7 (32 位下载) 的工作文件夹 ](https://www.microsoft.com/download/details.aspx?id=42559) |
| **操作** | -   [工作文件夹 iPad 应用：](https://windows.microsoft.com/windows/work-folders-ipad-faq) 用户的 FAQ () <br />-   [工作文件夹证书管理](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) (博客文章) <br />-   [监视 Windows Server 2012 R2 工作文件夹部署](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) (博客文章) <br />-   [Windows PowerShell 中的 Set-syncshare (工作文件夹) Cmdlet](/powershell/module/syncshare/?view=win10-ps)<br />-   [Windows Server 2012 R2 预览版的存储和文件服务 PowerShell Cmdlet 快速参考卡](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) |
| **疑难解答** | -   [Windows Server 2012 R2 - 使用 IIS 网站和工作文件夹解决端口冲突](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)（博客文章）<br />-   [工作文件夹中的常见错误](https://techcommunity.microsoft.com/t5/storage-at-microsoft/troubleshooting-work-folders-on-windows-client/ba-p/425627) |
| **社区资源** | -   [文件服务和存储论坛](/answers/topics/windows-server-storage.html)<br />-   [Microsoft 文件 Cabinet 博客上的存储团队博客](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)<br />-   [询问目录服务团队博客](/archive/blogs/askds/) |
| **相关技术** | -   [Windows Server 2016 中的存储](../storage.yml)<br>-   [文件和存储服务](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831487(v=ws.11))<br />-   [文件服务器资源管理器](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831701(v=ws.11))<br />-   [文件夹重定向、脱机文件和漫游用户配置文件](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh848267(v=ws.11))<br />-   [BranchCache](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831696(v=ws.11))<br />-   [DFS 命名空间和 DFS 复制](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11)) |