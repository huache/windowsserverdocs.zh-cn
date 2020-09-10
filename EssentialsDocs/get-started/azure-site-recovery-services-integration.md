---
title: Azure Site Recovery 服务集成
description: 描述如何使用 Windows Server Essentials
ms.date: 10/01/2016
ms.topic: article
ms.assetid: 262701a6-8a97-4c4e-bfbf-9f8007c308d6
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: aa84ae8f3d11631b76d2e85e6a50f309eb83dd74
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622584"
---
# <a name="azure-site-recovery-services-integration"></a>Azure Site Recovery 服务集成

>适用于： Windows Server 2016 Essentials

[Azure Site Recovery 服务](/azure/site-recovery/) 是 Microsoft Azure 提供的服务，可 (VM) 将虚拟机的实时复制到 Azure 中的备份保管库。 如果你的服务器或站点由于硬件或其他故障而停机，则可以故障转移到 Azure，其中存储在备份保管库中的 VM 映像将设置为 Azure 中正在运行的 VM。 与 Azure 虚拟网络结合使用时，在故障转移到 Azure 时，以前连接到本地服务器的客户端电脑将以透明方式连接到在 Azure 中运行的服务器。

与 Windows Server Essentials 集成 Azure Site Recovery 服务的启动方式与配置 [Azure 虚拟网络](azure-virtual-network-integration.md)的方式相同。 在仪表板中的 " **Microsoft 云服务集成** " 页上，单击 "将 **与 Azure Site Recovery 服务集成** "，使其位于仪表板的右侧：

![在 Windows Server Essentials 仪表板的主页上显示 "入门" 选项卡的屏幕截图。 在 "开始" 选项卡上，已选择 "服务" 部分，仪表板指示 Azure 恢复当前已禁用 Microsoft 云服务集成。](media/azure-site-recovery-1.PNG)

与 Azure 虚拟网络集成和 Azure 备份集成一样，必须使用现有的 Azure 帐户登录到 Azure，或创建新的帐户：

![显示 "启用复制到 Azure" 向导的 "登录到 Microsoft Azure" 页的屏幕截图。 显示 "登录" 按钮，因为用户尚未登录 Microsoft Azure。](media/azure-site-recovery-2.PNG)

成功登录到 Azure 后，你将看到一个屏幕，该屏幕将询问你要与 Azure Site Recovery 服务关联的订阅，以及将存储和托管 VM 的 Azure 区域：

![显示 "启用复制到 Azure" 向导的 "登录到 Microsoft Azure" 页的屏幕截图。 由于用户已登录 Microsoft Azure，此页面提供了用于选择订阅、存储帐户和区域的选项。](media/azure-site-recovery-3.PNG)

