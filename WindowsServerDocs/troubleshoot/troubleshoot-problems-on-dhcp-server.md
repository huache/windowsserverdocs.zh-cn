---
title: 排查 DHCP 服务器上的问题
description: 此 artilce 介绍了如何排查 DHCP 服务器上的问题并收集数据。
ms.prod: windows-server
ms.service: na
manager: dcscontentpm
ms.technology: server-general
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: 5ec2ef358cfaf7841b093843848f2ea5ee42433e
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181893"
---
# <a name="troubleshoot-problems-on-the-dhcp-server"></a>排查 DHCP 服务器上的问题

本文介绍如何解决在 DHCP 服务器上出现的问题。

## <a name="troubleshooting-checklist"></a>故障排除清单

检查以下设置：

  - DHCP 服务器服务已启动并正在运行。 若要检查此设置，请运行**net start**命令，然后查找**DHCP 服务器**。

  - DHCP 服务器已获得授权。 请参阅[在加入域的方案中的 WINDOWS DHCP 服务器授权](https://docs.microsoft.com/openspecs/windows_protocols/ms-dhcpe/56f8870b-a7c1-4db1-8a86-f69079fe5077)。

  - 验证 DHCP 客户端所在的子网的 DHCP 服务器作用域中是否存在 IP 地址租约。 为此，请在 DHCP 服务器管理控制台中查看适当范围的统计信息。

  - 检查是否 \_ 可以在 "地址租约" 中找到任何错误的地址列表。

  - 检查网络上的任何设备是否有未从 DHCP 作用域中排除的静态 IP 地址。

  - 验证 DHCP 服务器绑定到的 IP 地址是否在必须从中租用 IP 地址的作用域的子网内。这是因为没有中继代理可用。 为此，请运行**DhcpServerv4Binding**或**DhcpServerv6Binding** cmdlet。

  - 验证是否只有 DHCP 服务器在 UDP 端口67和68上进行侦听。 其他进程或其他服务（如 WDS 或 PXE）都不应占用这些端口。 为此，请运行 `netstat -anb` 命令。

  - 如果正在处理 IPsec 部署的环境，请验证是否添加了 DHCP 服务器 IPsec 例外。

  - 验证是否可以从 DHCP 服务器 ping 中继代理的 IP 地址。

  - 枚举并检查配置的 DHCP 策略和筛选器。

## <a name="event-logs"></a>事件日志

检查系统和 DHCP 服务器服务事件日志（**应用程序和服务日志** \> **Microsoft** \> **Windows** \> **DHCP 服务器**）中是否存在与发现的问题相关的报告问题。
根据问题的类型，会将事件记录到以下事件通道之一： [dhcp 服务器操作事件](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\)) 
 [dhcp 服务器管理事件](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\)) 
 [dhcp 服务器系统事件](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\)) 
 [dhcp 服务器筛选器通知事件](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\)) 
 [dhcp 服务器审核事件](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))

## <a name="data-collection"></a>数据收集

### <a name="dhcp-server-log"></a>DHCP 服务器日志

DHCP 服务器服务调试日志提供了有关 IP 地址租约分配以及 DHCP 服务器执行的 DNS 动态更新的详细信息。 默认情况下，这些日志位于% windir% \\ System32 \\ Dhcp 中。
有关详细信息，请参阅[分析 DHCP 服务器日志文件](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd183591\(v=ws.10\))。

### <a name="network-trace"></a>网络跟踪

关联网络跟踪可能指示在记录事件时 DHCP 服务器正在执行的操作。 若要创建此类跟踪，请执行以下步骤：

1.  请参阅[GitHub](https://github.com/CSS-Windows/WindowsDiag/tree/master/ALL/TSS)，并下载[tss \_tools.zip](https://github.com/CSS-Windows/WindowsDiag/blob/master/ALL/TSS/tss_tools.zip)文件。

2.  复制 Tss \_tools.zip 文件，并将其扩展到本地磁盘上的某个位置，如 C： \\ tools 文件夹。

3.  \\在提升的命令提示符窗口中从 C：工具运行以下命令：
    ```console
    TSS Ron Trace <Stop:Evt:>20321:<Other:>DhcpAdminEvents NoSDP NoPSR NoProcmon NoGPresult
    ```

    >[!Note]
    >在此命令中，将和替换为要在 \<*Stop:Evt:*\> \<*Other:*\> 跟踪会话中重点关注的事件 ID 和事件通道。
    >\_ \_ Tsstools.zip 文件中包含的 Tss 自述文件Help.docx 文件提供了 \_ 有关所有可用设置的详细信息。

4.  触发事件后，该工具会创建一个名为 C： \\ MS 数据的文件夹 \_ 。 此文件夹将包含一些有用的输出文件，这些文件提供有关计算机的网络和域配置的一般信息。
    此文件夹中最关注的文件是% Computername% \_ date \_ time \_ packetcapture \_ InternetClient \_ dbg。
    通过使用[网络监视器](https://www.microsoft.com/download/4865)应用程序，可以加载文件，并在 "DHCP 或 DNS" 协议上设置显示筛选器，以检查后台发生的情况。
