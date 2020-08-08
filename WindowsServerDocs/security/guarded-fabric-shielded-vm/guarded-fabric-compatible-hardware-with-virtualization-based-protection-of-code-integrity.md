---
title: 兼容硬件与基于 Windows Server 虚拟化的代码完整性保护
ms.topic: article
ms.assetid: 15ded82c-f70f-4efb-9e26-2731127931af
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 616718b2b2a5ce3c30655d3fef37da5ee2ea25e5
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87971354"
---
# <a name="compatible-hardware-with-windows-server-virtualization-based-protection-of-code-integrity"></a>兼容硬件与基于 Windows Server 虚拟化的代码完整性保护

>适用于： Windows Server 2019、Windows Server (半年频道) 、Windows Server 2016

Windows Server 2016 引入了新的基于虚拟化的代码保护，以帮助保护物理计算机和虚拟机免受修改系统代码的攻击。
为了实现这一高保护级别，Microsoft 将与计算机硬件制造商 (原始设备制造商或 Oem) ，以防止恶意写入系统执行代码。
此保护可以应用于任何系统，并用作构建基块之一，用于实现受防护虚拟机 (Vm) 的 Hyper-v 主机运行状况。

与任何基于硬件的保护一样，某些系统可能不合规，因为有一些问题（如内存页标记错误）作为可执行文件或在运行时实际尝试修改代码，这可能会导致意外失败，包括数据丢失或蓝屏错误 (也称为 "停止错误) "。

若要兼容并完全支持新的安全功能，Oem 需要实现在 2.6 2016 年1月发布的 UEFI 中定义的内存地址表。
采用新的 UEFI 标准需要一些时间;同时，为了防止客户遇到问题，我们需要提供有关已使用此功能设置的系统和配置以及我们知道不兼容的系统的信息。

## <a name="non-compatible-systems"></a>不兼容的系统

已知以下配置与基于虚拟化的代码完整性保护不兼容，并且无法用作受防护的 Vm 的主机：

- 运行 PERC H330 RAID 控制器的 dell PowerEdge 服务器有关详细信息，请参阅以下文章： Dell 支持 H330 中的以下文章[-启用 "主机保护者 Hyper-v 支持" 或 Win 2016 OS 上的 "Device Guard" 导致操作系统启动失败](http://www.dell.com/Support/Article/us/en/19/QNA44045)。


## <a name="compatible-systems"></a>兼容系统

这些是我们和我们的合作伙伴在我们的环境中进行测试的系统。
请确保在您的环境中验证系统是否正常工作：

- 虚拟机–可以在从 Windows Server 2016 开始的 Hyper-v 主机上运行的虚拟机上，启用基于虚拟化的代码完整性保护。



