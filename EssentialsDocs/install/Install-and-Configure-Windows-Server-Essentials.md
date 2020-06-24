---
title: 安装和配置 Windows Server Essentials
description: 描述如何使用 Windows Server Essentials
ms.date: 06/17/2013
ms.prod: windows-server
ms.topic: article
ms.assetid: e95cf219-46a4-4041-bd81-0c4c2a0622cf
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 46ee8e19f50b1bce48bd1e7c773bbd802d85b550
ms.sourcegitcommit: 6d6a0225b1f83b71fcb494b94d666cd5e54c7566
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85267567"
---
# <a name="install-and-configure-windows-server-essentials"></a>安装和配置 Windows Server Essentials

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="BKMK_InstallConfigure"></a>   

 本文档提供有关安装和配置 Windows Server Essentials 的分步说明。 在开始安装之前，请在[安装 Windows Server Essentials 之前](Before-You-Install-Windows-Server-Essentials.md)查看并完成中所述的任务。  

 本文档提供有关安装和配置 Windows Server Essentials 的分步说明。 在开始安装之前，请在[安装 Windows Server Essentials 之前](../install/Before-You-Install-Windows-Server-Essentials.md)查看并完成中所述的任务。  
  
 安装和配置 Windows Server Essentials 的步骤分为两个步骤：  
  

