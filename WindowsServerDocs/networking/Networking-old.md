---
title: 联网
description: 本主题概述了 Windows Server 2016 中提供的软件定义的网络和网络平台技术。
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.date: 05/08/2018
ms.assetid: daaf6b61-5953-4c2d-b6b8-7c885b552646
manager: dougkim
ms.author: lizross
author: eross-msft
ms.localizationpriority: medium
ms.openlocfilehash: 833f1681af16b4e79a28383462a3471b3bc08f52
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319360"
---
# <a name="networking"></a>联网

>适用于：Windows Server（半年频道）、Windows Server 2016

       [!TIP]
        Looking for information about older versions of Windows Server? Check out our other [Windows Server libraries](/previous-versions/windows/) on docs.microsoft.com. You can also [search this site](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions) for specific information.

<img src="../media/landing-icons/network.png" style='float:left; padding:.5em;' alt="Icon depicting two networked computers"> 网络是软件定义的数据中心 \(SDDC\) 平台的基础部分，而 Windows Server 2016 提供了新的和改进的软件定义网络 \(SDN\) 技术，可帮助你迁移到适用于你的组织的完全实现的 SDDC 解决方案。

作为软件定义的资源管理网络时，可以一次描述应用程序的基础结构要求，然后选择应用程序在本地或云中运行的位置。 

这种一致性意味着，应用程序现在可以更轻松地进行扩展，并可随时随地无缝运行，且其安全性、性能、服务质量以及可用性不受影响。

