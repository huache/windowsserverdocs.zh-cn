---
title: Windows Server 2016 Essentials 中的新增功能
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: affff774-5fa6-4944-887a-9bfde05f6a3f
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: baf674b75f9476b65ba508f2841e0973783f1b9a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624170"
---
# <a name="whats-new-in-windows-server-2016-essentials"></a>Windows Server 2016 Essentials 中的新增功能

> 适用于： Windows Server 2016 Essentials

下面是 Windows Server 2016 Essentials 中的新增功能和增强功能。

## <a name="integration-with-azure-site-recovery-services"></a>[与 Azure Site Recovery Services 的集成](azure-site-recovery-services-integration.md)

**What it does**  -- 作用 &reg;当受保护的虚拟机失败或运行受保护虚拟机的主机服务器发生故障时，使用 Azure Site Recovery 服务进行故障转移会保持业务连续性，直到本地虚拟机或主机服务器已修复并可用。 

**它的工作原理** -Azure Site Recovery 服务，Microsoft Azure 提供，可将虚拟机 (VM) 实时复制到 Azure 中的备份保管库。 如果你的服务器或站点由于硬件或其他故障而停机，则可以使用 Azure Site Recovery 服务进行故障转移，以便将存储在备份保管库中的 VM 映像预配为 Azure 中正在运行的 VM。 与 Azure 虚拟网络相结合，先前连接到本地服务器的客户端电脑将以透明方式连接到在 Azure 中运行的服务器。


## <a name="integration-with-azure-virtual-network"></a>[与 Azure 虚拟网络集成](azure-virtual-network-integration.md)

**它**的作用是：随着组织做出云计算的方式，他们很少一次移动其所有资源。 相反，它们将一些资源移到云中，并将其保存在本地。 这样一来，在一段时间内就可以轻松地将组织迁移到云。 Azure 虚拟网络集成提供了网络基础结构，使该过程无缝且可管理。

**工作原理** -Azure 虚拟网络是 Microsoft Azure 中提供的一种服务，它使组织能够创建点到点 (P2P) 或站点到站点 (S2S) 虚拟专用网络，使在 Azure 中运行的资源 (例如虚拟机和存储) 查看本地网络中的资源，以实现无缝应用程序和资源访问。



## <a name="support-for-larger-deployments"></a>[支持较大的部署](support-for-larger-deployments.md)

一些较大的小型企业需要更多的功能和容量才能有效地实施 Windows Server Essentials。 通过添加对较大部署的支持，Windows Server 2016 Essentials 可提高域、用户和设备的可管理性：

 - 多个域
 - 多个域控制器
 - 指定指定域控制器的能力


<a name="see-also"></a>请参阅
--------

[Windows Server Essentials 入门](get-started.md)&copy;&reg;