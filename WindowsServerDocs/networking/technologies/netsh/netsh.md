---
title: Network Shell (Netsh)
description: 本主题概述了 Windows Server 2016 中的 Network Shell (netsh) 命令行实用工具。
ms.topic: article
ms.assetid: aedef092-8445-4e53-b9d4-525ecd98b02d
manager: dougkim
ms.author: lizross
author: eross-msft
ms.date: 09/13/2018
ms.openlocfilehash: 1f331a7ea987f413f814dcb1b0e4173714b1153b
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87994614"
---
# <a name="network-shell-netsh"></a>Network Shell \(Netsh\)

>适用于：Windows Server（半年频道）、Windows Server 2016

Network shell (netsh) 是一种命令行实用工具，使用该工具，你可以在运行 Windows Server 2016 的计算机上安装网络通信服务器组件之后配置和显示各种网络通信服务器角色和组件的状态。

一些客户端技术，例如动态主机配置协议 \(DHCP\) 客户端和BranchCache，也提供 netsh 命令，通过这些命令，你可以配置运行 Windows 10 的客户端计算机。

在大多数情况下，netsh 命令提供的功能与你使用每个网络服务器角色或网络功能的 Microsoft 管理控制台 \(MMC\) 管理单元时提供的功能相同。 例如，可以使用 NPS MMC 管理单元或 netsh nps 上下文中的 netsh 命令来配置网络策略服务器 \(NPS\)  。

此外，还有一些用于网络技术的 netsh 命令，例如用于 IPv6、网桥和远程过程调用 \(RPC\) 的命令，这些命令在Windows Server 中不能作为 MMC 管理单元使用。

>[!IMPORTANT]
>建议使用 Windows PowerShell（而非使用 Network Shell）管理 [Windows Server 2016 和 Windows 10](/powershell/windows/get-started?view=win10-ps) 中的网络技术。 但是，为了与脚本兼容，其中包含了 Network Shell 并支持使用。

## <a name="network-shell-netsh-technical-reference"></a>Network Shell (Netsh) 技术参考

Netsh 技术参考提供了全面的 netsh 命令参考，包括语法、参数和 netsh 命令的示例。 可以使用 Netsh 技术参考构建脚本和批处理文件，方法是使用 netsh 命令在运行 Windows Server 2016 和 Windows 10 的计算机上对网络技术进行本地或远程管理。

### <a name="content-availability"></a>内容可用性

可以从 TechNet 库中以 Windows Help \(*.chm\) 格式下载 Network Shell 技术参考：[Netsh 技术参考](https://gallery.technet.microsoft.com/Netsh-Technical-Reference-c46523dc)

---