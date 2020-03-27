---
title: Windows Server Essentials 中的快速启动板概述
description: 描述如何使用 Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 198d16cb-3d07-4706-be89-ad14a5f7dc47
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 63a161057f7068dcb9e02faa353270f0150200b4
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80310666"
---
# <a name="overview-of-the-launchpad-in-windows-server-essentials"></a>Windows Server Essentials 中的快速启动板概述

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

Windows Server Essentials 快速启动板是一个小应用程序，该快速启动板会在计算机首次连接到服务器时安装在该计算机上。 快速启动板为经过身份验证的用户提供了对 Windows Server Essentials 的主要功能（包括计算机备份、共享文件和媒体）的访问权限。 用户可以从加入域的计算机或未加入域的计算机中访问这些功能。 快速启动板还提供了有关计算机运行状况的实时信息和通知。 管理员可以使用快速启动板访问服务器仪表板，即使计算机未连接到网络也是如此。  
  
 为 Windows Server Essentials 开发了加载项的 OEM 和独立软件供应商 (ISV) 可以使用快速启动板将加载项功能扩展到网络上的计算机。  
  
 以下 Windows 操作系统支持使用 Windows Server Essentials 快速启动板：  
  
- **Windows 8**：所有版本。  
  
- **Windows 7**：所有版本。  
- **Windows 10**：所有版本。 
  
  以下操作系统不支持使用 Windows Server Essentials 快速启动板：  
  
- **其他服务器**：不能在运行 Windows Server 操作系统的任何其他计算机上运行 Windows Server Essentials 快速启动板。  
  
  本主题内容：  
  
- [使用快速启动板](Overview-of-the-Launchpad-in-Windows-Server-Essentials.md#BKMK_Launchpad)  
  
- [将快速启动板用于 Mac 计算机](Overview-of-the-Launchpad-in-Windows-Server-Essentials.md#BKMK_Mac)  
  
##  <a name="use-the-launchpad"></a><a name="BKMK_Launchpad"></a>使用快速启动板  
 以下链接和信息在 Windows Server Essentials 快速启动板上可用。  
  
### <a name="backup"></a>备份  
 单击“备份”以打开计算机的“备份属性”。 在“备份属性”页面上，你可以执行以下操作：  
  
- 启动或停止备份。  
  
- 查看最新备份的状态和详细信息。  
  
- 指定如何在运行备份时管理计算机电源。  
  
  有关如何使用快速启动板备份计算机的信息，请参阅[管理客户端备份](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md)。  
  
### <a name="remote-web-access"></a>远程 Web 访问  
 单击“远程 Web 访问”以将 Web 浏览器打开到远程 Web 访问站点。 远程 Web 访问站点使你能够连接到其他计算机，并通过启用了 Internet 的计算机从办公室中或任何远程位置中访问某些网络资源。 有关远程 Web 访问的详细信息，请参阅[管理远程 Web 访问](Manage-Remote-Web-Access-in-Windows-Server-Essentials.md)。  
  
### <a name="shared-folders"></a>共享文件夹  
 单击“共享文件夹”以将 Windows 资源管理器打开到服务器上共享文件夹的位置。 有关共享文件和文件夹的信息，请参阅[管理服务器文件夹](Manage-Server-Folders-in-Windows-Server-Essentials.md)主题。  
  
### <a name="dashboard"></a>面板  
 单击“仪表板” 以打开用于访问 Windows Server Essentials 仪表板的“登录” 页面。 完成登录后，将打开到服务器仪表板的远程桌面连接。 有关仪表板的详细信息，请参阅[仪表板概述](Overview-of-the-Dashboard-in-Windows-Server-Essentials.md)。  
  
> [!NOTE]
>  若要使用此功能，你必须具有相应的访问权限或登录该服务器的权限。  
  
### <a name="microsoft-office-365"></a>Microsoft Office 365  
 如果用户具有 Office 365 帐户，“Microsoft Office 365” 链接将仅显示在快速启动板上。 单击“Microsoft Office 365” 访问指向 Office 365 资源的其他链接。 有关详细信息，请参阅[使用 Microsoft Office 365 快速入门指南](../use/Quick-Start-Guide-to-Using-Microsoft-Office-365-with-Windows-Server-Essentials.md)。  
  
### <a name="computer-health-alerts"></a>计算机运行状况警报  
 快速启动板上的警报提供了一个有关计算机的即时运行状况的快速状态。 若要查看有关运行状况警报的信息，请单击警报指示器以打开警报查看器。 运行状况警报基于严重性级别显示在查看器中。 最严重的警报显示在列表前面；不太严重的警报显示在列表后面。 有关计算机运行状况警报的详细信息，请参阅[管理系统运行状况](Manage-System-Health-in-Windows-Server-Essentials.md)。  
  
##  <a name="use-the-launchpad-with-a-mac-computer"></a><a name="BKMK_Mac"></a>将快速启动板用于 Mac 计算机  
 可以将运行 Mac OS X®10.5 或更高版本的 Mac®计算机连接到 Windows Server Essentials、Windows Server Essentials 或 Windows Server 2012 R2，或下载并安装连接器软件。 完成安装连接器软件时，你可以选择在启动时自动启动快速启动板。  
  
 快速启动板是一个小应用程序，它为经过身份验证的用户提供了对服务器的主要功能（包括共享文件和媒体、加载项以及远程 Web 访问）的访问权限。 快速启动板还提供了有关计算机运行状况的实时信息和通知。  
  
> [!NOTE]
>  服务器管理员无法使用 Mac 计算机上的快速启动板或远程 Web 访问来打开服务器仪表板和管理该服务器。  
  
### <a name="backup"></a>备份  
 单击“备份”以将“时间机器”设置为备份你的计算机并更改“时间机器”设置。 有关“时间机器”的详细信息，请参阅计算机制造商提供的文档。  
  
### <a name="remote-web-access"></a>远程 Web 访问  
 单击 "**远程 Web 访问**"，将 Web 浏览器打开到远程 Web 访问站点。 远程 Web 访问使你能够使用启用了 Internet 的计算机从任何远程位置访问服务器上的共享文件和文件夹。 你可以上载文件、在基于 Web 的媒体播放上播放音乐和视频、查看图片以及播放幻灯片放映。 有关详细信息，请参阅[使用远程 Web 访问](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md)。  
  
### <a name="shared-folders"></a>共享文件夹  
 单击“共享文件夹”以将查找器打开到服务器上共享文件夹的位置。 有关共享文件和文件夹的信息，请参阅[使用共享文件夹](../use/Use-Shared-Folders-in-Windows-Server-Essentials.md)。  
  
### <a name="computer-health-alerts"></a>计算机运行状况警报  
 快速启动板上的警报提供了一个有关计算机的即时运行状况的快速状态。 若要查看有关运行状况警报的信息，请单击警报指示器以打开警报查看器。 运行状况警报基于严重性级别显示在查看器中。 最严重的警报显示在列表前面。 不太严重的警报显示在列表后面。  
  
## <a name="see-also"></a>另请参阅  
  
-   [连接](../use/Get-Connected-in-Windows-Server-Essentials.md)  
  
-   [使用 Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)  
  
-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)
