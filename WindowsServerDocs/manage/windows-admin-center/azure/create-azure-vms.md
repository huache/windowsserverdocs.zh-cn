---
title: 使用 Windows 管理中心部署 Azure 虚拟机
description: 部署 Azure 虚拟机和 Windows 管理中心。 将 Azure 虚拟机配置为 Windows 管理中心托管方案的一部分。
ms.topic: article
author: nedpyle
ms.author: nedpyle
manager: jgerend
ms.date: 01/28/2020
ms.localizationpriority: medium
ms.openlocfilehash: c9401d19472e362ee411613ee97caa3428c35e4f
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87997536"
---
# <a name="deploy-azure-virtual-machines-from-within-windows-admin-center"></a>从 Windows 管理中心部署 Azure 虚拟机

>适用于：Windows Admin Center、Windows Admin Center 预览版

Windows 管理中心版本1910允许你部署 Azure 虚拟机。 这将 VM 部署集成到 Windows 管理中心中心管理的工作负荷，例如[存储迁移服务](../../../storage/storage-migration-service/overview.md)和[存储副本](../../../storage/storage-replica/storage-replica-overview.md)。 在部署工作负荷之前，无需在 Azure 门户中创建新的服务器和 Vm，并且可能缺少所需的步骤和配置-Windows 管理中心可以部署 Azure VM、配置其存储、将其加入域、安装角色，然后设置你的分布式系统。 你还可以在没有工作负荷的情况下部署新的 Azure Vm。

Windows 管理中心还管理各种 Azure 服务。 [详细了解 Windows 管理中心提供的 Azure 集成选项](./index.md)。

如果要将虚拟机直接迁移到 Azure，而不是创建新虚拟机，请考虑使用 Azure Migrate。 有关详细信息，请参阅[Azure Migrate 概述](https://go.microsoft.com/fwlink/?linkid=2056064)。

## <a name="scenarios"></a>方案

Windows 管理中心版本 1910 Azure VM 部署支持以下方案：

- [存储迁移服务](../../../storage/storage-migration-service/overview.md)
- [存储副本](../../../storage/storage-replica/storage-replica-overview.md)
- [无角色的新独立服务器 () ](index.md#extend-on-premises-capacity-with-azure)

## <a name="requirements"></a>要求

若要从 Windows 管理中心中创建新的 Azure VM，需要具备以下要求：

- 一个 [Azure 订阅](https://azure.microsoft.com)。
- [使用 Azure 注册的 Windows 管理中心网关](azure-integration.md)
- 具有创建权限的现有[Azure 资源组](/azure/azure-resource-manager/management/overview)。
- 现有的[Azure 虚拟网络](/azure/virtual-network/virtual-networks-overview)和子网。
- 与虚拟网络和子网关联的[Azure Express 路由](https://azure.microsoft.com/services/expressroute/)或[azure VPN 解决方案](https://azure.microsoft.com/services/vpn-gateway/)，该解决方案允许从 Azure vm 连接到本地客户端、域控制器、Windows 管理中心计算机，以及需要与此 VM 进行通信的任何服务器作为工作负荷部署的一部分。 例如，若要使用存储迁移服务将存储迁移到 Azure VM，orchestrator 计算机和源计算机必须都能联系到要迁移到的目标 Azure VM。

## <a name="usage"></a>使用情况

Azure VM 部署步骤和向导因情况而异。 查看工作负荷的文档，以获取有关整个方案的详细信息。

### <a name="deploying-azure-vms-as-part-of-storage-migration-service"></a>将 Azure Vm 作为存储迁移服务的一部分进行部署

1. 在 Windows 管理中心的*存储迁移服务*工具中，执行一个或多个源服务器的清单。
2. 进入 "*传输数据*" 阶段后，在 "*指定目标*" 页上选择 "**创建新的 Azure VM** "，然后单击 "**创建 VM**"。<br><br>
这将开始一个分步创建工具，该工具选择 Windows Server 2012 R2、Windows Server 2016 或 Windows Server 2019 Azure VM 作为迁移的目标。 存储迁移服务提供了建议的 VM 大小来匹配源，但你可以通过单击 "**查看所有大小**" 来替代它们。
<br><br>源服务器数据还用于自动配置托管磁盘及其文件系统，并将新的 Azure VM 加入到 Active Directory 域。 如果 VM 为 Windows Server 2019 (建议) ，则 Windows 管理中心会安装存储迁移服务代理功能。 创建 Azure VM 后，Windows 管理中心将返回到正常的存储迁移服务传输工作流。

以下视频演示了如何使用存储迁移服务迁移到 Azure Vm。

> [!VIDEO https://www.youtube-nocookie.com/embed/k8Z9LuVL0xQ]

### <a name="deploying-azure-vms-as-part-of-storage-replica"></a>将 Azure Vm 部署为存储副本的一部分

1. 在 Windows 管理中心的 "*存储副本*" 工具中，选择 *"* **新建**"，然后在 "*使用其他服务器复制*" 下选择 "**使用新的 Azure VM** "，然后选择 "**下一步**"。
2. 指定源服务器信息和复制组名称，然后选择 "**下一步**"。<br><br>
这会开始一个过程，该过程会自动选择 Windows Server 2016 或 Windows Server 2019 Azure VM 作为迁移源的目标。 存储迁移服务建议 VM 大小与你的源匹配，但你可以通过选择 "**查看所有大小**" 来覆盖此项。 清单数据用于自动配置托管磁盘及其文件系统，并将新的 Azure VM 加入到 Active Directory 域。
3. Windows 管理中心创建 Azure VM 后，提供复制组名称，然后选择 "**创建**"。 然后，Windows 管理中心会开始正常存储副本初始同步过程以开始保护数据。

以下视频演示了如何使用存储副本复制到 Azure Vm。

> [!VIDEO https://www.youtube-nocookie.com/embed/_VqD7HjTewQ]

### <a name="deploying-a-new-standalone-azure-vm"></a>部署新的独立 Azure VM

1. 在 Windows 管理中心的 "*所有连接*" 页中，选择 "**添加**"。
2. 在 " *AZURE VM* " 部分中，选择 "**新建**"。<br><br> 这将开始一个逐步创建的工具，该工具可让你选择 Windows Server 2012 R2、Windows Server 2016 或 Windows Server 2019 Azure VM，选择大小，添加托管磁盘，并选择性地加入 Active Directory 域。

以下视频演示如何使用 Windows 管理中心创建 Azure Vm。

> [!VIDEO https://www.youtube-nocookie.com/embed/__A8J9aC_Jk]