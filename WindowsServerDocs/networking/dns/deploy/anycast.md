---
title: 任意广播 DNS 概述
description: 本主题简要概述了可广播 DNS
manager: laurawi
ms.prod: windows-server
ms.technology: networking-dns
ms.topic: article
ms.assetid: f9c313ac-bb86-4e48-b9b9-de5004393e06
ms.author: greglin
author: greg-lindsay
ms.openlocfilehash: 2f91ace398cf236967fadde21db7ea0957640995
ms.sourcegitcommit: c4f30b1617571fe434c7fe054695d163e73506b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2020
ms.locfileid: "88048886"
---
# <a name="anycast-dns-overview"></a>任意广播 DNS 概述

>适用于： Windows Server (半年通道) ，Windows Server 2016，Windows Server 2019

本主题提供有关任意播 DNS 的工作方式的信息。

## <a name="what-is-anycast"></a>什么是任意广播？

任意广播是一种技术，该技术提供指向一组终结点的多个路由路径，每个终结点都分配有相同的 IP 地址。 组中的每个设备在网络上公布相同的地址，并且使用路由协议选择哪个是最佳目标。

使用任意播，可以通过将多个节点放在同一 IP 地址后面并使用相等成本多路径 (ECMP) 路由来定向这些节点之间的流量，来缩放无状态服务（如 DNS 或 HTTP）。 任意播不同于单播，其中每个终结点都有自己的单独的 IP 地址。 

## <a name="why-use-anycast-with-dns"></a>为什么对 DNS 使用任意广播？

使用任意播 DNS，你可以启用 DNS 服务器或一组服务器，以根据 DNS 客户端的地理位置来响应 DNS 查询。 这可以提高 DNS 响应时间并简化 DNS 客户端设置。 任意广播 DNS 还提供额外的冗余层，有助于防范 DNS 拒绝服务攻击。 

### <a name="how-anycast-dns-works"></a>任意播 DNS 的工作方式

使用路由协议（例如边界网关协议 (BGP) 将 DNS 查询发送到首选 DNS 服务器或 DNS 服务器组），可广播 DNS 的工作 (例如：负载均衡) 器所管理的一组 DNS 服务器。 这可以通过从离客户端最近的 DNS 服务器获取 DNS 响应来优化 DNS 通信。

使用任意广播时，位于多个地理位置的服务器每个都将一个相同的 IP 地址播发到本地网关 (路由器) 。 当 DNS 客户端启动对任意播地址的查询时，将评估可用路由，并将 DNS 查询发送到首选位置。 通常，这是基于网络拓扑的最接近的位置。 请参阅以下示例。

![任意广播 DNS](../../media/Anycast/anycast.png)

**图 1**：位于网络中不同站点上的四个 DNS 服务器，每个服务器都公布相同的任意广播 IP 地址 (黑色箭头) 网络。 DNS 客户端设备将请求发送到任意广播 IP 地址。 网络设备分析可用路由，并将客户端的 DNS 查询发送到最近的位置 (蓝色箭头) 。 

现在，可以使用任意播 DNS 来路由多个全局 DNS 服务的 DNS 流量。 例如，根 DNS 服务器系统很大程度上取决于任意播 DNS。 任意广播还适用于各种路由协议，可在 intranet 上专门使用。

## <a name="windows-server-native-bgp-anycast-demo"></a>Windows Server 本机 BGP 任意播演示

下面的过程演示如何将 Windows Server 上的本机 BGP 与任意播 DNS 一起使用。  

### <a name="requirements"></a>要求

- 一台安装了 Hyper-v 角色的物理设备。
  - Windows Server 2012 R2、Windows 10 或更高版本。
- 2个客户端 Vm (任何操作系统) 。
  - 建议为 DNS 安装 BIND 工具，如 "进行挖掘"。
- 3个服务器 Vm (Windows Server 2016 或 Windows Server 2019) 。
  - 如果尚未在服务器 Vm 上安装 Windows PowerShell LoopbackAdapter 模块 (DC001，DC002) ，则暂时需要 Internet 访问权限才能安装此模块。

### <a name="hyper-v-setup"></a>Hyper-v 设置

按如下所示配置 Hyper-v 服务器：

- 已配置2个专用虚拟交换机网络
  - 模拟 Internet 网络 131.253.1.0/24
  - 模拟 intranet 网络 10.10.10.0/24
- 2个客户端 Vm 连接到 131.253.1.0/24 网络
- 2个服务器 Vm 连接到 10.10.10.0/24 网络
- 1个服务器是双重宿主，同时连接到 131.253.1.0/24 和 10.10.10.0/24 网络。

### <a name="virtual-machine-network-configuration"></a>虚拟机网络配置