订阅和区域选择之后， **Windows Server Essentials 仪表板** 中会出现一个名为 " **Azure 恢复**" 的新选项卡。 在运行 Windows Server Hyper-v 2012 R2 和更) 高版本 (，以及在单个主机下 (来宾) 的虚拟机，可以通过网络扫描来识别和枚举受支持的主机服务器：

![显示 Windows Server Essentials 仪表板的 Azure 恢复页的屏幕截图。 将显示两个 Hyper-v 主机以及这些主机上运行的虚拟机。 已选择主机 RAM 上名为 ramh157v01 的虚拟机-H1-7，并且当前已为此虚拟机禁用了到 Azure 的复制。](media/azure-site-recovery-4.PNG)

### <a name="enabling-guest-virtual-machines-for-protection"></a>启用来宾虚拟机以进行保护

在 Azure 恢复窗口中选择虚拟机后，可以单击仪表板右侧的 " **启用到 azure 的复制** " 来准备并将虚拟机 &trade; 映像复制到 azure：

![显示 "启用到 Azure 的复制" 对话框的屏幕截图。 添加主机时，会显示一个进度栏。](media/azure-site-recovery-5.PNG)

在此过程中，将在主机服务器上安装 Azure Site Recovery Service agent，创建将在其中存储来宾 VM 映像的备份保管库，并开始将映像复制到 Azure。 完成复制过程可能需要数小时或数天，具体取决于要复制的 VM 的大小。 在将整个 VM 映像和最新增量复制到 Azure 之前，故障转移任务不可用并且 VM 不受保护。 完成复制后，Azure 恢复窗口中的 "保护状态" 列将从 " **复制** " 更改为 " **已启用**"：

![显示 Windows Server Essentials 仪表板的 Azure 恢复页的屏幕截图。 将显示两个 Hyper-v 主机以及这些主机上运行的虚拟机。 主机 RAM 上名为 ramh12v02 的虚拟机-H1-2 已选中，并且当前已为此虚拟机启用了到 Azure 的复制。](media/azure-site-recovery-6.PNG)

### <a name="failover-of-a-guest-vm-to-azure"></a>来宾 VM 到 Azure 的故障转移

![显示 "将 VM 故障转移到 Azure" 页的屏幕截图。](media/azure-site-recovery-7.PNG)

当受保护的虚拟机失败或运行受保护虚拟机的主机服务器发生故障时，可以执行故障转移到 Azure，以便在本地虚拟机或主机服务器已修复并且可用之前维持业务连续性。 如上图所示，Azure Site Recovery 服务支持三种类型的故障转移：

-   **测试故障转移** ƒA 良好的灾难恢复计划合并了模拟灾难的功能，以确保在发生真实灾难时最短的停机时间。 测试故障转移使用已复制到恢复保管库的 VM 映像，将其设置为 Azure 中正在运行的虚拟机，并使你能够连接到该服务器以测试适用于业务的方案。 在测试故障转移期间，本地虚拟机将继续运行，而不会中断，因为在灾难恢复测试期间不会中断业务。 测试故障转移完成后，你将通过 Azure 门户停止测试，这会取消预配虚拟机并删除 VHD。 在整个测试故障转移过程中，恢复保管库中的 VM 映像将继续从现场 VM 进行复制，就好像一切都没发生。

-   如果主机服务器上运行的受保护的主机服务器或 VM 发生了实际错误，则会发生**计划外故障转移**ƒAn 计划外故障转移。 故障转移是从 Windows Server Essentials 仪表板中手动触发的，或者如果故障服务器本身是运行 Windows Server Essentials 的服务器，则可直接从 Azure 门户触发。 在这种情况下，非计划的故障转移将使用已复制到恢复保管库的 VM 映像，将其预配为 Azure 中正在运行的虚拟机，并使你能够连接到服务器来测试适用于业务的方案。 在本地还原服务器时，可以从 Azure 门户触发手动故障回复，然后将 VM 映像重新复制到本地服务器。

-   **计划的故障转移** ƒA 计划的故障转移是一项操作，当计划的活动（如 HW 维护）必须发生，这会使服务器停机。 发生计划的故障转移时，会发生与在 Azure 中预配复制的 VM 映像有关的相同过程。 但是，在执行此操作之前，本地服务器将以有序的方式关闭，以确保在关闭之前将所有更改复制到 Azure。 完成计划内维护后，你可以从 Windows Server Essentials 仪表板或 Azure 门户中手动触发故障回复，这会使本地服务器启动，然后在 Azure 中取消预配 VM 并删除。VHD 文件。 从本地 VM 到 Azure 的复制会继续正常进行。

在上述三种情况中，在 VM 故障转移到 Azure 时，Windows Server Essentials 仪表板将显示 Azure 中的新 VM，如下图所示。

![显示 Windows Server Essentials 仪表板的 Azure 恢复页的屏幕截图。 已为名为 Essentials 的主机启用了到 Azure 的复制，在 Azure 中运行的名为 Essentials-Test 的虚拟机指示该主机已故障转移到 Azure。](media/azure-site-recovery-8.PNG)

<a name="see-also"></a>请参阅
--------
[Windows Server Essentials 入门](get-started.md)