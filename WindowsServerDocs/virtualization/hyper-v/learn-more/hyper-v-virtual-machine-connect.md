---
title: Hyper-V 虚拟机连接
description: 介绍虚拟机连接，该连接提供对虚拟机的远程访问。 详细介绍如何执行常见任务，例如向虚拟机发送 Ctrl-Alt-Delete。
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: deae35b9-7647-42b8-b6bf-45645a44c9c4
author: KBDAzure
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: fba83d22d9e5d9f31a5809781aa04943cc4cd3af
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364151"
---
# <a name="hyper-v-virtual-machine-connection"></a>Hyper-V 虚拟机连接

>适用于：Windows Server 2016、Windows 10、Windows 8.1、Windows Server 2012 R2、Windows Server 2012、Windows 8

虚拟机连接 \(VMConnect\) 是一种用来与虚拟机进行连接，以便在虚拟机中安装来宾操作系统或与之进行交互的工具。 使用 VMConnect 可执行的部分任务包括：  
  
-   启动和关闭虚拟机  
  
-   连接到 DVD 映像 \(.iso 文件\) 或 USB 闪存驱动器  
  
-   创建检查点  
  
-   修改虚拟机的设置  
    
## <a name="tips-for-using-vmconnect"></a>VMConnect 的使用技巧  
以下信息可能会有助于使用 VMConnect：  
  
|要实现的目的…|执行的操作…|  
|---------------|------------|  
|向虚拟机发送鼠标点击情况或键盘输入|单击虚拟机窗口中的任意位置。 当连接到正在运行的虚拟机时，鼠标指针可能会显示为一个小点。|  
|将鼠标点击情况或键盘输入返回到物理计算机|按 CTRL\+ALT\+向左键，然后将鼠标指针移动到虚拟机窗口的外部。 在 Hyper\-V 管理器的 Hyper\-V 设置中可以更改此鼠标释放组合键。|  
|向虚拟机发送 CTRL\+ALT\+DELETE 组合键|选择“操作” > Ctrl\+Alt\+Delete 或使用组合键 CTRL\+ALT\+END   。|  
|从窗口模式切换到全屏模式|选择“查看” > “全屏模式”   。 若要切换回窗口模式，请按 CTRL\+ALT\+BREAK。|  
|创建用于捕获计算机当前状态的检查点，以进行故障排除|选择“操作” > “检查点”或使用组合键 CTRL\+N   。|  
|更改虚拟机的设置|选择“文件” > “设置”   。|  
|连接到 DVD 映像 \(.iso 文件\) 或虚拟软盘 \(.vfd 文件\)|选择“媒体”  。<br /><br />第二代虚拟机不支持虚拟软盘。 有关详细信息，请参阅[应该在 Hyper-v 中创建第 1 代还是第 2 代虚拟机？](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md)。|  
|在 Hyper\-V 虚拟机上使用主机的本地资源，例如 USB 闪存驱动器|请在 Hyper-V 主机上打开增强会话模式，使用 VMConnect 连接到虚拟机，并在连接之前，选择要使用的本地资源。 有关具体步骤，请参阅[通过 VMConnect 在 Hyper\-V 虚拟机上使用本地资源](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md)。|  
|更改虚拟机已保存的 VMConnect 设置|在 Windows PowerShell 或命令提示符中，运行以下命令：<br /><br />`VMConnect.exe <ServerName> <VMName> \/edit`|  
|阻止 VMConnect 用户接管其他用户的 VMConnect 会话|[在 Hyper-V 主机上打开增强会话模式](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md#turn-on-enhanced-session-mode-on-a-hyper-v-host)。<br /><br />如果未打开增强会话模式，可能会带来安全和隐私风险。 如果一个用户通过 VMConnect 连接并登录到虚拟机，而另一个授权用户连接到同一个虚拟机，则该会话将被第二个用户接管，第一个用户将失去会话。 第二个用户将能够查看第一个用户的桌面、文档和应用程序。|
|管理允许 VM 与 Hyper-V 主机通信的集成服务或组件| 在运行 Windows 10 或 Windows Server 2016 的 Hyper-V 主机上，无法通过 VMConnect 管理集成服务。 请参阅以下主题： <br />- [打开/关闭 Hyper-V 主机上的集成服务](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics) <br />- [打开/关闭 Windows 虚拟机上的集成服务](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#manage-integration-services-from-guest-os-windows)<br />- [打开/关闭 Linux 虚拟机上的集成服务](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#manage-integration-services-from-guest-os-linux) <br />- [更新虚拟机上的集成服务](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#integration-service-maintenance)  <br />对于运行 Windows Server 2012 或 Windows Server 2012 R2 的主机，请参阅[集成服务](https://technet.microsoft.com/library/dn798297(v=ws.11).aspx)。|
|调整 VMConnect 窗口的大小|可以更改运行 Windows 操作系统的第 2 代虚拟机的 VMConnect 窗口的大小。 为此，可能需要在 Hyper-v 主机上打开增强会话模式。 有关详细信息，请参阅[在 Hyper-V 主机上打开增强会话模式](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md#turn-on-enhanced-session-mode-on-a-hyper-v-host)。 对于运行 Ubuntu 的虚拟机，请参阅[在 Hyper-V VM 中更改 Ubuntu 屏幕分辨率](https://blogs.msdn.microsoft.com/virtual_pc_guy/2014/09/19/changing-ubuntu-screen-resolution-in-a-hyper-v-vm/)。|


## <a name="keyboard-shortcuts"></a>键盘快捷方式  
默认情况下，键盘输入和鼠标点击情况将发送到虚拟机。 因此，在使用下列快捷键之前，可能需要按 CTRL + ALT + 向左键。 

|组合键|说明|  
|-------------------|---------------|  
|CTRL\+ALT\+向左键|鼠标释放|  
|CTRL\+ALT\+END|等同于虚拟机中的 CTRL\+ALT\+DELETE|  
|CTRL\+ALT\+BREAK|从全屏模式切换回窗口模式|  
|CTRL\+O|打开虚拟机的设置|  
|CTRL\+S|启动虚拟机|  
|CTRL\+N|创建检查点|  
|CTRL\+E|还原到检查点|  
|CTRL\+C|执行屏幕捕获|  

## <a name="see-also"></a>另请参阅  
-   [通过 VMConnect 在 Hyper-v 虚拟机上使用本地资源](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md)  
-   [Windows Server 2016 上的 Hyper-V](../Hyper-V-on-Windows-Server.md)  
-   [Windows 10 上的 Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/windows_welcome)  
  
  
