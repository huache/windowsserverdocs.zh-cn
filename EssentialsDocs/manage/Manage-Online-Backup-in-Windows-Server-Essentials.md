---
title: 管理 Windows Server Essentials 中的联机备份
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 95a9f593-fad7-4335-bd4d-c7bb8c033efb
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: fd43b528c9528f531d2de72b0c401358019e2216
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626168"
---
# <a name="manage-online-backup-in-windows-server-essentials"></a>管理 Windows Server Essentials 中的联机备份

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 与 Microsoft Azure 备份集成后，" **联机备份** " 管理页面将出现在 Windows Server Essentials 仪表板中。 **“联机备份”** 页面使执行常见的管理任务成为可能。 联机备份页上的功能包括：

- 下面的子部分页面：

  -   **“联机备份”** 注册服务器以进行联机备份后，此部分将显示当前的备份状态、存储状态和帐户信息。

  -   **受保护文件夹** 此部分列出了服务器上的所有共享文件夹和所有文件历史记录文件夹，以及你已选择在 Azure 中备份的任何其他文件夹。 列表包括每个共享文件夹的文件夹名称、文件夹路径以及状态。

  -   **“备份历史记录”** 本节显示最近的联机备份的列表。 该列表包含操作类型，以及每个备份的时间和状态。

- 具有有关选定的备份作业或还原作业的其他信息的详细信息窗格。

