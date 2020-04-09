---
title: Azure 虚拟网络集成
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: d7d38505-cff5-4f15-9fd5-ae6dba15ce88
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d79530b2c4bfb71b23fa984731d624f30e9a3ef6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815210"
---
# <a name="azure-virtual-network-integration"></a>Azure 虚拟网络集成

>适用于： Windows Server 2016 Essentials

随着组织做出云计算的方式，他们很少会一次移动其所有资源100%，而是采取一种方法，其中某些资源在云中，一些资源仍在本地。 利用这种混合方法，组织不仅可以将一些计算资源转移到云，而且还能使其在无需购买新硬件的情况下增长其 IT 基础结构。

实现这种混合方法以进行计算时，需要在两个位置中的资源之间进行无缝的方法来相互通信。 Azure 虚拟网络是一项 Azure 服务，使组织能够创建点到点（P2P）或站点到站点（S2S）虚拟专用网络，使在 Azure 中运行的资源（例如虚拟机和存储）看起来像是用于无缝应用程序和资源访问的本地网络。

Azure 虚拟网络的配置可能很复杂。 使用 Windows Server Essentials 2016，你可以通过一个简单的向导轻松地配置 Azure 虚拟网络，此向导可帮助你为网络环境选择最适合的默认值。 如以下屏幕截图所示，已将新的 Azure 虚拟网络集成任务添加到 Windows Essentials 仪表板的 "Microsoft 云服务" 部分，以引入 Azure 虚拟网络，并提供快速链接来启动集成.

![在 Windows Server Essentials 仪表板的主页上显示 "入门" 选项卡的屏幕截图。 在 "开始" 选项卡上，已选择 "服务" 部分，仪表板指示 Azure 虚拟网络当前已禁用 Microsoft 云服务集成。](media/azure-virtual-network-1.PNG)

单击上面屏幕截图中的 "**立即集成**" 链接时，将出现一个对话框，要求你登录到 Microsoft Azure 帐户。 如果你没有 Microsoft Azure 帐户，你可以在此屏幕上注册一个帐户，这会将你重定向到 Azure 帐户注册门户：

![显示 "与 Azure 虚拟网络集成" 向导的 "登录到 Microsoft Azure" 页的屏幕截图。](media/azure-virtual-network-2.PNG)

登录到 Azure 后，你将看到一个选项，用于选择要与 Azure 虚拟网络服务关联的订阅：

![显示 "与 Azure 虚拟网络集成" 向导的 "我的 Microsoft Azure 订阅" 页面的屏幕截图。](media/azure-virtual-network-3.PNG)

选择要用于 Azure 虚拟网络的 Azure 订阅后，你将看到用于创建新的 Azure 虚拟网络的选项，或者，如果已在此订阅中设置了此项，则下拉框将显示 "可用"。 你还将为 Azure 虚拟网络将用于识别本地网络中的资源的本地网络选择一个名称。 最后，选择要在其中托管 Azure 虚拟网络的 Azure 区域。 选择物理上离本地网络最近的位置通常最适合用于优化带宽速度，以便与可能在其 Azure 服务中托管的资源进行通信：

![显示 "与 Azure 虚拟网络集成" 向导的 "设置 Azure 虚拟网络" 页的屏幕截图。](media/azure-virtual-network-4.PNG)

集成过程的最后一步是设置将用于 S2S VPN 连接的 VPN 设备。 由于大多数小型企业在其环境中只有几个服务器，并且缺少 IT 人员来正确配置 VPN 路由器以连接到 Microsoft Azure，因此默认选择是将 Windows Server Essentials 服务器设置为 VPN 服务器，该服务器的资源在本地网络中，将连接到，以便访问 Azure 虚拟网络中的资源。 但是，如果您想要在您的环境中使用另一个服务器作为 VPN 服务器，或者您要使用 VPN 路由器，则可以选择这些选项。

由于路由器类型和型号的变化，Windows Server Essentials 不会尝试自动配置 VPN 路由器。 选择此集成向导中的 VPN 路由器仅会通知设备类型的 Azure 虚拟网络，以便在 Azure 中进行连接时所需的相应路由配置。

完成集成向导后，Azure 虚拟网络的 Windows Server Essentials 仪表板中将显示一个新选项卡：

![显示 Windows Server Essentials 仪表板的 Azure VNet 页的屏幕截图。 选择 "Azure 虚拟网络" 选项卡，并将状态显示为 "正在配置"。](media/azure-virtual-network-5.PNG)

>!请注意，在云中完成 Azure 虚拟网络的配置可能需要很长时间，并且可能会长达30分钟。 在此期间，配置的状态将显示在仪表板的 "Azure 虚拟网络状态" 页中。

Azure 虚拟网络的配置完成后，状态将更改为 "已连接"，并显示 Azure 虚拟网络的详细信息，例如 "传入/传出"、"网关 IP 地址"、"本地 IP 地址" 和 "帐户详细信息"：

![显示 Windows Server Essentials 仪表板的 Azure VNet 页的屏幕截图。 选择 "Azure 虚拟网络" 选项卡，并将状态显示为 "已连接"，并且在此状态信息下会显示虚拟网络的详细信息。](media/azure-virtual-network-6.PNG)

在仪表板右侧的 "任务" 窗格中，你可以使用 Azure 虚拟网络进行各种任务。

-   **从 AZURE VNET 断开连接**设置 Azure 虚拟网络是免费的，但对于连接到本地的 VPN 网关和 Azure 中的其他 Vnet，会收取费用。 从 Azure VNET 断开连接将停止所有计费。

-   **切换 VPN 设备**如果要将 VPN 服务器更改为 VPN 路由器，此任务将使你能够进行切换并通知 Azure VNET。

-   **配置 AZURE VNET**此任务允许更改 Azure VNET 的高级配置选项，方法是将其重定向到 Azure VNET 的 "Azure 门户配置" 页。

-   **刷新状态**刷新 "状态" 页，更新 Azure VNET 的连接状态，包括 "传入/传出"。

-   **禁用 Azure VNET 集成**断开 Azure VNET 的连接并从 Windows Server Essentials 仪表板中删除集成。 请注意，这不会删除 Azure VNET，如果以后想要将 Azure VNET 与仪表板重新集成，则这些设置仍保留在 Azure 中。

-   **详细了解 AZURE VNET** [https://azure.microsoft.com/services/virtual-network/](https://azure.microsoft.com/services/virtual-network/)。

<a name="see-also"></a>另请参阅
--------
[Windows Server Essentials 入门](get-started.md)
