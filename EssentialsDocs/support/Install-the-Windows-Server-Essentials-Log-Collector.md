---
title: 安装 Windows Server Essentials 日志收集器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: d271c54f-1ffa-464e-afa5-27b8df61854e
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: ecffbfd3157720ad2762ba77d528af05e5abf53f
ms.sourcegitcommit: 56ac7cf3f4bbcc5175f140d2df5f37cc42ba76d1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85217537"
---
# <a name="install-the-windows-server-essentials-log-collector"></a>安装 Windows Server Essentials 日志收集器

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

Windows Server Essentials 日志收集器安装向导将日志收集器作为快速启动板外接程序进行安装。 你可以在网络计算机或服务器或者这两者上安装并使用日志收集器。 安装后，日志收集器将显示在仪表板上。  
  
###  <a name="to-install-the-log-collector"></a><a name="BKMK_ToInstall"></a>安装日志收集器  
  
1.  将日志收集器安装包下载到任意服务器或网络中的计算机。  
  
    > [!NOTE]
    > [下载 Windows Server Essentials 日志收集器安装包](https://www.microsoft.com/download/details.aspx?id=34821)。  
  
2.  双击日志收集器图标。  
  
3.  如果你从网络计算机运行安装，请在收到提示时输入服务器管理员凭据。  
  
4.  选择接受 Microsoft 软件许可条款。  
  
5.  若要仅在该服务器上安装日志收集器，请选中 **“仅在服务器上”** 复选框。 若要在所有网络计算机上安装日志收集器，请选中 **“在服务器和网络中的所有计算机上”** 复选框。  
  
6.  单击 **“安装加载项”**。  
  
###  <a name="reinstalling-the-log-collector"></a><a name="BKMK_Reinstall"></a>重新安装日志收集器  
 如果有必要重新安装日志收集器，你必须在服务器和网络中的网络计算机上卸载并重新安装日志收集器。 通过从仪表板卸载服务器上的日志收集器，所有网络计算机都将自动卸载日志收集器。  
  
##### <a name="to-uninstall-and-reinstall-the-log-collector"></a>卸载并重新安装日志收集器  
  
1.  打开“仪表板”。  
  
2.  单击 **“加载项”** 选项卡，从列表中选择 **“日志收集器”**，然后单击 **“卸载”**。

3.  通过执行之前的过程[安装日志收集器的步骤](Install-the-Windows-Server-Essentials-Log-Collector.md#BKMK_ToInstall)中的步骤，下载并安装日志收集器。   
  
### <a name="manually-install-the-log-collector"></a>手动安装日志收集器  
 如果安装向导安装日志收集器失败，则可以使用以下过程在单个计算机上安装日志收集器。  
  
##### <a name="to-manually-install-the-log-collector"></a>手动安装日志收集器的步骤  
  
1.  将下载的安装文件的扩展名从 .wssx 重命名为 .cab。  
  
2.  双击安装文件名。  
  
3.  如果收到提示则单击 **“确定”**。  
  
4.  双击以 ".msi" 结尾的文件名，然后选择要在其中提取它的文件夹。  
  
5.  导航到带有提取的文件的文件夹，并双击安装文件，以使用向导完成安装。
