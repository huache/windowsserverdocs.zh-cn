---
title: Use local resources on Hyper-V virtual machine with VMConnect
description: 描述通过 VMConnect 使用本地资源的要求
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: 18eface5-7518-4c6b-9282-93e2e3e87492
author: kbdazure
ms.author: kathydav
ms.date: 12/06/2016
ms.openlocfilehash: dccc4ccf66d457da9dcc2a71ff8d259565fe2714
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860470"
---
# <a name="use-local-resources-on-hyper-v-virtual-machine-with-vmconnect"></a>Use local resources on Hyper-V virtual machine with VMConnect

>适用于：Windows 10、Windows 8.1、Windows Server 2016、Windows Server 2012 R2

通过虚拟机连接 (VMConnect)，可以在虚拟机中使用计算机的本地资源，如可移动 U 盘或打印机。 利用增强会话模式，还可以调整 VMConnect 窗口的大小。 本文介绍如何配置主机，并向虚拟机授予对本地资源的访问权限。

增强会话模式和“类型”剪贴板文本仅适用于运行最新 Windows 操作系统的虚拟机。 \(请参阅下面的[使用本地资源的要求](#requirements-for-using-local-resources)\)。 

对于运行 Ubuntu 的虚拟机，请参阅[在 Hyper-V VM 中更改 Ubuntu 屏幕分辨率](https://blogs.msdn.microsoft.com/virtual_pc_guy/2014/09/19/changing-ubuntu-screen-resolution-in-a-hyper-v-vm/)。 
  
## <a name="turn-on-enhanced-session-mode-on-a-hyper-v-host"></a>在 Hyper-V 主机上打开增强会话模式  
如果 Hyper-V 主机运行的是 Windows 10 或 Windows 8.1，则默认情况下，增强会话模式处于打开状态，因此你可以跳过此步骤并转到下一部分。 但是，如果主机运行的是 Windows Server 2016 或 Windows Server 2012 R2，请先执行此操作。 
  
要打开增强会话模式：

1.  请连接到承载虚拟机的计算机。  
  
2.  在 Hyper-V 管理器中，选择主机的计算机名。  
  
    ![显示左窗格中“Hyper-V 管理器”下列出的主机名的屏幕截图。](media/Hyper-V-HyperVManager-HostNameSelected.png)  
  
3.  选择“Hyper-V 设置”  。  
  
    ![显示右窗格中“操作”下的 Hyper-V 设置选项的屏幕截图。](media/HyperV-ActionsHyperVSettings.png)  
  
4.  在“服务器”  下，选择“增强会话模式策略”  。  
  
    ![显示“安全性”部分下的“增强会话模式策略”选项的屏幕截图。](media/Hyper-V-Settings-ServerEnhancedSessionModePolicy.png)  
  
5.  选中“允许增强会话模式”  复选框。  
  
    ![显示“增强会话模式策略”的“允许增强会话模式”复选框的屏幕截图。](media/Hyper-V-Settings-EnhancedSessionModePolicyCheckBox.png)  
  
6.  在“用户”  下，选择“增强会话模式”  。  
  
    ![显示“用户”部分下的“增强会话模式”选项的屏幕截图。 ](media/Hyper-V-Settings-UserEnhancedSessionMode.png)  
  
7.  选中“允许增强会话模式”  复选框。  
  
8.  单击“确定”  。  
  
## <a name="choose-a-local-resource"></a>选择本地资源

本地资源包括打印机、剪贴板以及运行 VMConnect 的计算机上的本地驱动器。 有关更多详细信息，请参阅下面的[使用本地资源的要求](#requirements-for-using-local-resources)。  
  
要选择本地资源，请执行以下操作：
  
1.  打开 VMConnect。  
  
2.  选择要连接到的虚拟机。  
  
3.  单击“显示选项”  。  
  
    ![调用对话框左下角的“显示”选项的屏幕截图。](media/HyperV-VMConnect-DisplayConfig.png)  
  
4.  选择“本地资源”  。  
  
    ![调用“本地资源”选项卡的屏幕截图。](media/HyperV-VMConnect-DisplayConfig-LocalResources.png)  
  
5.  单击“更多”  。  
  
    ![调用“更多”按钮的屏幕截图。](media/HyperV-VMConnect-DisplayConfig-LocalResourcesMore.png)  
  
6.  选择要在虚拟机上使用的驱动器，然后单击“确定”  。  
  
    ![显示可供选择的本地资源和驱动器的屏幕截图。](media/HyperV-VMConnect-Settings-LocalResourcesDrives.png)  
  
7.  选择“保存我的设置以便在将来连接到此虚拟机”  。  
  
    ![调用复选框以选择此选项的屏幕截图。](media/HyperV-VMConnect-SaveSettings.png)  
  
8.  单击“连接”  。  
  
## <a name="edit-vmconnect-settings"></a>编辑 VMConnect 设置

可以通过在 Windows PowerShell 或命令提示符处运行以下命令，针对 VMConnect 方便地编辑连接设置：  
  
`VMConnect.exe <ServerName> <VMName> /edit`  
  
## <a name="requirements-for-using-local-resources"></a>使用本地资源的要求

为了能够在虚拟机上使用计算机的本地资源，请满足以下要求：  
  
-   Hyper-V 主机必须打开“增强会话模式策略”和“增强会话模式”设置   。  
  
-   使用 VMConnect 的计算机必须运行 Windows 10、Windows 8.1、Windows Server 2016 或 Windows Server 2012 R2。  
  
-   虚拟机必须启用远程桌面服务并将 Windows 10、Windows 8.1、Windows Server 2016 或 Windows Server 2012 R2 作为来宾操作系统进行运行。  
  
如果运行 VMConnect 的计算机和虚拟机均满足要求，则可以使用以下任何本地资源（如果可用）：  
  
-   显示器配置  
  
-   音频
  
-   打印机  
  
-   用于复制和粘贴的剪贴板  
  
-   智能卡  
  
-   USB 设备  
  
-   驱动器  
  
-   支持的即插即用设备  
  
## <a name="why-use-a-computers-local-resources"></a>为什么使用计算机的本地资源？
可能要使用计算机的本地资源执行以下操作：  
  
-   在虚拟机没有网络连接的情况下对虚拟机进行疑难解答。  
  
-   按照使用远程桌面连接 (RDP) 进行复制和粘贴的相同方式，将文件复制并粘贴到虚拟机以及从虚拟机复制并粘贴文件。  
  
-   通过使用智能卡登录到虚拟机。  
  
-   从虚拟机打印到本地打印机。  
  
-   在不使用 RDP 的情况下测试需要 USB 和声音重定向的开发人员应用程序并进行疑难解答。  
  
## <a name="see-also"></a>另请参阅  
[连接到虚拟机](https://technet.microsoft.com/library/cc742407.aspx)  
[是否应在 Hyper-V 中创建第 1 代或第 2 代虚拟机？](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md)