>[!Note]
> 若要下载 Windows Server，请参阅 [Windows Server 评估](https://www.microsoft.com/evalcenter/evaluate-windows-server-technical-preview)。

Windows Server 2016 新增了以下网络技术：

- 软件定义网络：网络控制器提供集中的可编程点，可用于在数据中心自动管理、配置、监视虚拟和物理网络基础结构并进行故障排除。 网络控制器允许你使用网络功能虚拟化轻松地将虚拟机部署 \(Vm\) 用于软件负载平衡 \(SLB\) 以优化租户的网络流量负载，RAS 网关可为租户提供在 Internet、本地和云资源之间所需的连接选项。 还可以使用网络控制器管理 VM 和 Hyper-V 主机上的数据中心防火墙。

- 网络平台：使用现有网络平台技术的新功能，你可以使用 DNS 策略自定义 DNS 服务器对查询的响应，使用聚合 NIC 处理 \(RDMA 的合并远程直接内存访问\) 和以太网流量，使用交换机嵌入组合 \(设置\) 以创建连接到 RDMA Nic 的 Hyper-v 虚拟交换机，并使用 IP 地址管理 \(IPAM\) 来管理 DNS 区域和服务器以及 DHCP 和 IP 地址。

有关详细信息，请参阅 [Windows Server 支持的网络方案](windows-server-supported-networking-scenarios.md)。

以下部分提供有关 SDN 技术和网络平台技术的信息。

## <a name="software-defined-networking-technologies"></a>软件定义网络技术

### <a name="software-defined-networking-40sdn41"></a>[软件定义的&#40;网络 SDN&#41;](sdn/software-defined-networking.md)

阅读本主题，可以了解 Windows Server、System Center 和 Microsoft Azure 中提供的 SDN 技术。

>[!NOTE]
>对于 Hyper-v 主机和虚拟机 \(Vm\) 运行 SDN 基础结构服务器，如网络控制器和软件负载平衡节点，则必须安装 Windows Server 2016 Datacenter edition。 对于仅包含连接到 SDN\-受控网络的租户工作负荷 Vm 的 Hyper-v 主机，你可以运行 Windows Server 2016 Standard edition。

### <a name="deploy-a-software-defined-network-infrastructure-using-scripts"></a>[使用脚本部署软件定义的网络基础结构](sdn/deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md)
本指南说明如何在测试实验室环境中部署具有虚拟网络和网关的网络控制器。

### <a name="network-controller"></a>[网络控制器](sdn/technologies/network-controller/Network-Controller.md)

网络控制器提供集中的可编程点，可用于在数据中心自动管理、配置、监视虚拟和物理网络基础结构并进行故障排除。

### <a name="software-load-balancing-40slb41-for-sdn"></a>[用于 SDN 的&#40;软件&#41;负载平衡 SLB](sdn/technologies/network-function-virtualization/software-load-balancing-for-sdn.md)

云服务提供商 \(Csp\)，在 Windows Server 2016 中部署软件定义的网络（SDN）的企业可使用软件负载平衡 \(SLB\) 将租户和租户客户网络流量在虚拟网络资源之间均匀分配。 Windows Server SLB 允许多台服务器承载相同的工作负荷，具有较高的可用性和可扩展性。

### <a name="ras-gateway-for-sdn"></a>[用于 SDN 的 RAS 网关](sdn/technologies/network-function-virtualization/RAS-Gateway-for-SDN.md)

RAS 网关是 Windows Server 2016 中基于软件的、多租户的边界网关协议 \(BGP\) 支持的路由器，适用于使用 Hyper-v 网络虚拟化托管多个租户虚拟网络的云服务提供商 \(Csp\) 和企业。 

### <a name="network-function-virtualization"></a>[网络功能虚拟化](sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md)

在软件定义的数据中心，由硬件设备执行的网络功能 \(例如负载平衡器、防火墙、路由器、交换机等\) 会越来越多地虚拟化为虚拟设备。 服务器虚拟化和网络虚拟化自然而然地形成了这种“网络功能虚拟化”。

### <a name="datacenter-firewall-overview"></a>[数据中心防火墙概述](sdn/technologies/network-function-virtualization/Datacenter-Firewall-Overview.md)

数据中心防火墙是网络层上 5 元组（协议、源端口号、目标端口号、源 IP 地址和目标 IP 地址）的有状态多租户防火墙。

## <a name="networking-technologies"></a><a name="bkmk_networking"></a>网络技术

下表提供了 Windows Server 2016 中的一些网络技术的链接。

### <a name="whats-new-in-networking"></a>[网络中的新增功能](../networking/What-s-New-in-Networking.md)

你可以使用以下部分了解 Windows Server 2016 中的新网络技术和现有技术的新功能。

### <a name="branchcache"></a>[BranchCache](branchcache/BranchCache.md)

BranchCache 是一种广域网\) 带宽优化技术 \(广域网。 为了在用户访问远程服务器上的内容时优化 WAN 带宽，BranchCache 从总部或托管的云内容服务器复制内容，并将内容缓存在分支机构位置，使分支机构的客户端计算机可以从本地访问内容，而不是从 WAN 访问。

### <a name="core-network-guide-for-windows-server-2016"></a>[Windows Server 2016 核心网络指南](core-network-guide/core-network-guide-windows-server.md)

了解如何使用核心网络指南部署 Windows Server 网络，以及如何使用核心网络助理指南向网络中添加功能。

### <a name="directaccess"></a>[DirectAccess](../remote/remote-access/directaccess/DirectAccess.md)

DirectAccess 允许远程用户连接到组织网络资源。 

DirectAccess 文档现在位于[远程访问](https://docs.microsoft.com/windows-server/remote/)下 Windows Server 2016 目录的[远程访问和服务器管理](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access)部分中。 有关详细信息，请参阅 [DirectAccess](../remote/remote-access/directaccess/DirectAccess.md)。

### <a name="domain-name-system-40dns41"></a>[域名系统&#40;DNS&#41;](dns/dns-top.md)

域名系统 \(DNS\) 是构成 TCP/IP 的行业标准协议套件之一，结合 DNS 客户端和 DNS 服务器，为计算机和用户提供计算机名到 IP 地址映射的名称解析服务。

### <a name="dynamic-host-configuration-protocol-40dhcp41"></a>[动态主机配置协议&#40;DHCP&#41;](technologies/dhcp/dhcp-top.md)

动态主机配置协议 \(DHCP\) 是一种客户端/服务器协议，自动为 Internet 协议 \(IP\) 主机提供 IP 地址及其他相关配置信息，如子网掩码和默认网关。

### <a name="hyper-v-network-virtualization"></a>[Hyper-v 网络虚拟化](sdn/technologies/hyper-v-network-virtualization/Hyper-V-Network-Virtualization.md)

Hyper-v 网络虚拟化 \(HNV\) 在共享物理网络基础结构的基础上启用客户网络虚拟化。

### <a name="hyper-v-virtual-switch"></a>[Hyper-V 虚拟交换机](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)

Hyper-V 虚拟交换机是基于软件的第 2 层以太网网络交换机，当安装 Hyper-V 服务器角色时 Hyper-V 管理器中提供了该交换机。 交换机包括以编程方式管理的功能和扩展功能，可将虚拟机同时连接到虚拟网络和物理网络。 此外，Hyper-V 虚拟交换机提供了安全、隔离和服务级别的策略执行。 

Hyper-V 虚拟交换机文档现在位于 Windows Server 2016 目录的**虚拟化**部分中。 有关详细信息，请参阅 [Hyper-V 虚拟交换机](../virtualization/hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)。

### <a name="ip-address-management-40ipam41"></a>[IP 地址管理&#40;IPAM&#41;](technologies/ipam/ipam-top.md)

IP 地址管理 \(IPAM\) 是一套集成工具，支持端到端规划、部署、管理和监视 IP 地址基础结构，同时提供丰富的用户体验。 IPAM 会自动发现网络上的 IP 地址基础结构服务器和域名系统 \(DNS\) 服务器，并使你能够从中心界面管理它们。

### <a name="network-load-balancing"></a>[网络负载均衡](technologies/Network-Load-Balancing.md)

网络负载平衡 \(NLB\) 使用 TCP/IP 网络协议在多台服务器中分发流量。 对于非 SDN 部署，NLB 有助于确保无状态应用程序（如运行 Internet 信息服务 \(IIS\) 的 Web 服务器）通过在负载增加时添加更多服务器实现扩展。

### <a name="high-performance-networking"></a>[高性能网络](technologies/hpn/hpn-top.md)

Windows Server 2016 中的网络卸载和优化技术包括仅限软件 (SO) 的功能和技术、软件和硬件 (SH) 集成功能和技术，以及仅限硬件 (HO) 的功能和技术。

此外，还提供以下卸载和优化技术文档。

- [聚合网络接口卡（NIC）配置指南](technologies/conv-nic/cnic-top.md)
- [数据中心桥接（DCB）](technologies/dcb/dcb-top.md)
- [虚拟接收方缩放 (vRSS)](technologies/vrss/vrss-top.md)


### <a name="network-policy-server"></a>[网络策略服务器](technologies/nps/nps-top.md)

通过网络策略服务器 (NPS)，你可以针对连接请求身份验证和授权创建并实施组织级网络访问策略。

### <a name="network-shell-netsh"></a>[Network Shell (Netsh)](technologies/netsh/netsh.md)

可以使用网络 Shell \(netsh\) 网络实用工具来管理 Windows Server 2016 和 Windows 10 中的网络技术。

### <a name="network-subsystem-performance-tuning"></a>[网络子系统性能优化](technologies/network-subsystem/net-sub-performance-top.md)

本主题提供有关为服务器工作负荷选择合适的网络适配器、对网络接口排序、网络相关性能计数器以及性能优化网络适配器和相关网络技术（如 \(RSS\)、接收方合并 \(RSC\)等）的信息。

### <a name="nic-teaming"></a>[NIC 组合](technologies/nic-teaming/NIC-Teaming.md)

NIC 组合可以将物理以太网网络适配器组合为一个或多个基于软件的虚拟网络适配器。 这些虚拟网络适配器可以提高性能，并在网络适配器发生故障时提供容错能力。

### <a name="quality-of-service-qos-policy"></a>[服务质量（QoS）策略](technologies/qos/qos-policy-top.md)

通过创建其设置使用组策略分发的 QoS 配置文件，你可以在整个 Active Directory 基础架构中，将 QoS 策略用作网络带宽管理的中心点。

### <a name="remote-access"></a>[远程访问](../remote/remote-access/remote-access.md)

可以使用远程访问技术（例如 DirectAccess 和虚拟专用网络） \(VPN\) 为远程辅助角色提供与内部网络资源的连接。 此外，还可以对局域网 \(LAN\) 路由和 Web 应用程序代理使用远程访问。 该代理为企业网络中的 Web 应用程序提供反向代理功能，使任一设备上的用户能够从企业网络外部访问这些 Web 应用程序。

远程访问文档现在位于 Windows Server 2016 目录的[远程访问和服务器管理](https://docs.microsoft.com/windows-server/remote/)部分中。 有关详细信息，请参阅[远程访问](../remote/remote-access/remote-access.md)。

有关 Web 应用程序代理（是远程访问服务器角色的角色服务）的详细信息，请参阅 [Windows Server 2016 中的 Web 应用程序代理](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server)。

### <a name="virtual-private-networking-vpn"></a>[虚拟专用网 (VPN)](../remote/remote-access/vpn/vpn-top.md)

在 Windows Server 2016 中，**DirectAccess 和 VPN** 是**远程访问**服务器角色的角色服务。

当你将远程访问作为 VPN 服务器安装时，你可以使用虚拟专用网络 \(VPN\) 为远程员工提供跨 Internet 连接到你的组织网络的连接，同时还可以使用加密连接来维护信息隐私。

对于 Windows Server 2016 远程访问 VPN 和 Windows 10 客户端计算机，你现在可以部署“始终启用 VPN”。 “始终启用 VPN”让你可以管理始终连接的远程 VPN 客户端，同时还为远程工作人员提供便利，因为他们不再需要从 VPN 手动连接到组织网络和断开该连接。

有关详细信息，请参阅 [Windows Server 2016 和 Windows 10 远程访问始终启用 VPN 部署指南](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy)。

>[!NOTE]
>VPN 文档现在位于[远程访问](https://docs.microsoft.com/windows-server/remote/)下 Windows Server 2016 目录的[远程访问和服务器管理](https://docs.microsoft.com/windows-server/remote/remote-access/remote-access)部分中。

有关 VPN 的详细信息，请参阅[虚拟专用网络 (VPN)](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/vpn-top)。

### <a name="windows-container-networking"></a>[Windows 容器网络](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/container-networking)

通过 Windows 容器网络，你可以使用标准行业工具和工作流程创建并管理网络，以连接 Windows 10 和 Windows Server 主机上的容器终结点。 Windows 容器网络支持多个拓扑，包括专用、平面 L2 和路由 L3。

还支持使用 Docker、Kubernetes 或 Windows PowerShell 通过与 Windows 主机网络服务 \(HNS\)通信的插件在主机上本地创建重叠。 可以通过将本地代理与每个节点的 HNS 通信，来创建和管理多个\-节点群集网络（通过更高级别的业务流程系统）。

### <a name="windows-internet-name-service-wins"></a>[Windows Internet 名称服务 (WINS)](technologies/wins/wins-top.md)

Windows Internet 名称服务 (WINS) 是传统的计算机名称注册和解析访问服务，该服务将计算机 NetBIOS 名称映射到 IP 地址。 建议使用 DNS 而非 WINS。

## <a name="additional-resources"></a>其他资源

以下位置提供了早于 Windows Server 2016 的操作系统的网络资源。

- Windows Server 2012 和 Windows Server 2012 R2 [网络连接概述](https://technet.microsoft.com/library/hh831357.aspx)
- Windows Server 2008 和 Windows Server 2008 R2 [Networking](https://technet.microsoft.com/library/cc753940)（网络）
- Windows Server 2003 [Windows server 2003/2003 R2 已停用内容](https://www.microsoft.com/download/details.aspx?id=53314)
