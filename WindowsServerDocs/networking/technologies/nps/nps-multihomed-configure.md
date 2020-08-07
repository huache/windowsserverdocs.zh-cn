---
title: 在多宿主计算机上配置 NPS
description: 本主题提供有关在 Windows Server 2016 中使用运行网络策略服务器的多个网络适配器配置服务器的说明。
manager: brianlic
ms.topic: article
ms.assetid: d9d9e9ac-4859-4522-89ed-a23092c9e12a
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 1292accf4d19afa7f6a050281b7af373b3c867c3
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87952082"
---
# <a name="configure-nps-on-a-multihomed-computer"></a>在多宿主计算机上配置 NPS

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题来配置具有多个网络适配器的 NPS。

在运行网络策略服务器 (NPS) 的服务器中使用多个网络适配器时，可以配置以下内容：

- 不发送和接收远程身份验证拨入用户服务 RADIUS 流量的网络适配器 \( \) 。
- 在每个网络适配器基础上，NPS 是否监视 Internet 协议版本4（ \( ipv4 \) 、ipv6）或 Ipv4 和 ipv6 上的 RADIUS 流量。
- UDP 端口号，根据每个协议的 \( IPv4 或 IPv6 \) （每个网络适配器）发送和接收 RADIUS 流量。

默认情况下，NPS 针对用于所有已安装网络适配器的 IPv6 和 IPv4 侦听端口 1812、1813、1645 和 1646 上的 RADIUS 流量。 由于 NPS 自动将所有网络适配器用于 RADIUS 流量，因此当你想要阻止 NPS 使用特定网络适配器时，只需指定你希望 NPS 用于 RADIUS 流量的网络适配器。

>[!NOTE]
>如果卸载网络适配器上的 IPv4 或 IPv6，则 NPS 不会监视已卸载协议的 RADIUS 流量。

在安装了多个网络适配器的 NPS 上，你可能想要将 NPS 配置为仅在指定的适配器上发送和接收 RADIUS 流量。

例如，安装在 NPS 中的一个网络适配器可能会导致不包含 RADIUS 客户端的网络段，而另一个网络适配器为 NPS 提供到其配置的 RADIUS 客户端的网络路径。 在这种情形中，重要的是引导 NPS 对所有 RADIUS 流量使用第二个网络适配器。

在另一个示例中，如果 NPS 安装了三个网络适配器，但仅希望 NPS 将两个适配器用于 RADIUS 流量，则只能为这两个适配器配置端口信息。 通过排除第三个适配器的端口配置，阻止 NPS 对 RADIUS 流量使用适配器。

## <a name="using-a-network-adapter"></a>使用网络适配器

若要将 NPS 配置为在网络适配器上侦听和发送 RADIUS 流量，请在 NPS 控制台中的网络策略服务器的 "属性" 对话框中使用以下语法：

- IPv4 流量语法： IPAddress： UDPport，其中，IPAddress 是在要发送 RADIUS 流量的网络适配器上配置的 IPv4 地址，UDPport 是要用于 RADIUS 身份验证或记帐流量的 RADIUS 端口号。
- IPv6 流量语法： [IPv6Address]： UDPport，其中，IPv6Address 是在要发送 RADIUS 流量的网络适配器上配置的 IPv6 地址，而 UDPport 是要用于 RADIUS 身份验证或记帐流量的 RADIUS 端口号。

下列字符可用作配置 IP 地址和 UDP 端口信息的分隔符：

- 地址/端口分隔符：冒号 (:)
- 端口分隔符：逗号 (,)
- 接口分隔符：分号 (;)

## <a name="configuring-network-access-servers"></a>配置网络访问服务器

请确保使用在 NPSs 上配置的相同 RADIUS UDP 端口号配置网络访问服务器。 RFC 2865 和 2866 中定义的 RADIUS 标准 UDP 端口是用于身份验证的 1812 和用于记帐的 1813；然而，默认情况下某些访问服务器配置为使用用于身份验证请求的 UDP 端口 1645 和用于记帐请求的 UDP 端口 1646。

>[!IMPORTANT]
>如果不使用 RADIUS 默认端口号，则必须在本地计算机的防火墙上配置例外，以允许在新端口上进行 RADIUS 流量。 有关详细信息，请参阅为[RADIUS 流量配置防火墙](nps-firewalls-configure.md)。

## <a name="configure-the-multihomed-nps"></a>配置多宿主 NPS

你可以使用以下过程来配置多宿主 NPS。

若要完成该过程，必须至少具有 **Domain Admins** 的成员资格或同等权限。

### <a name="to-specify-the-network-adapter-and-udp-ports-that-nps-uses-for-radius-traffic"></a>指定 NPS 用于 RADIUS 流量的网络适配器和 UDP 端口的步骤

1. 在服务器管理器中，单击 "**工具**"，然后单击 "**网络策略服务器**" 以打开 NPS 控制台。

2. 右键单击 "**网络策略服务器**"，然后单击 "**属性**"。

3. 单击 "**端口**" 选项卡，并预先为要用于 RADIUS 流量的网络适配器的 IP 地址添加到现有端口号。 例如，如果要将 IP 地址192.168.1.2 和 RADIUS 端口1812和1645用于身份验证请求，请将端口设置从**1812、1645**改为**192.168.1.2：1812、1645**。 如果 RADIUS 身份验证和 RADIUS 记帐 UDP 端口与默认值不同，请相应更改端口设置。

4. 若要为身份验证或记帐请求使用多个端口设置，请用逗号分隔端口号。

有关 NPS UDP 端口的详细信息，请参阅[配置 NPS Udp 端口信息](nps-udp-ports-configure.md)


有关 NPS 的详细信息，请参阅[网络策略服务器](nps-top.md)

