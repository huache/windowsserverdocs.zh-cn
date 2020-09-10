---
title: 在迁移模式下安装 Windows Server Essentials
description: 描述如何使用 Windows Server Essentials
ms.date: 04/29/2020
ms.topic: article
ms.assetid: fd7196ac-cfa6-46a5-ba77-6962b47a825e
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.custom:
- CI ID 117135
- CSSTroubleshoot
ms.openlocfilehash: ada3b5fa3b95fa6de45177513b26589c4180696d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622832"
---
# <a name="install-windows-server-essentials-in-migration-mode"></a>在迁移模式下安装 Windows Server Essentials

> 适用于： Windows Server 2012 Essentials

你的网络中只能有一台运行 Windows Server Essentials 的服务器，并且该服务器必须是网络的域控制器。

 在迁移模式下安装 Windows Server Essentials 时，安装向导将执行以下任务：

1.  在目标服务器上安装并配置 Windows Server Essentials 服务器软件。

2.  将域架构更新到最新版本。

3.  将目标服务器加入到现有域中。 在迁移过程完成之前，源服务器和目标服务器都可以是同一个域的成员。 在完成迁移之后，必须在 21 天内从网络中删除源服务器。

    > [!WARNING]
    >  在 21 天的宽限期内，每天都会向事件日志添加一条错误消息，直到从网络中删除源服务器为止。 文本消息显示为：“FSMO 角色检查检测到你环境中的某个条件不符合授权策略。 管理服务器必须包含主域控制器以及域命名主机 Active Directory 角色。 请立即将 Active Directory 角色移到管理服务器。 如果从第一次检测到该条件起 21 天内没有纠正该问题，则该服务器将自动关机。” 在 21 天的宽限期之后，源服务器将关闭。

4.  将操作主机（也称为灵活单主机操作或 FSMO）角色从源服务器转移到目标服务器。 操作主机角色是专门的域控制器任务，在标准数据传输和更新方法不充分时使用。 在目标服务器变成域控制器时，它必须保留操作主机角色。

5.  将目标服务器配置为一台全局编录服务器。 全局编录服务器是管理分布式数据存储库的域控制器。 它包含 Active Directory 林的每个域中每个对象的可搜索的部分表示。

6.  将目标服务器配置为站点授权服务器。

##  <a name="install-windows-server-essentials-on-the-destination-server"></a><a name="BKMK_Install"></a> 在目标服务器上安装 Windows Server Essentials
 若要在迁移模式下在目标服务器上安装并配置 Windows Server Essentials，请执行以下过程。

#### <a name="to-install-windows-server-essentials-on-the-destination-server"></a>在目标服务器上安装 Windows Server Essentials

1. 打开目标服务器并将 Windows Server Essentials DVD1 插入 DVD 驱动器。 如果你看到一条消息，询问你是否要从 CD 或 DVD 启动，请按任意键来执行该操作。

   > [!NOTE]
   >  如果目标服务器支持从 u 盘启动，则可以使用 **windows 7 USB/DVD 下载工具** 从 Windows SERVER Essentials ISO 文件创建可启动的 u 盘。 因为 U 盘读取数据的速度比 DVD-ROM 驱动器要快得多，所以使用 U 盘可以显著加快安装过程。 在创建可启动的 U 盘之后，可以将应答文件添加到 U 盘中。 你可以在 Microsoft Store 网站上免费 [下载 Windows 7 USB/DVD 下载工具](https://go.microsoft.com/fwlink/p/?LinkId=248282) 。

   > [!NOTE]
   >  如果目标服务器不从 DVD 启动，则请重新启动计算机并检查 BIOS 设置，以确保在启动序列中首先列出“DVD-ROM”****。 有关如何更改 BIOS 设置启动序列的详细信息，请参阅硬件制造商提供的文档。

2. 单击“新安装”****。

3. 如果你拥有未显示在列表中的内部硬盘驱动器，则请单击“加载驱动程序”****，并在继续安装之前安装必要的驱动程序。

4. 选中可验证是否将删除主硬盘驱动器上的所有文件和文件夹的复选框，然后单击“安装”****。

5. 在“选择服务器安装模式”**** 页上，单击“服务器迁移”****，然后提供所需的迁移信息。

6. 当“已成功迁移你的服务器”**** 消息出现时，请单击“关闭”****。

   安装完成后，你将通过已在迁移应答文件中提供的管理员用户帐户和密码自动登录。

> [!NOTE]
>  若要在 Windows Server Essentials 安装时解锁桌面，请使用内置管理员帐户并将密码保留为空白。

##  <a name="verify-the-health-of-the-domain-controller"></a><a name="BKMK_VerifyTheHealthOfDC"></a> 验证域控制器的运行状况
 在继续进行迁移之前，应确保域控制器和 Windows Server Essentials 网络正常。

 下表列出了可用于在目标服务器、网络和域中诊断问题的工具：

|工具|说明|
|----------|-----------------|
|Netdiag|帮助隔离网络和连接问题。 如需详细信息和下载，请参阅 [Netdiag](https://go.microsoft.com/fwlink/?LinkId=217388)。|
|Dcdiag.exe|分析林或企业中域控制器的状态，并报告问题以协助进行疑难解答。 如需详细信息和下载，请参阅 [Dcdiag](https://go.microsoft.com/fwlink/?LinkId=217389)。|
|Repadmin.exe|协助诊断域控制器间的复制问题。 此工具需要使用命令行参数才能运行。 如需详细信息和下载，请参阅 [Repadmin](https://go.microsoft.com/fwlink/?LinkId=217387)。|

 应先更正这些工具报告的所有问题，而后才能继续进行迁移。

> [!NOTE]
>  如果你计划将电子邮件迁移到另一个本地 Exchange 服务器，请参阅将 [本地 Exchange server 与 Windows Server Essentials 集成](../manage/Integrate-an-On-Premises-Exchange-Server-with-Windows-Server-Essentials.md) ，了解有关如何设置本地 exchange server 的信息。