1.  [步骤1：安装 Windows Server Essentials 操作系统](Install-and-Configure-Windows-Server-Essentials.md#BKMK_ManualInstallation)此步骤将操作系统安装到服务器上。  
  
2.  [步骤2：配置 Windows Server Essentials 操作系统](Install-and-Configure-Windows-Server-Essentials.md#BKMK_Step2Configure)在此步骤中，你将提供有关你的公司、域设置和网络管理员的信息，以完成安装。 以下信息说明如何使服务器做好使用准备。  

  
###  <a name="step-1-install-the-windows-server-essentials-operating-system"></a><a name="BKMK_ManualInstallation"></a>步骤1：安装 Windows Server Essentials 操作系统  
  
> [!IMPORTANT]
>  安装操作系统后，在完成[步骤2：配置 Windows Server Essentials 操作系统](#BKMK_Step2Configure)之前，请勿自定义服务器。  
  
 **估计完成时间：** 大约30分钟。  
  
> [!NOTE]
>  完成此过程的预计完成时间基于最低硬件要求。  
  
##### <a name="to-install-the-operating-system"></a>安装操作系统的步骤  
  
1. 使用网络电缆将你的计算机连接到网络。  
  
   > [!IMPORTANT]
   >  在安装过程中，请勿从网络断开计算机连接。 否则可能导致安装失败。  
  
2. 打开计算机，然后将 Windows Server Essentials DVD 插入 DVD 驱动器。  
  
    如果你要执行无人参与安装，请连接包含应答文件的可移动媒体（如软盘或 U 盘）。 你可能无法看到下面的部分或任何安装屏幕，具体取决于应答文件的内容。  
  
3. 重新启动计算机。 当消息 **“按任意键从 CD 或 DVD 启动”** 出现时，请按任意键。  
  
   > [!NOTE]
   >  如果你的计算机不从 DVD 启动，请确保 CD-ROM 驱动器在 BIOS 引导顺序中排在第一位。 有关 BIOS 引导顺序的详细信息，请参阅计算机制造商提供的文档。  
  
4. 选择要安装的 **“语言”**、**“时间和货币格式”** 以及 **“键盘或输入方法”**，然后单击 **“下一步”**。  
  
5. 单击 **“立即安装”**。  
  
6. 在 **“输入产品密钥”** 中输入产品密钥。  
  
7. 阅读 **“许可条款”**。 如果接受，请选中 **“我接受许可条款”** 复选框，然后单击 **“下一步”**。  
  
   > [!NOTE]
   >  如果不选择接受许可条款，安装将无法继续。  
  
8. 在 **“您想进行何种类型的安装”** 中，单击 **“自定义：仅安装 Windows（高级）”**  
  
9. 在 **“要在哪里安装 Windows？”** 中，选择要安装 Windows 操作系统的硬盘驱动器。 检查是否所有内部硬盘驱动器均可用于进行安装。  
  
    > [!IMPORTANT]
    >   Windows Server Essentials 必须安装为 C：卷，并且卷大小必须至少为 60 GB。 建议在操作系统磁盘上创建两个分区，并且不使用 C:（系统分区）存储任何业务数据。  
  
    > [!NOTE]
    >  如果某个硬盘驱动器未列出（例如，串行高级技术附件 (SATA) 硬盘），则必须为该硬盘加载设备驱动程序。 从制造商获取设备驱动程序并将其保存到可移动媒体（如软盘或 U 盘）上。 将可移动媒体连接到你的计算机，然后单击 **“加载驱动程序”**。  
  
     如果你需要删除和/或创建分区，请参阅下列步骤：  
  
    1.  要删除分区，请选择一个分区，单击 **“驱动器选项（高级）”**，然后单击 **“删除”**。 删除系统分区后，按照步骤 **b** 或步骤 **c** 中的说明重新创建一个新的分区。  
  
        > [!NOTE]
        >  单击 **“驱动器选项（高级）”** 后，该选项不会再出现。 在这种情况下，请跳过与驱动器选项相关的步骤部分。  
  
    2.  要从未分区的空间创建分区，请单击要分区的硬盘，单击 **“驱动器选项（高级）”**，单击 **“新建”**，然后在 **“大小”** 文本框中，输入要创建的分区大小。 例如，如果使用 120 千兆字节 (GB) 的建议分区大小，请输入 **122880**，然后单击 **“应用”**。 创建分区后，请单击 **“下一步”**。 安装继续前会格式化分区。  
  
    3.  要使用所有未分区的空间创建分区，请单击要分区的硬盘，单击 **“驱动器选项（高级）”**，单击 **“新建”**，然后单击 **“应用”** 以接受默认分区大小。 创建分区后，请单击 **“下一步”**。 安装继续前会格式化分区。  
  
        > [!IMPORTANT]
        >  完成此步骤后无法将操作系统移到不同的分区。  
  
   在安装过程中，临时文件会复制到计算机上的安装文件夹中，这需要约 30 分钟。 安装 Windows Server Essentials 操作系统后，计算机将重新启动。 现在，你已准备好配置 Windows Server Essentials 操作系统。  
  
###  <a name="step-2-configure-the-windows-server-essentials-operating-system"></a><a name="BKMK_Step2Configure"></a>步骤2：配置 Windows Server Essentials 操作系统  
  
> [!IMPORTANT]
>  如果要从以前版本的 Windows Small Business Server 迁移到 Windows Server Essentials，则必须遵循不同的流程。 有关迁移安装的信息如下所述：  
> 
> - [从 Windows SBS 2003 迁移](../migrate/Migrate-Windows-Small-Business-Server-2003-to-Windows-Server-Essentials.md)  
>   -   [从 Windows SBS 2008 迁移](../migrate/Migrate-Windows-Small-Business-Server-2008-to-Windows-Server-Essentials.md)  
  
 在这一安装阶段，系统会提示回答关于你组织的一些问题。 该信息用于配置操作系统。  
  
> [!IMPORTANT]
>  开始此步骤之前，请确保本地网络适配器已连接到处于打开状态且正常工作的路由器或交换机。  
  
 **估计的完成时间：** 大约 30 分钟。  
  
##### <a name="to-configure-the-operating-system"></a>配置操作系统  
  
1.  在 **“验证日期和时间设置”** 页面上，单击 **“更改日期和时间设置”**，以此为服务器选择日期、时间和时区设置。 完成后，单击“下一步”。   
  
    > [!IMPORTANT]
    >  如果要在虚拟机上安装 Windows Server Essentials，请确保选择与主机操作系统所使用的时区设置相同的时区设置。 如果时区设置不同，服务器安装可能会失败。  
  
2.  在 **“选择服务器安装模式”** 页面上，请执行下列操作之一：  
  
    1.  选择 "**全新安装**" 以设置 Windows Server Essentials 服务器软件的全新安装。  
  
    2.  选择 "**服务器迁移**" 以安装 Windows Server Essentials 并将此服务器加入现有 Windows 域。  
  
3.  在 **“个性化服务器”** 页面上，输入组织名称、内部域名和服务器名称。  
  
    > [!IMPORTANT]
    >  在网络上，服务器名称必须为唯一名称。 完成这一步后不能更改服务器名称或内部域名。  
  
4.  单击“下一步”。  
  
5.  在 **“提供管理员帐户信息”** 页面上，输入新管理员帐户的信息。  
  
    > [!CAUTION]
    >  请勿将网络管理员帐户管理员或网络管理员命名为。 这些帐户名称保留供系统使用。  
  
6.  在 **“提供标准用户帐户信息”** 页面上，输入新标准用户帐户的信息，然后单击 **“下一步”**。  
  
7.  在 **“让服务器自动保持最新状态”** 页面上，选择你希望服务器接收 Windows 更新的方式，然后单击 **“下一步”**。  
  
8.  **“更新和准备服务器”** 页面会显示最终安装过程的进度。 这需要一定的时间才能完成，并且你的计算机会重新启动几次。  
  
9. 服务器最后一次重新启动后，会显示 **“服务器已就绪，可供使用”** 页面。 单击“关闭”。  
  
10. 在 **“开始”** 屏幕上单击仪表板标题，然后在仪表板上，完成 **“主页”** 上的 **“设置我的服务器”** 任务。 Windows Server Essentials 安装完成后，应立即完成这些任务。  
  
> [!NOTE]
>  安装完成后，你会使用安装过程中添加的新管理员帐户自动登录到服务器。 内建管理员帐户密码设置为与新管理员帐户的密码相同，然后内建管理员帐户被禁用。  
  
 在不输入产品密钥的情况下，你可以使用新安装的服务器的时间有限（称为 "评估期"）。 评估期结束后，你必须输入产品密钥才能激活服务器或延长评估期。 你最多可以延长评估期两次。 当你达到评估期所允许的最长天数时，必须使用产品密钥激活服务器。  
  
### <a name="customize-windows-server-essentials"></a>自定义 Windows Server Essentials  
 Windows Server Essentials 仪表板的 "**主页**" 链接到在安装服务器后应立即完成的**设置**任务。 通过执行这些任务，您可以帮助保护存储在服务器上的信息，并启用 Windows Server Essentials 中的可用功能。  
  
 如果你选择不执行这些任务，用户可能无法访问某些网络功能。 若要以后返回这些任务，请返回到 Windows Server Essentials 仪表板**主页**。  
  
 下表定义可显示在设置任务列表中的项目。  
  
|任务|说明
|----------|-----------------|  
|获取其他 Microsoft 产品的更新|单击此任务可访问一个链接，该链接运行的工具可用于指定是否要使用 Microsoft 更新来自动获取 Windows Server Essentials 和其他 Microsoft 产品（如 Office）的更新。  
|添加用户帐户|单击此任务可查看关于添加用户帐户的信息摘要。 提供了运行 **“添加用户帐户向导”** 的链接。 有关详细信息，请参阅[添加用户帐户](../manage/Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Manage1)。  
|添加服务器文件夹|单击此任务可查看关于添加服务器文件夹的信息摘要。 提供了运行 **“添加文件夹向导”** 的链接。 还提供了指向使用服务器文件夹的在线帮助主题的链接。 有关详细信息，请参阅[添加或移动服务器文件夹](../manage/Manage-Server-Folders-in-Windows-Server-Essentials.md#BKMK_5)。 
|设置服务器备份|单击此任务可查看关于使用服务器备份来保护数据的信息摘要。 提供了运行 **“设置服务器备份向导”** 的链接。 有关详细信息，请参阅[设置或自定义服务器备份](../manage/Manage-Server-Backup-in-Windows-Server-Essentials.md#BKMK_1)。 
|设置“随处访问”|单击此任务可查看有关 Windows Server Essentials 中的 "随处访问" 功能的信息摘要。 提供了指向 **“随处访问设置”** 页面的链接。 有关详细信息，请参阅[管理随处访问](../manage/Manage-Anywhere-Access-in-Windows-Server-Essentials.md)。 
|设置电子邮件警报通知|单击此任务可查看关于电子邮件警报通知的信息摘要。 提供了运行 **“设置警报电子邮件通知”** 的链接。 有关详细信息，请参阅[设置警报电子邮件通知](../manage/Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Email)。  
|设置媒体服务器|单击此任务可查看关于使用媒体服务器来共享音乐、视频和图像文件的信息摘要。 提供了指向“媒体设置”  **** 页面的链接。 还提供了指向在线帮助主题的链接，可了解关于媒体服务器的详细信息。 有关详细信息，请参阅[管理数字媒体](../manage/Manage-Digital-Media-in-Windows-Server-Essentials.md)。 
|连接计算机|单击此任务可查看关于如何将网络计算机连接到服务器的信息摘要。 有关详细信息，请参阅[如何将计算机连接到服务器](../use/Get-Connected-in-Windows-Server-Essentials.md#BKMK_9)。
  
## <a name="see-also"></a>请参阅  
  
-   [安装 Windows Server Essentials](Install-Windows-Server-Essentials.md)