在具有以下设置的虚拟机上配置网络设置：

1.  Client1、client2
  - Client1：131.253.1。1
  - Client2：131.253.1。2
  - 子网掩码：255.255.255.0
  - DNS：51.51.51.51
  - 网关：131.253.1.254
2.  网关 (Windows Server) 
  - NIC1：131.253.1.254，子网255.255.255。0
  - NIC2：10.10.10.254，子网255.255.255。0
  - DNS：51.51.51.51
  - 网关：对于演示，可以忽略 131.253.1.100 () 
3.  DC001 (Windows Server) 
  - NIC1：10.10.10。1
  - 子网：255.255.255。0
  - DNS：10.10.10。1
4.  DC002 (Windows Server) 
  - NIC1：10.10.10。2
  - 子网255.255.255。0
  - DNS：10.10.10。2

### <a name="configure-dns"></a>配置 DNS

使用服务器管理器和 DNS 管理控制台或 Windows PowerShell 安装以下服务器角色，并在两个服务器上的每个服务器上创建一个静态 DNS 区域。

1.  DC001, DC002
  - 安装 Active Directory 域服务并升级到域控制器 (可选) 
  -  (必需安装 DNS 角色) 
  - 在 DC001 和 DC002 上创建 (非 AD 集成) 为 "tst" 的静态区域 **。**
    - 在 "TXT" 类型的区域中添加单个静态记录名称**服务器**
    - DC001 上的 TXT 记录的数据 (文本) = **DC001**
    - DC002 上的 TXT 记录的数据 (文本) = **DC002**

### <a name="configure-loopback-adapters"></a>配置环回适配器

在 DC001 和 DC002 上提升的 Windows PowerShell 提示符下输入以下命令以配置环回适配器。 

> [!NOTE]
> **安装模块**命令要求访问 Internet。 这可以通过将 VM 临时分配到 Hyper-v 中的外部网络来完成。

```PowerShell
$primary_interface = (Get-NetAdapter |?{$_.Status -eq "Up" -and !$_.Virtual}).Name
$loopback_ipv4 = '51.51.51.51'
$loopback_ipv4_length = '32'
$loopback_name = 'Loopback'
Install-Module -Name LoopbackAdapter -MinimumVersion 1.2.0.0 -Force
Import-Module -Name LoopbackAdapter
New-LoopbackAdapter -Name $loopback_name -Force
$interface_loopback = Get-NetAdapter -Name $loopback_name
$interface_main = Get-NetAdapter -Name $primary_interface
Set-NetIPInterface -InterfaceIndex $interface_loopback.ifIndex -InterfaceMetric "254" -WeakHostReceive Enabled -WeakHostSend Enabled -DHCP Disabled
Set-NetIPInterface -InterfaceIndex $interface_main.ifIndex -WeakHostReceive Enabled -WeakHostSend Enabled
Set-NetIPAddress -InterfaceIndex $interface_loopback.ifIndex -SkipAsSource $True
Get-NetAdapter $loopback_name | Set-DNSClient –RegisterThisConnectionsAddress $False
New-NetIPAddress -InterfaceAlias $loopback_name -IPAddress $loopback_ipv4 -PrefixLength $loopback_ipv4_length -AddressFamily ipv4
Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_msclient
Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_pacer
Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_server
Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_lltdio
Disable-NetAdapterBinding -Name $loopback_name -ComponentID ms_rspndr
```

### <a name="virtual-machine-routing-configuration"></a>虚拟机路由配置

在 Vm 上使用以下 Windows PowerShell 命令来配置路由。

1.  网关
```PowerShell
Install-RemoteAccess -VpnType RoutingOnly
Add-BgpRouter -BgpIdentifier “10.10.10.254” -LocalASN 8075
```

2.  DC001
```PowerShell
Install-RemoteAccess -VpnType RoutingOnly
Add-BgpRouter -BgpIdentifier “10.10.10.1” -LocalASN 65511
Add-BgpPeer -Name "Labgw" -LocalIPAddress 10.10.10.1 -PeerIPAddress 10.10.10.254 -PeerASN 8075 –LocalASN 65511
Add-BgpCustomRoute -Network 51.51.51.0/24
```

3.  DC002
```PowerShell
Install-RemoteAccess -VpnType RoutingOnly
Add-BgpRouter -BgpIdentifier "10.10.10.2" -LocalASN 65511
Add-BgpPeer -Name "Labgw" -LocalIPAddress 10.10.10.2 -PeerIPAddress 10.10.10.254 -PeerASN 8075 –LocalASN 65511
Add-BgpCustomRoute -Network 51.51.51.0/24
```

### <a name="summary-diagram"></a>摘要图表

![任意广播 DNS](../../media/Anycast/anycast-lab.png)

