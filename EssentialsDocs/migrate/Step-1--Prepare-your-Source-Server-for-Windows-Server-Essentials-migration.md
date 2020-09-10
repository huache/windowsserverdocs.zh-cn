---
title: 步骤 1：为 Windows Server Essentials 迁移准备源服务器。
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 244c8a06-04c6-4863-8b52-974786455373
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 2be09665c0a2361938226b10be0ef058b8aa0ee6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625505"
---
# <a name="step-1-prepare-your-source-server-for-windows-server-essentials-migration"></a>步骤 1：为 Windows Server Essentials 迁移准备源服务器。

> 适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials

本主题介绍如何备份源服务器、评估源服务器系统运行状况、安装最新的 Service Pack 和修补程序，以及验证网络配置。

## <a name="to-prepare-for-migration"></a>准备迁移的步骤
 完成以下初步步骤，以确保将源服务器上的设置和数据成功迁移到目标服务器。

1.  [备份源服务器](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_BackUpYourSourceServerToPrepareForMigration)

2.  [安装最新的 Service Pack](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_InstallTheMostRecentServicePacksToPrepareForMigration)

3.  [删除 "作为服务登录" 帐户设置](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_DeleteSvcAcctSetting)

4.  [评估源服务器的运行状况](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_EvaluateHealth)

5.  [创建计划以迁移业务线应用程序](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_MigrateLOB)

###  <a name="back-up-your-source-server"></a><a name="BKMK_BackUpYourSourceServerToPrepareForMigration"></a> 备份源服务器
 在开始迁移过程之前，请备份源服务器。 进行备份有助于保护你的数据在迁移过程中出现不可恢复错误的情况下不意外丢失。

##### <a name="to-back-up-the-source-server"></a>备份源服务器

1. 使用下表中的一个资源指导你执行源服务器的完整备份。

