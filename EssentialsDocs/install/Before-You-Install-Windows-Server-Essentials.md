---
title: 安装 Windows Server Essentials 之前的准备事项
description: 描述如何使用 Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d0893bd-e2b7-4494-9537-02b1cbbcd57a
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 4629c0ba04cc7ee617a2fc6b6a73a19b9e45ada8
ms.sourcegitcommit: 3d76683718ec6f38613f552f518ebfc6a5db5401
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829551"
---
# <a name="before-you-install-windows-server-essentials"></a>安装 Windows Server Essentials 之前的准备事项

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="BKMK_BeforeYouBegin"></a>在开始安装 Windows Server Essentials 之前，请执行以下任务：  

-   **请确保你的计算机符合最低硬件要求**。 这包括确定是否需要额外的硬件并验证 Windows Server Essentials 是否支持硬件的驱动程序。 有关详细信息，请参阅[Windows Server Essentials 的系统要求](../get-started/system-requirements.md)。   

> [!IMPORTANT]
> 在预先存在的计算机上安装 Windows Server Essentials 之前，我们建议您完全格式化现有计算机的硬盘，然后再对其进行重新分区。 通过对硬盘进行格式化和重新分区，你可以消除硬盘存在隐藏分区的可能性。  

- **准备网络**若要准备网络以安装 Windows Server Essentials，请执行以下操作：  


  - **升级客户端计算机上的操作系统** Windows Server Essentials 支持以下操作系统： Windows 8、Windows 7、Windows 10 和 Macintosh OS X Lion 或更高版本。 这些操作系统为本地网络提供了必要的安全功能、可靠性、性能和功能。  

  - **配置路由器** 检查路由器的配置是否符合下述要求：  

    -   路由器上已启用 UPnP 框架。  

    -   可启用或禁用 LAN 的动态主机配置协议 (DHCP) 服务器服务。  Windows Server Essentials 确保 DHCP 在服务器和路由器上均未运行？ 如果在路由器上启用 DHCP，则在安装过程中不会在服务器上启用 DHCP。  

    -   路由器有一个外部接口 IP 地址，该地址由 Internet 服务提供商 (ISP) 提供。 IP 地址可由 ISP 的 DHCP 服务器服务动态分配，或者你必须使用路由器管理控制台手动配置静态 IP 地址。  

    -   如果你的 Internet 连接需要用户名和密码（也称为点对点以太网协议 (PPPoE)），则即使设备支持 UPnP 框架，也要在路由器上配置这些设置。  

    -   路由器连接到 LAN 和 Internet 并打开，而且可以正常工作。  

    如果路由器不支持 UPnP 框架，或者如果在安装过程中无法配置路由器，则必须使用网络设置来手动配置路由器。 确保以下端口已打开并且定向到目标服务器的 IP 地址：  

  |端口号|应用程序|  
  |-----------------|-----------------|  
  |端口 80|HTTP Web 流量|  
  |端口 443|HTTPS Web 流量|  


- **阅读 Windows Server Essentials 版本文档**。 版本文档包含可能对正确安装和配置 Windows Server Essentials 至关重要的最新信息。 若要查看或打印发行文档，请参阅[Windows Server Essentials 的发布文档](../get-started/release-notes.md)。  

## <a name="see-also"></a>另请参阅  

-   [安装 Windows Server Essentials](Install-Windows-Server-Essentials.md)

