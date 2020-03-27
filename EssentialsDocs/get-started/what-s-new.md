---
title: Windows Server 2016 Essentials 中的新增功能
description: 描述如何使用 Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: affff774-5fa6-4944-887a-9bfde05f6a3f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 1d5176a69136e9bad36e22472b8fadbd6d0e9e79
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80310308"
---
# <a name="whats-new-in-windows-server-2016-essentials"></a>Windows Server 2016 Essentials 中的新增功能

> 适用于： Windows Server 2016 Essentials

下面是 Windows Server 2016 Essentials 中的新增功能和增强功能。

## <a name="integration-with-azure-site-recovery-services"></a>[与 Azure Site Recovery Services 的集成](azure-site-recovery-services-integration.md)

**它**的作用-如果受保护的虚拟机失败，或者运行受保护虚拟机的主机服务器发生故障，则使用 Azure Site Recovery 服务进行故障转移会保持业务连续性，直到本地虚拟机或主机服务器已修复并可用。 

**它的工作原理**-Azure Site Recovery 服务在 Microsoft Azure 中提供，可将虚拟机（VM）实时复制到 Azure 中的备份保管库。 如果你的服务器或站点由于硬件或其他故障而停机，则可以使用 Azure Site Recovery 服务进行故障转移，以便将存储在备份保管库中的 VM 映像预配为 Azure 中正在运行的 VM。 与 Azure 虚拟网络相结合，先前连接到本地服务器的客户端电脑将以透明方式连接到在 Azure 中运行的服务器。     
                                                                                                                                                                                                                                                                                                               

## <a name="integration-with-azure-virtual-network"></a>[与 Azure 虚拟网络集成](azure-virtual-network-integration.md)

**它**的作用是：随着组织做出云计算的方式，他们很少一次移动其所有资源。 相反，它们将一些资源移到云中，并将其保存在本地。 这样一来，在一段时间内就可以轻松地将组织迁移到云。 Azure 虚拟网络集成提供了网络基础结构，使该过程无缝且可管理。

**工作原理**-Azure 虚拟网络是 Microsoft Azure 中提供的一种服务，它使组织能够创建点到点（P2P）或站点到站点（S2S）虚拟专用网络，使在 Azure 中运行的资源（例如虚拟机和存储）看起来就像是在本地网络上，以实现无缝应用程序和资源访问。



## <a name="support-for-larger-deployments"></a>[支持较大的部署](support-for-larger-deployments.md) 

一些较大的小型企业需要更多的功能和容量才能有效地实施 Windows Server Essentials。 通过添加对较大部署的支持，Windows Server 2016 Essentials 可提高域、用户和设备的可管理性：                                                                                                                                                                                                 

 - 多个域
 - 多个域控制器                                                                                                                                                                                                                                        
 - 指定指定域控制器的能力                                                                                                                                                                                                                   
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       

<a name="see-also"></a>另请参阅
--------

[Windows Server Essentials 入门](get-started.md)
