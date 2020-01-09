---
title: SMB 多通道故障排除
description: 介绍 SMB 多通道故障排除方法。
author: Deland-Han
manager: dcscontentpm
audience: ITPro
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 91f034a0062f509b1185f04554af4383022a68e1
ms.sourcegitcommit: 8cf04db0bc44fd98f4321dca334e38c6573fae6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654538"
---
# <a name="smb-multichannel-troubleshooting"></a>SMB 多通道故障排除

本文介绍如何解决与 SMB 多通道相关的问题。

## <a name="check-the-network-interface-status"></a>检查网络接口状态

请确保 SMB 客户端（MS\_客户端）和 SMB 服务器（MS\_服务器）上的网络接口绑定设置为**True** 。 运行以下命令时 **，对于这**两个网络接口，输出应显示为 "**真**"：

```PowerShell
Get-NetAdapterBinding -ComponentID ms_server,ms_msclient
```

之后，请确保在以下命令的输出中列出了网络接口：

```PowerShell
Get-SmbServerNetworkInterface
```

```PowerShell
Get-SmbClientNetworkInterface
```

您还可以运行**get-netadapter**命令来查看接口索引以验证结果。 接口索引显示主动绑定到相应接口的所有活动 SMB 适配器。

## <a name="check-the-firewall"></a>检查防火墙

如果只有链接本地 IP 地址，并且没有可公开路由的地址，则网络配置文件可能会设置为 "**公共**"。 这意味着 SMB 在默认情况下会在防火墙上被阻止。

以下命令显示正在使用的连接配置文件。 你还可以使用 "网络和共享中心" 来检索此信息。

**NetConnectionProfile**

在 "**文件和打印机共享**" 组下，检查防火墙入站规则，以确保为正确的配置文件启用了 "SMB 传入"。

![SMB-in 规则](media/smb-multichannel-troubleshooting-1.png)

还可以在 "**网络和共享中心**" 窗口中启用 "**文件和打印机共享**"。 为此，请在左侧菜单中选择 "**更改高级共享设置**"，然后为配置文件选择 **"打开文件和打印机共享**"。 此选项启用 "文件和打印机共享" 防火墙规则。

![“更改高级共享设置”，](media/smb-multichannel-troubleshooting-2.png)

## <a name="capture-client-and-server-sided-traffic-for-troubleshooting"></a>捕获客户端和服务器端流量以进行故障排除

需要从 TCP 三向握手开始的 SMB 连接跟踪信息。 建议你在开始捕获前关闭所有应用程序（尤其是 Windows 资源管理器）。 在 SMB 客户端上重新启动**工作站**服务，启动数据包捕获，然后重现该问题。

请确保正在协商*SMBv3 连接，* 并且服务器和客户端之间的任何内容都不会影响方言协商。 SMBv2 及更早版本不支持多通道。

查找网络\_接口\_信息数据包。 SMB 客户端从 SMB 服务器请求适配器列表。 如果未交换这些数据包，多通道将不起作用。

服务器通过返回有效网络接口的列表来做出响应。 然后，SMB 客户端将它们添加到多通道的可用适配器列表中。 此时，多通道应启动，至少尝试启动连接。

有关详细信息，请参阅以下文章：

- [查询服务器的网络接口的3.2.4.20.10 应用程序请求](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/147adde4-d936-4597-924a-8caa3429c6b0)

- [2.2.32.5 NETWORK\_INTERFACE\_INFO Response](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/fcd862d1-1b85-42df-92b1-e103199f531f)

- [3.2.5.14.11 处理网络接口响应](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/5459722b-1eaa-4ead-b465-284363264cad)

在以下方案中，无法使用适配器：

- 客户端上出现路由问题。 这通常是由于不正确的路由表导致流量超出错误的接口。

- 已设置多通道约束。 有关详细信息，请参阅[SmbMultichannelConstraint](https://docs.microsoft.com/powershell/module/smbshare/new-smbmultichannelconstraint)。

- 某个对象阻止了网络接口请求和响应数据包。

- 客户端和服务器无法通过额外的网络接口进行通信。 例如，TCP 三向握手失败，连接被防火墙阻止，会话设置失败，等等。

如果适配器及其 IPv6 地址位于服务器发送的列表中，则下一步是查看是否通过该接口来尝试通信。 按链路本地地址和 SMB 流量筛选跟踪，并查找连接尝试。 如果这是一个 Test-netconnection 跟踪，还可以检查 Windows 筛选平台（WFP）事件以查看连接是否被阻止。
