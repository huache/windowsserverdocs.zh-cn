---
title: 禁用个别重定向文件夹上的脱机文件
description: 如何通过使用文件夹重定向在重定向到网络共享的个别文件夹上禁用脱机文件缓存。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 09/10/2018
ms.localizationpriority: medium
ms.openlocfilehash: 0219c669a52d961cc98d6b0ee16bcbcfbbb78417
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961569"
---
# <a name="disable-offline-files-on-individual-redirected-folders"></a>禁用个别重定向文件夹上的脱机文件

>适用于：Windows 10、Windows 8、Windows 8.1、Windows Server 2019、Windows Server 2016、Windows Server 2012、Windows Server 2012 R2、Windows（半年频道）

本主题介绍如何通过使用文件夹重定向在重定向到网络共享的个别文件夹上禁用脱机文件缓存。 通过执行此操作，可以本地指定要从缓存中排除的文件夹，从而减少同步脱机文件所需的脱机文件缓存大小和时间。

>[!NOTE]
>此主题将介绍一些 Windows PowerShell cmdlet 示例，你可以使用它们来自动执行所述的一些步骤。 有关详细信息，请参阅 [Windows PowerShell 基础知识](/powershell/scripting/getting-started/fundamental/windows-powershell-basics?view=powershell-6)。

## <a name="prerequisites"></a>必备条件

若要禁用特定重定向文件夹的脱机文件缓存，环境必须满足以下先决条件。

- Active Directory 域服务 (AD DS) 域，并且客户端计算机已加入该域。 没有林或域功能级别要求或架构要求。
- 运行 Windows 10、Windows 8.1、Windows 8、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows（半年频道）的客户端计算机。
- 安装了组策略管理的计算机。

## <a name="disabling-offline-files-on-individual-redirected-folders"></a>禁用个别重定向文件夹上的脱机文件

若要禁用特定的重定向文件夹的脱机文件缓存，请使用组策略为适当的组策略对象 (GPO) 启用“请勿自动允许脱机使用特定的重定向文件夹”策略设置  。 将此策略设置配置为“禁用”或“未配置”会允许脱机使用所有重定向文件夹   。

>[!NOTE]
>只有域管理员、企业管理员和组策略创建者所有者组的成员才能创建 GPO。

### <a name="to-disable-offline-files-on-specific-redirected-folders"></a>禁用特定重定向文件夹上的脱机文件

1. 打开“组策略管理”  。
2. 若要选择性地创建新的 GPO，用于指定哪些用户应将已重定向的文件夹排除在脱机可用范围之外，请右键单击相应的域或组织单位 (OU)，然后选择“在此域中创建 GPO 并将其链接在此处”，  。
3. 在控制台树中，右键单击要为其配置文件夹重定向设置的 GPO，然后选择“编辑”  。 此时会显示“组策略管理编辑器”。
4. 在控制台树中的“用户配置”下，依次展开“策略”、“管理模板”、“系统”和“文件夹重定向”      。
5. 右键单击“请勿自动允许脱机使用特定的重定向文件夹”，然后选择“编辑”   。 “请勿自动允许脱机使用特定的重定向文件夹”窗口将出现  。
6. 选择“已启用”  。 在“选项”窗格中，通过选择相应的复选框来选择不应脱机使用的文件夹  。 选择“确定”  。

### <a name="windows-powershell-equivalent-commands"></a>Windows PowerShell 等效命令

以下一个或多个 Windows PowerShell cmdlet 与[禁用个别重定向文件夹上的脱机文件](#disabling-offline-files-on-individual-redirected-folders)中所述过程的功能相同。 在同一行输入每个 cmdlet（即使此处可能因格式限制而出现多行换行）。

此示例将在 contoso.com 域的 MyOu 组织单位中创建名为“脱机文件设置”的新 GPO（LDAP 的可分辨名称为“ou=MyOU,dc=contoso,dc=com”）    。 然后，它将禁用视频重定向文件夹的脱机文件。

```PowerShell
New-GPO -Name "Offline Files Settings" | New-Gplink -Target "ou=MyOu,dc=contoso,dc=com" -LinkEnabled Yes

Set-GPRegistryValue –Name "Offline Files Settings" –Key
"HKCU\Software\Policies\Microsoft\Windows\NetCache\{18989B1D-99B5-455B-841C-AB7C74E4DDFC}" -ValueName DisableFRAdminPinByFolder –Type DWORD –Value 1
```

请参阅下表，了解用于每个重定向文件夹的注册表项名称（文件夹 GUID）的列表。

|重定向文件夹|注册表项名称（文件夹 GUID）|
|---|---|
|AppData(Roaming)|{3EB685DB-65F9-4CF6-A03A-E3EF65729F3D}|
|台式机|{B4BFCC3A-DB2C-424C-B029-7FE99A87C641}|
|“开始”菜单|{625B53C3-AB48-4EC1-BA1F-A1EF4146FC19}|
|文档|{FDD39AD0-238F-46AF-ADB4-6C85480369C7}|
|图片|{33E28130-4E1E-4676-835A-98395C3BC3BB}|
|音乐|{4BD8D571-6D19-48D3-BE97-422220080E43}|
|视频|{18989B1D-99B5-455B-841C-AB7C74E4DDFC}|
|收藏夹|{1777F761-68AD-4D8A-87BD-30B759FA33DD}|
|联系人|{56784854-C6CB-462b-8169-88E350ACB882}|
|下载|{374DE290-123F-4565-9164-39C4925E467B}|
|链接|{BFB9D5E0-C6A9-404C-B2B2-AE6DB6AF4968}|
|搜索|{7D1D3A04-DEBB-4115-95CF-2F29DA2920DA}|
|保存的游戏|{4C5C32FF-BB9D-43B0-B5B4-2D72E54EAAA4}|

## <a name="more-information"></a>详细信息

- [文件夹重定向、脱机文件和漫游用户策略文件概述](folder-redirection-rup-overview.md)
- [部署文件夹重定向和脱机文件](deploy-folder-redirection.md)