- 包含一组可执行的管理任务的任务窗格。

  作为最佳实践，应备份最重要的业务和用户数据。 例如，你应该备份包含重要数据文件的服务器文件夹。 你还应该备份包含重要信息的网络计算机的文件历史记录。

  在决定要联机备份的数据时，请考虑你想要实现的备份频率和保留策略。 然后查看你的预算并确定可以承受的存储空间量。 根据你的需求平衡成本和存储量，然后配置联机备份以保护尽可能多的重要数据。 有关定价的信息，请参阅 [Azure 备份的定价详细信息](https://azure.microsoft.com/pricing/details/backup/)。

  以下部分介绍可以在 Windows Server Essentials 仪表板中显示的各种联机备份任务。

## <a name="online-backup-tasks-in-the-dashboard"></a>仪表板中的联机备份任务

-   [将证书上载到 Azure Backup 保管库](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)

-   [配置联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)

-   [开始联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_3)

-   [从联机备份中还原文件和文件夹](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_4)

-   [注册此服务器以用于备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)

-   [注销服务器](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_6)

###  <a name="upload-a-certificate-to-the-azure-backup-vault"></a><a name="BKMK_1"></a> 将证书上传到 Azure 备份保管库
 在将 Azure 备份用于 Windows Server Essentials 中的联机备份之前，必须上载公共证书以注册到备份保管库。 证书用于验证代理)  (的 Azure 备份部署，它代表 Microsoft Online Services 订阅所有者来管理与此订阅关联的资源。

> [!NOTE]
>  在上载证书之前，必须完成[注册 Azure 备份服务](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_16)中的过程。

##### <a name="to-upload-a-certificate-to-use-with-the-azure-backup-service"></a>上载用于 Azure 备份服务的证书

1. 使用管理员帐户登录到 Windows Server Essentials 仪表板。

2. 在仪表板的 **“主页”** 页面上，单击 **“联机备份”**。

3. 在 **“联机备份”** 区域中，单击 **“将证书上载到 Azure 备份保管库”**。

    这会在 Azure 管理门户中打开 **恢复服务** 。 如果尚未登录到 Azure，则需要使用 Microsoft 帐户进行登录。

4. 单击你将用于联机备份的备份保管库的名称以打开该备份保管库的“快速启动” **** 页面。

5. 单击 **“管理证书”**。

6. 在 **“管理证书”** 对话框中，粘贴 Windows Server Essentials 生成的公用证书的路径。 若要获得公用证书的路径，请执行以下操作：

   1.  在 Windows Server Essentials 仪表板上，单击 **“联机备份”** 选项卡。

   2.  在 **“联机备份”** 页面上，复制生成的证书的路径。

   3.  切换到 "Azure 管理门户"，然后在 " **管理证书** " 对话框中粘贴该路径，以上载生成的公用证书。

   > [!NOTE]
   >  你还可以使用自己的公共证书。 若要了解需要哪些证书，请在 **“快速启动”** 页面上，单击 **“获取证书”** 链接。

   > [!NOTE]
   >   Azure 需要带有公钥的 x.509 v2 证书。 有关详细信息，请参阅 [管理保管库证书](/previous-versions/azure/dn169036(v=azure.100))。

7. 选择证书后，请单击 **“确定”**（复选标记）。

8. 你将返回到 **“快速启动”** 页。 单击 **“仪表板”**，并验证该证书已成功上载。 成功上载证书后，仪表板显示证书指纹和过期日期。

   完成此过程后，请执行以下操作：

9. 将服务器注册到 Azure 备份服务。 有关详细信息，请参阅[注册此服务器用于备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)。

10. 配置服务器的联机备份。 有关详细信息，请参阅[配置联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)。

###  <a name="configure-online-backup"></a><a name="BKMK_2"></a> 配置联机备份
 向 Azure 备份注册服务器后，可以在 Windows Server Essentials 中配置联机备份设置。

##### <a name="to-configure-online-backup"></a>配置联机备份

1.  从注册你的服务器向导或从 Windows Server Essentials 仪表板的 **“联机备份”** 页面，单击 **“配置联机备份”**。 配置联机备份向导将显示。

2.  在向导的 " **配置联机备份** " 页上，选中要备份到 Azure 备份的每个服务器文件夹的复选框。 清除不希望包括在备份中的每个服务器文件夹的复选框。 若要添加未显示在列表中的文件夹，请单击 **“添加文件夹”**。 当你完成选择时，请单击 **“下一步”**。

    > [!NOTE]
    >  不能选择不在本地服务器上的文件夹，或格式化为 ReFS 的驱动器上的文件夹。

3.  在向导的 **“添加文件历史记录备份”** 页面上，你可以选择包含用于支持文件历史记录功能的网络计算机的文件历史记录备份。 然后单击 **“下一步”** 以继续。

4.  在向导的 **“指定备份计划”** 页面上，配置以下各项，然后单击 **“下一步”** 以继续：

    -   选择或接受一天中你希望运行联机备份的时间。 默认时间是 10:00 PM。 你还可能指定运行第二个备份的时间。

    -   选择或接受你希望运行联机备份的日期。 默认情况下，联机备份从星期一运行至星期五。

5.  在向导的 **“指定备份保留策略”** 页面上，选择你想要保留联机备份的天数，然后单击 **“下一步”**。 默认值为 7 天。 还可以选择保留联机备份 15 或 30 天。

    > [!NOTE]
    >   Azure 备份始终保留你最近的备份。 如果备份目标没有足够可用空间来存储备份，则备份过程将不会成功。 若要避免这种情况，请购买额外的存储空间或缩短数据保留期。 有关定价信息，请参阅 Microsoft Azure 备份的 [定价详细信息](https://azure.microsoft.com/pricing/details/backup/) 。

6.  在向导的 **“选择带宽使用量”** 页面上，如果你想要限制分配到联机备份中的 Internet 带宽量，则选择 **“启用 Internet 带宽的使用”**。 使用页面上的选项来指定允许联机备份在工作时间和非工作时间内使用的 Internet 带宽量。 然后，定义你的工作时间和工作日。

    > [!NOTE]
    >   Azure 备份允许你自定义集成软件在备份或还原信息时使用网络带宽的方式。 使用通常称为 "限制" 的方法，可以控制在特定日期和时间间隔内可供备份和还原过程使用的网络带宽量。 在配置联机备份向导中选择 **“启用 Internet 带宽的使用”** 复选框后，你可以指定应用工作时间带宽限制的工作日和工作时间。 在所有其他时间使用非工作时间限制。 这两个限制的有效带宽范围都是从 256 Kbps 到无限。

7.  联机备份配置完成后，单击 **“关闭”**。

    > [!TIP]
    >  成功地配置备份后，**“联机备份”** 页显示最近的联机备份的状态和由备份保管库使用的存储空间量。 若要查看上一个备份的状态，请单击 **“备份历史记录”**。

###  <a name="start-an-online-backup"></a><a name="BKMK_3"></a> 开始联机备份

> [!NOTE]
>  开始联机备份之前，你必须首先[注册此服务器用于备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)，然后[配置联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)。

##### <a name="to-start-an-online-backup-immediately"></a>立即开始联机备份

1.  以管理员身份登录到仪表板。

2.  在导航栏上，单击 **“联机备份”**。

3.  在 **“联机备份任务”** 窗格中，单击 **“立即开始备份”**。

###  <a name="restore-files-and-folders-from-an-online-backup"></a><a name="BKMK_4"></a> 从联机备份还原文件和文件夹
 还原文件和文件夹向导指导你完成查找、选择和还原已联机备份的文件和文件夹。 当你继续执行向导时，将执行以下任务：

1.  **选择要从中还原文件和文件夹的联机备份**

     当你运行还原文件和文件夹向导时，必须执行的第一个操作是指定你是要从你当前登录到的服务器的联机备份还原文件，还是要从另一台服务器的备份还原文件。

2.  **选择要从中还原文件和文件夹的服务器**

     如果你选择从另一台服务器还原文件和文件夹，则在可用的服务器列表中选择你想要还原的服务器，然后单击 **“下一步”**。

3.  **选择包含要还原的文件和文件夹的卷。**

     联机备份包含对应于备份源服务器上的卷的卷。 选择该卷后，选择从中还原备份的日期和时间，然后单击 **“下一步”**。

4.  **选择要还原的文件和文件夹**

     在向导的 **“选择要还原的项目”** 页面上，可以打开不同的文件夹位置并选择每个要还原的文件或文件夹的复选框。 当你完成选择文件的操作时，请单击 **“下一步”**。

5.  **指定已还原的文件和文件夹的目标位置**

     向导的 **“指定恢复选项”** 页面使你可以指定还原文件和文件夹的位置。 共有两个选项：

    -   **还原到原始位置**。 选择此选项以将文件和文件夹还原到发起备份的确切位置。

    -   **还原到其他位置**。  选择此选项以在服务器上指定还原文件的其他位置。

         在默认安装中，如果具有与还原文件相同名称的文件已在目标位置上存在，则向导将创建原始文件的副本。 此外，更新访问控制列表 (ACL) 以反映当前的文件权限。 可以单击 **“高级”** 自定义默认设置。

6.  **确认还原信息**

     **“确认还原信息”** 页提供了你已指定的还原说明的摘要。 若要继续进行文件还原，必须为你的联机备份帐户键入正确的密码。

###  <a name="register-this-server-for-backup"></a><a name="BKMK_5"></a> 注册此服务器以进行备份
 若要将 Windows Server Essentials 服务器上的文件、文件夹和文件历史记录备份或还原到 Azure 备份，必须先将服务器注册到 Microsoft Azure 备份服务。

> [!NOTE]
>  注册你的服务器之前，必须上载证书以用于将存储联机备份的备份保管库。 有关详细信息，请参阅[将证书上载到 Azure 备份保管库中](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)。

##### <a name="to-register-your-server-with-azure-backup"></a>向 Azure Backup 注册服务器

1.  以管理员身份登录到服务器，然后打开仪表板。

2.  在导航栏上，单击 **“联机备份”**。

3.  在 **“联机备份”** 子节中，单击 **“注册”**。

4.  为你的联机备份选择要用于备份保管库的证书。 默认情况下，选择默认证书；如果要选择其他证书，则使用 **“浏览”**。 然后单击“下一步”  。

5.  按照该向导中的说明创建密码，然后完成注册。

###  <a name="unregister-server"></a><a name="BKMK_6"></a> 注销服务器

> [!CAUTION]
>  如果从 Microsoft Azure 备份服务中注销 Windows Server Essentials 服务器，Azure 备份将不能再备份服务器。 此外，将删除以前已上载的服务器数据。 若要继续联机备份，必须再次注册服务器。

##### <a name="to-unregister-your-server-with-azure-backup"></a>从 Azure Backup 注销服务器

1.  登录到 [Azure 管理门户](https://manage.windowsazure.com)。

2.  单击 **“恢复服务”**。

3.  在 **“恢复服务”** 中，单击备份保管库的名称。

4.  从该保管库的 **“快速启动”** 页面上，单击 **“服务器”**。

5.  选择服务器，单击 **“删除”**，然后在确认提示中单击 **“是”**。

## <a name="related-tasks"></a>相关任务

-   [更改联机备份策略](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_7)

-   [查看联机备份的存储使用情况](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_8)

-   [在联机备份中包括新的文件夹](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_9)

-   [从联机备份策略中删除或排除文件历史记录备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_10)

-   [禁用或重新启用联机服务器备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_11)

-   [停止正在进行的联机服务器备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_12)

-   [查看联机备份状态](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_13)

-   [查看和管理联机备份的警报](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_14)

-   [将联机备份重置为默认设置](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_15)

-   [注册 Azure Backup 服务](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_16)

-   [将 Azure Backup 与 Windows Server Essentials 集成](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_17)

-   [保护 Windows Server Essentials 中的联机备份的文件夹](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_18)

-   [Windows Server Essentials 中的联机备份历史记录](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_19)

###  <a name="change-the-online-backup-policy"></a><a name="BKMK_7"></a> 更改联机备份策略
 通过使用 Windows Server Essentials 仪表板对联机备份策略进行更改很容易。

##### <a name="to-change-the-online-backup-policy"></a>更改联机备份策略

1. 以管理员身份登录到仪表板。

2. 在导航栏上，单击 **“联机备份”**。

3. 在 **“联机备份任务”** 窗格中，单击 **“立即开始备份”**。

4. 按照向导中的说明自定义联机备份策略。

   有关你可以自定义的设置的详细信息，请参阅[配置联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)。

###  <a name="view-online-backup-storage-usage"></a><a name="BKMK_8"></a> 查看联机备份存储使用情况

##### <a name="to-view-the-amount-of-storage-space-that-online-backup-uses"></a>查看联机备份使用的存储空间量

1.  以管理员身份登录到仪表板。

2.  在导航栏上，单击 **“联机备份”**。

3.  在 **“联机备份”** 选项卡上的信息窗格中显示 **“存储状态”**。

###  <a name="include-a-new-folder-in-online-backup"></a><a name="BKMK_9"></a> 在联机备份中包括新的文件夹

##### <a name="to-include-a-new-folder-in-the-online-backup-policy"></a>在联机备份策略中包括新的文件夹

1. 以管理员身份登录到仪表板。

2. 在导航栏上，单击 **“联机备份”**。

3. 在 **“联机备份任务”** 窗格中，单击 **“立即开始备份”**。

4. 在 **“更改或删除备份策略”** 页面上，单击 **“自定义联机备份策略”**。

5. 在 **“配置联机备份”** 页面上，如果要包括的文件夹未出现在列表中，则单击 **“添加文件夹”**。

6. 在 **“添加文件夹”** 窗口中，浏览到并选择要包括在联机备份中的文件夹，然后单击 **“确定”**。

7. 在 **“配置联机备份”** 页面上，根据需要选择要包括的其他文件夹，然后单击 **“下一步”**。

8. 按照向导中的说明完成自定义联机备份策略。

   有关可自定义的其他设置的详细信息，请参阅[配置联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)。

###  <a name="remove-or-exclude-file-history-backups-from-the-online-backup-policy"></a><a name="BKMK_10"></a> 从联机备份策略中删除或排除文件历史记录备份

##### <a name="to-remove-or-exclude-a-folder-from-the-online-backup-policy"></a>从联机备份策略中删除或排除某个文件夹

1.  以管理员身份登录到仪表板。

2.  在导航栏上，单击 **“联机备份”**。

3.  单击 " **受保护的文件夹** " 选项卡。"详细信息" 窗格显示文件夹的列表及其联机备份状态。

4.  选择要从联机备份策略中排除的文件夹，然后在任务窗格中，单击 **“从联机备份中删除文件夹”**。

###  <a name="disable-or-re-enable-online-server-backup"></a><a name="BKMK_11"></a> 禁用或重新启用联机服务器备份
 有关如何使用 Azure 备份来备份或还原服务器数据的说明，请参阅 [为备份注册此服务器](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)。

 有关如何停止使用 Azure 备份来备份或还原服务器数据的说明，请参阅 [注销服务器](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_6)。

###  <a name="stop-an-online-server-backup-in-progress"></a><a name="BKMK_12"></a> 停止正在进行的联机服务器备份

##### <a name="to-stop-an-online-server-backup-in-progress"></a>停止正在进行的联机服务器备份

1.  以管理员身份登录到仪表板。

2.  在导航栏上，单击 **“联机备份”**。

3.  在 **“联机备份任务”** 窗格中，单击 **“立即开始备份”**。

     停止备份后，为 **“备份历史记录”** 列表中的备份显示 **“已取消”** 状态。

###  <a name="view-online-backup-status"></a><a name="BKMK_13"></a> 查看联机备份状态

##### <a name="to-view-the-backup-status"></a>查看备份状态

1.  以管理员身份登录到仪表板。

2.  在导航栏上，单击 **“联机备份”**。

3.  单击 " **备份历史记录** " 选项卡。列表视图显示每个备份作业的状态。 选择备份作业以查看有关该作业的详细信息。

###  <a name="view-and-manage-online-backup-alerts"></a><a name="BKMK_14"></a> 查看和管理联机备份警报
 与许多其他警报一样，Azure 备份的警报显示在警报查看器中。

##### <a name="to-view-online-backup-alerts-in-the-alert-viewer"></a>在警报查看器中查看联机备份警报

1. 打开“仪表板”。

2. 执行下列操作之一：

     Windows Server Essentials：在导航窗格中，单击 "警报" 图标 \( 可能是关键、警告或信息 \) 。 这将打开警报查看器。

     Windows Server Essentials：在 **主页** 上，单击 " **运行状况监视** " 选项卡。

3. 查看与 Azure 备份相关的问题的警报列表。

   有关使用警报查看器或运行状况监视选项卡管理警报的详细信息，请参阅 [管理系统运行状况](Manage-System-Health-in-Windows-Server-Essentials.md)。

###  <a name="reset-online-backup-to-default-settings"></a><a name="BKMK_15"></a> 将联机备份重置为默认设置
 Windows Server Essentials 提供了帮助你配置联机备份的设置的向导。 如果要还原默认设置，则运行 **“配置联机备份”** 任务，并选择 **“删除联机备份策略”** 选项。 然后，再次运行 **“配置联机备份”** 任务。 你之前上载的数据保持不变。

###  <a name="sign-up-for-azure-backup-service"></a><a name="BKMK_16"></a> 注册 Azure 备份服务
 若要准备将 Microsoft Azure 备份与 Windows Server Essentials 集成，你将使用 Microsoft Online Services 帐户登录到 Azure 管理门户，然后创建备份保管库以在 Azure 中存储联机备份。 然后，你将下载 Azure 备份集成模块，并使用下载的文件在 Windows Server Essentials 服务器上安装 Azure 备份外接程序。 如果你没有 Microsoft 帐户，则可以注册免费试用版。

 若要执行此安装，请完成以下任务：

1.  注册 Microsoft Online Services 帐户和备份预览。

2.  创建备份保管库以存储联机备份。

3.  下载 Azure 备份代理。

4.  在服务器上安装 Azure 备份外接程序。

####  <a name="sign-up-for-a-microsoft-online-services-account-and-the-backup-preview"></a><a name="BKMK_SignupforaMicrosoftOnlineServiceAccount"></a> 注册 Microsoft Online Services 帐户和备份预览

1.  登录到 Windows Server Essentials 仪表板。

2.  在仪表板 **“主页”** 页面上，依次单击 **“外接程序”** 类别、**“与 Azure 备份集成”** 和 **“单击以注册 Azure 备份”**。

3.  在 "Azure **恢复服务** " 页上的 " **备份 (预览) ** " 部分中，查看详细信息。

4.  如果你没有 Azure 订阅，请单击 " **免费试用**"，然后按照说明获取 Azure 订阅。

     如果已有 Azure 订阅，请单击网页右上角的 " **门户** " 以前往 azure 管理门户。

5.  在 Azure 管理门户页面上，你将在左窗格中看到 " **恢复服务** "。 这就是你将在其中管理从 Windows Server Essentials 中存储联机备份的备份保管库的位置。

####  <a name="create-a-backup-vault-to-store-online-backups"></a><a name="BKMK_Createabackupvaulttostoreonlinebackups"></a> 创建备份保管库以存储联机备份

1.  从 Windows Server Essentials 服务器上的 Web 浏览器登录到 [Azure 管理门户](https://manage.windowsazure.com)。

2.  在 Azure 管理门户中，依次单击 " **新建**"、" **数据服务**"、" **恢复服务**"、" **备份保管库**" 和 " **快速创建**"。

3.  输入你的备份保管库的名称，选择你希望将备份存储到的区域，然后单击 **“快速创建”**。

     **“恢复服务”** 区域打开时会显示你的新备份保管库。

####  <a name="download-the-azure-backup-agent"></a><a name="BKMK_DownloadtheWindowsAzureBackupAgent"></a> 下载 Azure 备份代理

1.  打开 Windows Server Essentials 仪表板。

2.  在仪表板 **“主页”** 页面上，依次单击 **“开始”** 选项卡、**“外接程序”** 类别、**“与 Azure 备份集成”** 和 **“单击以下载 Azure 备份集成模块”**。

####  <a name="install-the-azure-backup-add-in-on-the-server"></a><a name="BKMK_InstalltheWindowsAzureBackupAddIn"></a> 在服务器上安装 Azure 备份外接程序

1. 使用管理员帐户登录到服务器，然后运行你在上一步中下载的 **“OnlineBackupAddin.wssx”** 文件。

2. 显示 **“软件许可条款”**。 如果你同意条款和条件，则单击 **“接受”** 以继续安装。

3. 在 **“安装外接程序”** 页面上，单击 **“安装外接程序”**。

   > [!NOTE]
   >  你可能需要重新启动服务器，以安装任何必备软件。

    显示 **“安装”** 页。 进度指示器指示安装何时开始并显示安装的进度。 安装完成后，你会收到一条消息，指出 Azure 备份外接程序已成功安装。

4. 单击“完成”。

5. 关闭并重新打开仪表板。

    将新的选项卡 **“联机备份”** 添加到仪表板。 在此选项卡中，你可以注册服务器、配置备份设置，并打开 Azure 管理门户中的 " **恢复服务** " 来管理服务器的备份保管库。

   完成这些步骤后，请执行以下操作：

6. 在 Windows Server Essentials 中，上载用于联机备份的证书。 有关详细信息，请参阅[将证书上载到 Azure 备份保管库中](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)。

7. 向 Azure 备份保管库注册服务器。 有关详细信息，请参阅[注册此服务器用于备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)。

8. 配置服务器的联机备份。 有关详细信息，请参阅[配置联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)。

###  <a name="integrate-azure-backup-with-windows-server-essentials"></a><a name="BKMK_17"></a> 将 Azure Backup 与 Windows Server Essentials 集成
 Microsoft Azure 备份集成模块是 Windows Server Essentials 的一项新功能，可用于将文件和文件夹从服务器加密和备份到 Microsoft 提供的 Azure 托管存储系统。 通过使用 Azure 备份对服务器上的数据进行加密和备份，你可以帮助防止由于火灾、水灾、盗窃或其他灾难引起的关键业务数据的灾难性损失。 使用 Azure 备份来备份服务器数据时，将使用你的密码加密信息，然后将其上传到 Internet 上的安全数据中心。 若要从联机备份访问数据，你必须有一台已由证书进行身份验证的服务器，而且必须提供密码。

 在将服务器与 Azure 备份集成并注册后，你可以配置联机备份设置以执行定期计划的备份。 你还可以随时通过单击联机备份仪表板中的 **“立即启动备份”** 任务启动联机备份。

 联机备份设置涉及以下步骤：

1.  [注册 Azure 备份服务](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_16) -在你注册备份服务后，你将创建备份保管库，下载并安装 Azure 备份集成模块。

2.  [将证书上载到 Azure Backup 保管库](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_1)

3.  [注册此服务器以用于备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_5)

4.  [配置联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md#BKMK_2)

> [!NOTE]
>   Azure 备份使用密码加密文件和文件夹以进行联机备份。 更改加密密码将替换你注册服务器时指定的密码。 密码仅接受 ASCII 编码的字符。

###  <a name="protect-folders-for-online-backup-in-windows-server-essentials"></a><a name="BKMK_18"></a> 保护 Windows Server Essentials 中的联机备份的文件夹
 仪表板的联机备份部分的 **“受保护文件夹”** 子部分中显示服务器上所有共享文件夹的列表。 下表描述列表中包含的信息。

|列|说明|
|------------|-----------------|
|**文件夹名称：**|联机备份中包含的文件夹的名称。<br /><br /> 若要添加或排除文件夹，请运行 **“配置联机备份”** 任务。|
|**文件夹路径：**|文件夹位置。|
|**状态：**|有三种类型的 **受保护**的状态： " **不受保护**" 和 " **未知**"。|

###  <a name="online-backup-history-in-windows-server-essentials"></a><a name="BKMK_19"></a> Windows Server Essentials 中的联机备份历史记录
 仪表板的联机备份部分中的 **“备份历史记录”** 子部分显示最近的联机备份的列表。 你可以使用成功的备份还原文件和文件夹。 下表描述列表中包含的信息。

|列|说明|
|------------|-----------------|
|**运作**|有两种类型的操作 - **“备份”** 和 **“还原”**。|
|**阶段**|这是最新状态的记录时间。|
|**状态：**|状态为 " **成功**"、" **正在进行**"、" **已取消**"、" **警告**" 和 " **失败**"。|

## <a name="additional-references"></a>其他参考

-   [管理备份和还原](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)

-   [管理 Microsoft Online Services](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)

-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)

-   [使用 Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)