---
title: 在 Windows Server 上使用磁盘清理
description: 了解如何使用命令行选项来配置磁盘清理工具 (Cleanmgr.exe) 以自动清除某些文件。
ms.reviewer: cosmosdarwin
author: iangpgh
ms.author: jgerend
manager: daveba
ms.date: 06/20/2019
ms.openlocfilehash: cd7aa3dbb648e5083894f4344ea96ca1c1684aab
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87971164"
---
# <a name="using-disk-cleanup-on-windows-server"></a>在 Windows Server 上使用磁盘清理

> 适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2

磁盘清理工具将清除 Windows Server 环境中不必要的文件。 此工具在 Windows Server 2019 和 Windows Server 2016 上默认可用，但可能需要执行几个手动步骤才能在早期版本的 Windows Server 上启用它。

若要启动磁盘清理工具，请运行 Cleanmgr.exe 命令，或依次选择“启动”、“Windows 管理工具”和“磁盘清理”    。

还可以通过使用 [cleanmgr Windows 命令](../../administration/windows-commands/cleanmgr.md)运行磁盘清理，并使用命令行选项来指定磁盘清理清理某些文件。

## <a name="enable-disk-cleanup-on-an-earlier-version-of-windows-server-by-installing-the-desktop-experience"></a>通过安装桌面体验，在早期版本的 Windows Server 上启用磁盘清理

按照以下步骤操作，使用“添加角色和功能向导”在运行 Windows Server 2012 R2 或更早版本的服务器上安装桌面体验，将同时安装磁盘清理。

1. 如果服务器管理器已经打开，则继续执行下一步。 如果服务器管理器尚未打开，请执行以下任一操作打开它。

   - 在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”  。

   - 转到“开始”并选择“服务器管理器”磁贴  。

1. 在“管理”菜单上，选择“添加角色和功能”   。

1. 在“开始之前”页上，验证你的目标服务器和网络环境是否准备好安装所需的功能  。 选择“下一步”  。

1. 在“选择安装类型”页面上，选择“基于角色或功能的安装”，在单个服务器上安装所有功能   。 选择“下一步”  。

1. 在“选择目标服务器”  页面上，从服务器池中选择一台服务器，或选择脱机 VHD。 选择“下一步”  。

1. 在“选择服务器角色”页上，选择“下一步”   。

1. 在“选择功能”页上，选择“用户界面和基础结构”，然后选择“桌面体验”    。

1. 在“添加桌面体验所需的功能？”中，选择“添加功能”   。

1. 继续安装，然后重新启动系统。

1. 验证“属性”对话框中是否显示“磁盘清理”选项按钮  。

   ![含有“磁盘清理”选项的“磁盘属性”对话框](media/diskpropswcleanup.png)

## <a name="manually-add-disk-cleanup-to-an-earlier-version-of-windows-server"></a>将磁盘清理手动添加到早期版本的 Windows Server

Windows Server 2012 R2 或更早版本中不存在磁盘清理工具 (cleanmgr.exe)，除非安装了桌面体验功能。

若要使用 cleanmgr.exe，请安装前面所述的桌面体验，或复制服务器上已存在的 cleanmgr.exe 和 cleanmgr.exe.mui 两个文件。 使用下表查找适用于你的操作系统的文件。

| 操作系统  | 体系结构  | 文件位置  |
| ----------------- | -------------- | --------------- |
| Windows Server 2008 R2 | 64 位 | C:\Windows\winsxs\amd64_microsoft-windows-cleanmgr_31bf3856ad364e35_6.1.7600.16385_none_c9392808773cd7da\cleanmgr.exe
| Windows Server 2008 R2 | 64 位 | C:\Windows\winsxs\amd64_microsoft-windows-cleanmgr.resources_31bf3856ad364e35_6.1.7600.16385_en-us_b9cb6194b257cc63\cleanmgr.exe.mui |

找到 cleanmgr.exe 并将该文件移动到 %systemroot%\System32  。

找到 cleanmgr.exe.mui 并将该文件移动到 %systemroot%\System32\en-US  。

你现在可以通过从命令提示符运行 Cleanmgr.exe 或单击“开始”并在搜索栏中键入“Cleanmgr”来启动磁盘清理工具   。

要使磁盘清理按钮显示在磁盘的属性对话框中，还需要安装桌面体验功能。

## <a name="additional-references"></a>其他参考

[在 Windows 10 中释放驱动器空间](https://support.microsoft.com/help/12425/windows-10-free-up-drive-space)

[cleanmgr](../../administration/windows-commands/cleanmgr.md)
