---
title: 步骤 6：从新的 Windows Server Essentials 网络中降级和删除源服务器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 86244c66-2c5e-488d-adb8-112e1ca3e2e1
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 6c4410cb94f79be291984a92a2b788e3ae984a4f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625422"
---
# <a name="step-6-demote-and-remove-the-source-server-from-the-new-windows-server-essentials-network"></a>步骤 6：从新的 Windows Server Essentials 网络中降级和删除源服务器

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials

完成 Windows Server Essentials 的安装并完成迁移后，必须执行以下任务：

1.  [删除 Active Directory 证书服务](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_ADCS)

2.  [断开直接连接到源服务器的打印机的连接](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_PhysicallyDisconnect)

3.  [对源服务器进行降级](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_DemoteTheSourceServer)

4.  [删除源服务器并重新调整其用途](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md#BKMK_RemoveTheSourceServer)

##  <a name="remove-active-directory-certificate-services"></a><a name="BKMK_ADCS"></a> 删除 Active Directory 的证书服务
 如果你在单个服务器上安装了多个 Active Directory 证书服务 (AD CS) 角色服务，则该步骤会稍有不同。 可以使用以下过程卸载 AD CS 角色服务，并保留其他 AD CS 角色服务。

 若要完成此过程，必须使用与安装证书颁发机构 (CA) 的用户相同的权限进行登录。 如果你要卸载企业 CA，则至少要求具有 Enterprise Admins 中的成员身份或其等效身份，才能完成此过程。

#### <a name="to-remove-ad-cs"></a>删除 AD CS

1.  以域管理员身份登录到目标服务器。

2.  依次单击“开始”****、“管理工具”**** 和“服务器管理器”****。

3.  在“用户帐户控制”**** 对话框中单击“继续”****。

4.  在“角色摘要”**** 部分中，单击“删除角色”****。

5.  在删除角色向导中，单击“下一步”****。

6.  清除“Active Directory 证书服务”**** 复选框，然后单击“下一步”****。

7.  在“确认删除选项”**** 页上，查看信息，然后单击“删除”****。

    > [!NOTE]
    >  如果正在运行 Internet Information Services (IIS)，则在继续下一步之前，系统会提示你停止该服务。 单击“确定”。 

    > [!NOTE]
    >  首先，可能需要删除“证书颁发机构 Web 注册”****（如果已安装）。

8.  删除角色向导完成后，请重新启动服务器以完成卸载过程。

    > [!IMPORTANT]
    >  即使未提示你重新启动服务器，也请执行此操作。

##  <a name="disconnect-printers-that-are-directly-connected-to-the-source-server"></a><a name="BKMK_PhysicallyDisconnect"></a> 断开直接连接到源服务器的打印机的连接
 在降级源服务器之前，请以物理方式断开直接连接到源服务器并通过源服务器共享的所有打印机的连接。 确保不会为已直接连接到源服务器的打印机保留任何 Active Directory 对象。 然后，可以将打印机直接连接到目标服务器并从 Windows Server Essentials 进行共享。

##  <a name="demote-the-source-server"></a><a name="BKMK_DemoteTheSourceServer"></a> 降级源服务器
 在将源服务器从 AD DS 域控制器的角色降级为域成员服务器的角色之前，请确保将组策略设置应用于所有的客户端计算机，如以下过程中所述。

> [!IMPORTANT]
>  更新客户端计算机上的组策略更改时，源服务器和目标服务器必须连接到网络。

#### <a name="to-force-a-group-policy-update-on-a-client-computer"></a>强制执行客户端计算机上的组策略更新

1. 以管理员身份登录到客户端计算机。

2. 以管理员身份打开“命令提示符”窗口。

3. 在命令提示符下，键入 **gpupdate /force**，然后按 Enter。

4. 该过程可能需要注销并重新登录才能完成。 单击“是”  以确认。

   如果要从 Windows Server Essentials 或其早期版本进行迁移，若要降级服务器，请参阅 [删除 Active Directory 域服务](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh472163(v=ws.11))。 在将源服务器添加为工作组的成员并断开它到网络的连接之后，必须将它从目标服务器上的 AD DS 中删除。

   如果要从 Windows Server Essentials 进行迁移，请使用服务器管理器删除 Active Directory 域服务角色，从而使用以下过程降级源服务器上的域控制器：

#### <a name="to-remove-the-source-server-from-active-directory"></a>从 Active Directory 中删除源服务器

1.  在目标服务器上，打开“Active Directory 用户和计算机”****。

2.  在“Active Directory 用户和计算机”**** 导航窗格中，展开域名，然后再展开“计算机”****。

3.  如果源服务器仍存在于服务器列表中，则右键单击源服务器名称，再单击“删除”****，然后单击“是”****。

4.  验证源服务器是否未列出，然后关闭“Active Directory 用户和计算机”****。

##  <a name="remove-and-repurpose-the-source-server"></a><a name="BKMK_RemoveTheSourceServer"></a> 删除源服务器并重新调整其用途
 关闭源服务器并断开它到网络的连接。 我们建议你至少在一周的时间内不要重新格式化源服务器，以确保所有必要的数据都迁移到目标服务器。 在验证所有数据已迁移之后，如有必要，你可以在网络上将此服务器作为辅助服务器进行重新安装，以用于其他任务。

> [!NOTE]
>  降级和删除源服务器后，请重新启动目标服务器。

 降级源服务器后，它将不会处于正常运行状态。 如果你想要调整源服务器的用途，最简单的方法是将其重新格式化、安装服务器操作系统，然后对其进行设置以用作另一台服务器。

## <a name="next-steps"></a>后续步骤
 已从新的 Windows Server Essentials 网络中降级和删除源服务器。 现在，请前往 [步骤7：执行迁移后任务以进行 Windows Server Essentials 迁移](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md)。


若要查看所有步骤，请参阅 [迁移到 Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)。