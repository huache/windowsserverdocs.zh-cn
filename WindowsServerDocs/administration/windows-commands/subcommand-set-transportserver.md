---
title: 子命令集-TransportServer
description: 子命令集的参考文章-TransportServer，用于设置传输服务器的配置设置。
ms.topic: article
ms.assetid: 7863225c-f4b2-4cd0-b929-78a454bef249
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b7725101bcc2230a07c8082f9a57b85d411e80d
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87882123"
---
# <a name="subcommand-set-transportserver"></a>子命令： set-TransportServer

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

设置传输服务器的配置设置。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Set-TransportServer [/Server:<Server name>]
     [/ObtainIpv4From:{Dhcp | Range}]
        [/start:<starting IP address>]
        [/End:<Ending IP address>]
     [/ObtainIpv6From:Range]\n\
        [/start:<start IP address>]\n\
        [/End:<End IP address>]
     [/startPort:<starting port>
        [/EndPort:<starting port>
     [/Profile:{10Mbps | 100Mbps | 1Gbps | Custom}]
     [/MulticastSessionPolicy]
             [/Policy:{None | AutoDisconnect | Multistream}]
                 [/Threshold:<Speed in KBps>]
                 [/StreamCount:{2 | 3}]
                 [/Fallback:{Yes | No}]
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server： <Server name> ]|指定传输服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名 (FQDN) 。 如果未指定传输服务器名称，则使用本地服务器。|
|[/ObtainIpv4From： {Dhcp &#124; 范围}]|设置 IPv4 地址的源，如下所示：<p>-[/start： <IP address> ] 设置 IP 地址范围的起始地址。 这是必需的，仅当此选项设置为 "**范围**" 时才有效。<br />-[/End： <IP address> ] 设置 IP 地址范围的结尾。 这是必需的，仅当此选项设置为 "**范围**" 时才有效。<br />-[/startPort： <port> ] 设置端口范围的开头。<br />-[/EndPort： <port> ] 设置端口范围的结尾。|
|[/ObtainIpv6From： Range]|指定 IPv6 地址的源。 此选项仅适用于 Windows Server 2008 R2，唯一受支持的值为**范围**。<p>-[/start： <IP address> ] 设置 IP 地址范围的起始地址。 这是必需的，仅当此选项设置为 "**范围**" 时才有效。<br />-[/End： <IP address> ] 设置 IP 地址范围的结尾。 这是必需的，仅当此选项设置为 "**范围**" 时才有效。<br />-[/startPort： <port> ] 设置端口范围的开头。<br />-[/EndPort： <port> ] 设置端口范围的结尾。|
|[/Profile： {10Mbps &#124; 100Mbps &#124; 1Gbps &#124; 自定义}]|指定要使用的网络配置文件。 此选项仅适用于运行 Windows Server 2008 或 Windows Server 2003 的服务器。|
|[/MulticastSessionPolicy]|配置多播传输的传输设置。 此命令仅适用于 Windows Server 2008 R2。<p>-[/Policy： {None &#124; AutoDisconnect &#124; Multistream}] 确定如何处理速度缓慢的客户端。 "**无**" 表示将所有客户端保持在一个会话中的速度相同。 **AutoDisconnect**表示断开连接到指定 **/Threshold**以下的任何客户端。 **Multistream**表示客户端将被划分为 **/StreamCount**指定的多个会话。<br />-[/Threshold： <Speed in KBps> ] 设置/policy 的最小传输速率（KBps） **： AutoDisconnect**。 低于此速率的客户端将与多播传输断开连接。<br />-[/StreamCount： {2 &#124; 3}] [/Fallback： {Yes &#124; No}] 确定/Policy 的会话数 **： Multistream**。 **2**表示两个会话 (速度快、速度缓慢) ， **3**表示三个会话 (慢、中、快) 。<br />-[/Fallback： {Yes &#124; No}] 确定是否断开客户端的连接将使用另一种方法来继续传输 (如果客户端) 支持此方法。 如果你使用的是 WDS 客户端，则计算机将回退为单播。 Wdsmcast.exe 不支持回退机制。 此选项也适用于不支持**Multistream**的客户端。 在这种情况下，计算机将回退到其他方法，而不是移到较慢的传输会话。|
## <a name="examples"></a>示例
若要设置服务器的 IPv4 地址范围，请键入：
```
wdsutil /Set-TransportServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100
```
若要为服务器设置 IPv4 地址范围、端口范围和配置文件，请键入：
```
wdsutil /Set-TransportServer /Server:MyWDSServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100 /startPort:12000 /EndPort:50000 /Profile:10mbps
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 TransportServer 命令](using-the-disable-transportserver-command.md) 
[使用 TransportServer 命令](using-the-enable-transportserver-command.md) 
[使用 TransportServer 命令](using-the-get-transportserver-command.md) 
[子命令： TransportServer](subcommand-start-transportserver.md) 
[子命令： TransportServer](subcommand-stop-transportserver.md)