2. 验证备份是否成功运行。 要测试备份的完整性，请从备份中选择随机文件，将它们还原到备用位置，然后确认还原后的文件是否与原始文件相同。

   |产品|资源|
   |---|---|
   |Windows Small Business Server 2003|[备份和还原 Windows Small Business Server 2003](/previous-versions/tn-archive/cc875809(v=technet.10))
   |Windows Small Business Server 2008|[备份和还原 Windows Small Business Server 2008 上的数据](https://technet.microsoft.com/library/cc527505\(WS.10\).aspx)
   |Windows Server 2008 Foundation|[备份和恢复](https://technet.microsoft.com/library/cc754097\(WS.10\).aspx)
   |Windows Small Business Server 2011 Essentials|[了解有关设置服务器备份的详细信息](/previous-versions/windows/it-pro/windows-server-essentials-sbs/ff402413(v=ws.11))
   |Windows Small Business Server 2011 Standard|[管理服务器备份](/previous-versions/windows/it-pro/windows-server-essentials-sbs/cc527488(v=ws.11))
   |Windows Server Essentials|[管理 Windows Server Essentials 中的备份和还原](/previous-versions/windows/it-pro/windows-server-essentials-sbs/cc514417(v=msdn.10))

###  <a name="install-the-most-recent-service-packs"></a><a name="BKMK_InstallTheMostRecentServicePacksToPrepareForMigration"></a> 安装最新的 service pack
 在迁移之前，必须在源服务器上安装最新更新和 Service Pack。

###  <a name="delete-the-log-on-as-a-service-account-setting"></a><a name="BKMK_DeleteSvcAcctSetting"></a> 删除 "作为服务登录" 帐户设置
 如果要从 Windows Small Business Server 2003 或 Windows Server 2003 进行迁移，请从组策略中删除“作为服务登录”**** 帐户设置。

##### <a name="to-delete-the-log-on-as-a-service-account-setting"></a>删除 "作为服务登录" 帐户设置

1.  若要打开“组策略管理”**** 工具，请依次单击“开始”****、“控制面板”****、“管理工具”**** 和“组策略管理”****。

2.  右键单击“默认域控制器策略”****，然后单击“编辑”****。

3.  导航到“计算机配置\Windows 设置\安全设置\本地策略\用户权限分配”****。

4.  在详细信息窗格中，双击“作为服务登录”****。

5.  清除“定义这些策略设置”**** 复选框。

6.  删除 \\ \localhost\SYSVOL \\<domainname \>\scripts\SBS_LOGIN_SCRIPT.bat。

###  <a name="evaluate-the-health-of-the-source-server"></a><a name="BKMK_EvaluateHealth"></a> 评估源服务器的运行状况
 请务必在开始迁移之前评估源服务器的运行状况。 使用以下过程以确保更新为最新版本、生成系统运行状况报告，并运行 Windows Server 解决方案最佳做法分析器 (BPA)。

#### <a name="download-and-install-critical-and-security-updates"></a>下载并安装重要更新和安全更新
 在源服务器上安装重要更新和安全更新有助于确保迁移成功，而且有助于在迁移过程中保护你的网络。

###### <a name="to-check-for-the-latest-updates"></a>检查最新更新

1.  在源服务器上，依次单击“开始”****、“所有程序”****，然后单击“Windows Update”****。

2.  单击“检查更新”****。

3.  如果找到更新，则请单击“安装更新”****。

#### <a name="run-the-best-practices-analyzer"></a>运行最佳做法分析器
 在开始执行迁移过程之前，你可以运行最佳做法分析器 (BPA) 来验证服务器、网络或域上不存在任何问题。 BPA 从以下来源收集配置信息：

-   Active Directory Windows Management Instrumentation (WMI)

-   注册表

-   Internet 信息服务 (IIS)

###### <a name="to-use-the-bpa-to-analyze-your-source-server"></a>使用 BPA 来分析源服务器

1. 下表提供了到 Microsoft 下载中心的链接，可以从其中下载和安装适用于源服务器的最佳做法分析器 (BPA)。


   |             如果源服务器正在运行             |                                                     你可以从中获取 BPA 工具                                                      |
   |----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
   |                     Windows SBS 2003                     | [Microsoft Windows Small Business Server 2003 最佳做法分析器网站](https://www.microsoft.com/download/details.aspx?id=5334) |
   |                     Windows SBS 2008                     | [Microsoft Windows Small Business Server 2008 最佳做法分析器网站](https://www.microsoft.com/download/details.aspx?id=6231) |
   | Windows SBS 2011 Essentials 或 Windows SBS 2011 Standard |          [Windows Server 解决方案最佳做法分析器网站](https://www.microsoft.com/download/details.aspx?id=15556)           |
   |     Windows Server Essentials 或 Windows Server 2012     |                                                          服务器仪表板                                                           |


2. 下载完毕后，单击“开始”****、指向“所有程序”****，然后单击“SBS 最佳做法分析器工具”****。

   > [!NOTE]
   >  在扫描服务器之前检查更新。

3. 在导航窗格中，单击“启动扫描”****。

    如果源服务器运行的是 Windows Server Essentials，请执行以下操作：

   1.  以管理员身份登录到目标服务器，然后打开仪表板。

   2.  在仪表板上单击“设备”**** 选项卡。

   3.  在 "<**服务器**  > **任务**" 窗格中，单击 "**最佳做法分析器**"。

4. 在详细信息窗格中，键入扫描标签，然后单击“开始扫描”****。 扫描标签是指扫描报告名称，例如 **SBS BPA Scan 1Jul2013**。

5. 扫描完毕后，单击“查看该最佳实践扫描的报告”****。

   在 BPA 工具收集有关服务器配置的信息后，它将验证信息是否正确，然后向管理员提供信息和问题（按严重性排序）的列表。 该列表描述每个问题并提供建议或可能的解决方案。 可以使用三种报告类型：

|报告类型|说明
|-----------------|-----------------
|列表报告|在一维列表中显示报告。
|目录树报告|在分层列表中显示报告。

要查看某个问题的描述和解决方案，请在报告中单击该问题。 并非 BPA 报告的所有问题都会对迁移造成影响，但应尽可能多地解决问题以确保迁移成功。

####  <a name="synchronize-the-source-server-time-with-an-external-time-source"></a><a name="BKMK_SynchronizeTheSourceServerTimeWithAnExternalTimeSource"></a> 将源服务器时间与外部时间源同步
 源服务器上的时间与目标服务器上的时间差异必须设置为在 5 分钟之内，并且两个服务器上的日期和时区必须相同。 如果源服务器正在虚拟机中运行，则主机服务器上的日期、时间和时区必须与源服务器和目标服务器上日期、时间和时区匹配。 为了帮助确保成功安装 Windows Server Essentials，必须将源服务器时间与 Internet 上的网络时间协议 (NTP) 服务器同步。

###### <a name="to-synchronize-the-source-server-time-with-the-ntp-server"></a>将源服务器时间与 NTP 服务器同步的步骤

1.  使用域管理员帐户和密码登录源服务器。

2.  依次单击“开始”****、“运行”****，在文本框框中键入 **cmd**，然后按 Enter 键。

3.  在命令提示符下，键入 w32tm /config /syncfromflags:domhier /reliable:no /update，然后按 Enter 键。

4.  在命令提示符下，键入 net stop w32time，然后按 ENTER。

5.  在命令提示符下，键入 net start w32time，然后按 ENTER。

> [!IMPORTANT]
>  在 Windows Server Essentials 安装过程中，你有机会验证目标服务器上的时间并根据需要对其进行更改。 确保目标服务器时间与源服务器上设置的时间的差距在五分钟之内。 当安装完成后，目标服务器将与 NTP 同步。 所有加入域的计算机（包括源服务器）均与目标服务器同步，目标服务器承担了主域控制器 (PDC) 仿真器主机的角色。

###  <a name="create-a-plan-to-migrate-line-of-business-applications"></a><a name="BKMK_MigrateLOB"></a> 创建计划以迁移业务线应用程序
 业务线 (LOB) 应用程序是运转企业的关键计算机应用程序。 LOB 应用程序包括会计、供应链管理和资源计划应用程序。

 在你计划迁移 LOB 应用程序时，请咨询 LOB 应用程序提供商来确定迁移每个应用程序的适当方法。 你还必须找到用于在目标服务器上安装 LOB 应用程序的介质。

> [!NOTE]
>  如果使用 Windows Small Business Server 2011 Essentials SDK 开发自定义的系统运行状况或警报加载项，并且希望继续将该加载项用于 Windows Server Essentials，则还必须更新外接程序并将其部署到目标服务器。


### <a name="create-a-plan-to-migrate-email-hosted-on-windows-sbs-2011-windows-sbs-2008-and-windows-sbs-2003"></a>创建计划以迁移 Windows SBS 2011、Windows SBS 2008 和 Windows SBS 2003 上托管的电子邮件
 在 Windows SBS 2011、Windows SBS 2008 和 Windows SBS 2003 中，电子邮件通过 Microsoft Exchange Server 提供。 但是，Windows Server Essentials 不提供收件箱电子邮件服务。 如果当前正在使用运行 Windows SBS 2011、Windows SBS 2008 或 Windows SBS 2003 的服务器来托管公司的电子邮件，则需要迁移到备用的本地或托管解决方案。

> [!NOTE]
>  在更新并准备好源服务器进行迁移之后，建议在继续进行迁移过程之前创建已更新服务器的备份。

#### <a name="migrate-email-to-microsoft-365"></a>将电子邮件迁移到 Microsoft 365
 如果已选择使用 Microsoft 365 作为域的电子邮件解决方案，请按照将 [所有邮箱迁移到云中](https://help.outlook.com/140/ms.exch.ecp.emailmigrationwizardexchangelearnmore.aspx) 的指导进行操作，并使用转换 Exchange 迁移开始电子邮件迁移以 Microsoft 365。 建议你在安装 Windows Server Essentials 之前完成电子邮件迁移。

> [!NOTE]
>  如果打算将 Windows Server Essentials 与 Microsoft 365 集成，则必须在源服务器上删除本地 Exchange Server 的步骤。 有关如何将 Exchange Server 公用文件夹迁移到 Microsoft 365 的信息，请参阅博客文章 [适用于 Microsoft 365 的 Microsoft Exchange 2013 公用文件夹迁移脚本](/archive/blogs/fmustafa/microsoft-exchange-2013-public-folders-migration-scripts-for-office-365)。
>
>  完成安装后，应通过运行 " **与 Microsoft 365 集成** " 任务来打开 Windows Server Essentials 中的 Microsoft 365 集成功能。

> [!IMPORTANT]
>  若要允许 Microsoft 365 迁移工具连接到在源服务器上运行的 Exchange Server，必须在源服务器上通过 HTTP 启用 RPC。 有关如何通过 HTTP 启用 RPC 的信息，请参阅 [如何在 Small Business Server 2003（Standard 或 Premium）中首次通过 HTTP 部署 RPC](/previous-versions/tn-archive/bb123622(v=exchg.65))。 如果在启用 RPC over HTTP 后无法成功运行 Microsoft 365 迁移工具，请在 HKEY_LOCAL_MACHINE \Software\Microsoft\Rpc\RpcProxy 的注册表中查看 **ValidPorts** 设置，并确保列出源服务器的完全限定域名 (FQDN) 。 如果未列出 FQDN，请使用以下示例进行手动添加：
>
>  remote. *contoso*.com:6001-6002;remote. *contoso*.com:6004（使用你的域名替换 *contoso*）

#### <a name="migrate-email-to-another-on-premises-exchange-server"></a>将电子邮件迁移到另一个本地 Exchange Server
 有关如何将电子邮件迁移到另一个本地 Exchange Server 的信息，请参阅将 [本地 Exchange server 与 Windows Server Essentials 集成](/previous-versions/windows/it-pro/windows-server-essentials-sbs/jj200172(v=ws.11))。 建议你在安装 Windows Server Essentials 后设置新的本地 Exchange Server，并在降级源服务器前完成电子邮件迁移。

> [!NOTE]
>  Exchange Server 不包括 Windows Small Business Server POP3 连接器。 在将电子邮件数据迁移到另一个 Exchange Server 之后，你将无法再使用 POP3 连接器功能。

> [!NOTE]
>  在更新并准备好用于迁移的源服务器后，你应该先为更新后的服务器创建备份，然后再继续执行迁移过程。

## <a name="next-steps"></a>后续步骤
 你已准备好将源服务器迁移到 Windows Server Essentials。  现在，请执行 [步骤2：将 Windows Server Essentials 安装为新的副本域控制器](Step-2--Install-Windows-Server-Essentials-as-a-new-replica-domain-controller.md)。

若要查看所有步骤，请参阅 [迁移到 Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)。