---
ms.assetid: e34622ff-b2d0-4f81-8d00-dacd5d6c215e
title: Windows 时间服务
description: ''
author: shortpatti
ms.author: pashort
manager: dougkim
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: e3dbaa188426ac81073e706db3adc6ab0a655c01
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405191"
---
# <a name="windows-time-service-w32time"></a>Windows 时间服务 (W32Time)

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows 10 或更高版本

Windows 时间服务 (W32Time) 为 Active Directory 域服务 (AD DS) 中运行的所有计算机同步日期和时间。 对于许多 Windows 服务和业务线 (LOB) 应用程序的正确操作，时间同步至关重要。 Windows 时间服务使用网络时间协议 (NTP) 来同步网络上的计算机时钟。 NTP 确保准确的时钟值（或时间戳）可以分配到网络验证和资源访问请求。

Windows 时间服务 (W32Time) 主题中提供了以下内容：
- **[Windows Server 2016 精确时间](accurate-time.md)。** Windows Server 2016 中的时间同步准确度已显著提高，同时保持早期 Windows 版本的完全向后 NTP 兼容性。 在合理的操作条件下，你可以为 Windows Server 2016 和 Windows 10 周年更新域成员根据 UTC 将时间差维持在 1 毫秒的准确度或更高准确度。
- **[高准确度环境的支持边界](support-boundary.md)。** 本文介绍 Windows 时间服务 (W32Time) 在需要高度准确和稳定系统时间的环境中的支持边界。
- **[配置高准确度的系统](configuring-systems-for-high-accuracy.md)。** Windows 10 和 Windows Server 2016 中的时间同步已大幅改善。  在合理的操作条件下，可将系统配置为维持 1ms（毫秒）的精度或更高的精度（相对于 UTC）。
- **[Windows 时间实现可追溯性](windows-time-for-traceability.md)。** 许多行业的法规都要求系统可追溯到 UTC。  这意味着可以根据 UTC 证明系统的偏移量。  为了启用法规合规性方案，Windows 10 和 Server 2016 需提供新的事件日志，以提供操作系统方面的信息，便于了解系统时钟上所执行的操作。  这些事件日志会为 Windows 时间服务持续生成，并且可以进行检查或存档以便进行后续分析。
- **[Windows 时间服务技术参考](windows-time-service-tech-ref.md)。** W32Time 服务为计算机提供网络时钟同步，而无需进行大量配置。 W32Time 服务对于成功运行 Kerberos V5 身份验证非常重要，因此对于基于 AD DS 的身份验证也很重要。
    - **[Windows 时间服务的工作原理](How-the-Windows-Time-Service-Works.md)。** 虽然 Windows 时间服务并不完全是网络时间协议 (NTP) 的实现，但它使用 NTP 规范中定义的一套复杂算法来确保整个网络中的计算机上的时钟尽可能精确。
    - **[Windows 时间服务工具和设置](Windows-Time-Service-Tools-and-Settings.md)。** 大多数域成员计算机的时间客户端类型为 NT5DS，这意味着它们会从域层次结构同步时间。 唯一的例外是，充当主域控制器 (PDC) 仿真器的域控制器操作林根域的主机，通常配置为使用外部时间源同步时间。


## <a name="related-topics"></a>“相关主题”
有关域层次结构和评分系统的详细信息，请参阅[“什么是 Windows 时间服务？”](https://blogs.msdn.microsoft.com/w32time/2007/07/07/what-is-windows-time-service/) 博客文章。

Windows 时间提供程序插件模型[记录在 TechNet 上](https://msdn.microsoft.com/library/windows/desktop/ms725475%28v=vs.85%29.aspx)。

可在[此处](https://windocs.blob.core.windows.net/windocs/WindowsTimeSyncAccuracy_Addendum.pdf)下载“Windows 2016 精确时间”一文中引用的附录

若要快速了解 Windows 时间服务，请参阅此[高级概述视频](https://aka.ms/WS2016TimeVideo)。
