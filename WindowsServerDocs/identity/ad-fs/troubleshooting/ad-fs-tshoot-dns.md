---
title: AD FS 故障排除-DNS 解析
description: 本文档介绍如何排查 AD FS 的 DNS 方面
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.openlocfilehash: b0134478ce0a4e91d6e33d5a0845a2be5df53d3f
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954173"
---
# <a name="ad-fs-troubleshooting---dns"></a>AD FS 疑难解答-DNS
首先要检查的是，如果 AD FS 不起作用或未响应，则是 DNS 名称解析。  这些是基本测试，用于确定在网络中是否找到 AD FS 服务器或 WAP 服务器。  对于内部用户，这些测试应该解析为 (STS) AD FS 服务器。    对于外部用户，这些测试应该解析为 WAP 服务器。

本文档的其余部分将演示如何使用命令行工具执行快速名称解析检查。

## <a name="ping-test"></a>Ping 测试
通过向另一台 TCP/IP 计算机发送 Internet 控制消息协议 (ICMP) 回响请求消息来验证 IP 级连接。 将显示相应的回响回复消息以及往返时间。  有关详细信息，请参阅[Ping](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff961503(v=ws.11))。


>[!NOTE]
>请注意，某些组织会在其服务器上阻止此端口，并且你可能会收到**请求超时**响应。

### <a name="to-use-a-ping-test"></a>使用 PING 测试
1.  打开命令提示符
2. 输入 PING <name of adfs server> a。 示例： PING sts.contoso.com
3. 你应看到来自服务器的答复

![Ping](media/ad-fs-tshoot-dns/dns1.png)

## <a name="nslookup"></a>NSLookup
显示可用于诊断域名系统 (DNS) 基础结构的信息。  有关详细信息，请参阅[NSLookup](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc725991(v=ws.11))。

### <a name="to-use-a-nslookup"></a>使用 NSLookup
1.  打开命令提示符
2. 输入 PING <name of adfs server> a。 示例： nslookup sts.contoso.com
3. 应看到服务器 NSLookup 的 dns 信息 ![](media/ad-fs-tshoot-dns/dns2.png)

## <a name="tracert"></a>Tracert
通过向目标发送 Internet 控制消息协议)  (（ (ICMP) 回响请求或 ICMPv6 消息），确定到达目标的路径。   有关详细信息，请参阅[Tracert](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ff961507(v=ws.11))。


### <a name="to-use-tracert"></a>使用 Tracert
1.  打开命令提示符
2. 输入 tracert <name of adfs server> a。 示例： tracert sts.contoso.com
3. 应该会看到用于访问服务器 Tracert 的目标路径 ![](media/ad-fs-tshoot-dns/dns3.png)

## <a name="next-steps"></a>后续步骤

- [AD FS 疑难解答](ad-fs-tshoot-overview.md)