**图 2**：本机 BGP 任意播 DNS 演示的实验室设置

## <a name="anycast-dns-demonstration"></a>任意广播 DNS 演示


1.  验证网关服务器上的 BGP 路由

    PS C： \> BgpRouteInformation

    DestinationNetwork NextHop LearnedFromPeer State LocalPref MED-V<br>
    ------------------ -------    --------------- ----- --------- ---<br>
    51.51.51.0/24 10.10.10.1 DC001 最佳<br>
    51.51.51.0/24 10.10.10.2 DC002 最佳<br>

2.  在 client1 和 client2 上，验证是否可以访问51.51.51.51

    PS C： \> ping 51.51.51.51

    Ping 包含32字节数据的51.51.51.51：<br>
    来自51.51.51.51 的回复： bytes = 32 time<1ms TTL = 126<br>
    来自51.51.51.51 的回复： bytes = 32 time<1ms TTL = 126<br>
    来自51.51.51.51 的回复： bytes = 32 time<1ms TTL = 126<br>
    来自51.51.51.51 的回复： bytes = 32 time<1ms TTL = 126

    51.51.51.51 的 Ping 统计信息：<br>
    数据包： Sent = 4，Received = 4，丢失 = 0 (0% 丢失) ，<br>
    Milli 中的近似往返时间（秒）：<br>
    最小值 = 0ms，最大 = 0ms，Average = 0ms

3.  在 client1 和 client2 上，使用 nslookup 或查询 TXT 记录。 下面显示了二者的示例。

    PS C： \> 挖 TST TXT + short<br>
    PS C： \> nslookup 类型 = txt tst 51.51.51.51

    一位客户端将显示 "DC001"，而另一个客户端将显示 "DC002"，验证任意播是否正常工作。  你还可以从网关服务器进行查询。

4.  接下来，禁用 DC001 上的以太网适配器。

    PS C： \> (get-netadapter) 。路径名<br>
    环回<br>
    以太网2<br>
    PS C： \> get-netadapter "以太网 2"<br>
    确认<br>
    是否确实要执行此操作？<br>
    Get-netadapter "以太网 2"<br>
    [Y] 是 [A] 所有 [N] 否 [L] 所有 [S] 挂起 [？]"帮助 (默认值为" Y ") ：<br>
    PS C： \> (get-netadapter) 。状态值<br>
    向上<br>
    已禁用

5.  确认以前从 DC001 接收响应的 DNS 客户端已切换到 DC002。

    PS C： \> nslookup 类型 = txt tst 51.51.51.51<br>
    服务器：未知<br>
    地址：51.51.51.51<br>

    tst 文本 =

    "DC001"<br>
    PS C： \> nslookup 类型 = txt tst 51.51.51.51<br>
    服务器：未知<br>
    地址：51.51.51.51<br>

    tst 文本 =

    "DC002"

6.  使用网关服务器上的 Get-bgpstatistics 确认 DC001 上的 BGP 会话是否已关闭。
7.  再次启用 DC001 上的以太网适配器，并确认已还原 BGP 会话，并且客户端将再次从 DC001 接收 DNS 响应。

> [!NOTE]
> 如果未使用负载均衡器，则单个客户端将使用相同的后端 DNS 服务器（如果可用）。 这会为客户端创建一致的 BGP 路径。 有关详细信息，请参阅 4.4.3 of RFC4786：[平等-Cost Paths](https://tools.ietf.org/html/rfc4786#page-10)部分。

## <a name="frequently-asked-questions"></a>常见问题

问：是否有可在本地 DNS 环境中使用的可广播 DNS 好解决方案？<br>
答：可广播 DNS 与本地 DNS 服务无缝协作。 但是，DNS 服务无*需*进行扩展即可进行扩展。
 
问：在具有大量 (ex： >50) 域控制器的环境中实现任意播 DNS 的影响是什么？ <br>
答：对功能没有直接的影响。 如果使用负载均衡器，则不需要域控制器上的其他配置。
 
问： Microsoft 客户服务是否支持任意播 DNS 配置？<br>
答：如果使用非 Microsoft 负载均衡器来转发 DNS 查询，Microsoft 将支持与 DNS 服务器服务相关的问题。 请咨询负载平衡器供应商以了解与 DNS 转发相关的问题。 
 
问：对于具有大量 (（例如： >50) 域控制器）的可广播 DNS，最佳做法是什么？<br>
答：最佳实践是在每个地理位置使用负载均衡器。 负载均衡器通常由外部供应商提供。 

问：任意播 DNS 和 Azure DNS 是否具有类似的功能？<br>
答： Azure DNS 使用任意播。 若要对 Azure DNS 使用任意播，请将负载均衡器配置为将请求转发到 Azure DNS 服务器。 