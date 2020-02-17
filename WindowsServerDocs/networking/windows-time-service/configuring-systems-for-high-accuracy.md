---
ms.assetid: ''
title: 配置系统以实现高精度
description: Windows 10 和 Windows Server 2016 中的时间同步已大幅改善。  在合理的操作条件下，可将系统配置为维持 1ms（毫秒）的精度或更高的精度（相对于 UTC）。
author: shortpatti
ms.author: dacuo
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: b7cd256fdbbdbe7432e5b5d5b16254314132560f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405199"
---
# <a name="configuring-systems-for-high-accuracy"></a>配置系统以实现高精度
>适用于：Windows Server 2016 和 Windows 10 版本 1607 或更高版本

Windows 10 和 Windows Server 2016 中的时间同步已大幅改善。  在合理的操作条件下，可将系统配置为维持 1ms（毫秒）的精度或更高的精度（相对于 UTC）。

以下指南将有助于配置系统以实现高精度。  本文讨论了以下要求：

- 支持的操作系统
- 系统配置 

> [!WARNING]
> **先前的操作系统精度目标**<br>
>Windows Server 2012 R2 及更低版本无法满足同样的高精度目标。 这些操作系统不支持高精度。
>
>在这些版本中，Windows 时间服务满足以下要求：
>
> - 提供了满足 Kerberos 版本 5 身份验证要求所需的时间精度。
> - 为加入到公共 Active Directory 林的 Windows 客户端和服务器提供了大致准确的时间。
>
>2012 R2 及更低版本的较高容差超出了 Windows 时间服务的设计规范。

## <a name="windows-10-and-windows-server-2016-default-configuration"></a>Windows 10 和 Windows Server 2016 默认配置

虽然 Windows 10 或 Windows Server 2016 上支持高达 1 ms 的精度，但大多数客户并不需要高度精确的时间。

因此，默认配置旨在满足与先前的操作系统相同的要求，目的是  ：

- 提供满足 Kerberos 版本 5 身份验证要求所需的时间精度。
- 为加入到公共 Active Directory 林的 Windows 客户端和服务器提供大致准确的时间。

## <a name="how-to-configure-systems-for-high-accuracy"></a>如何配置系统以实现高精度

>[!IMPORTANT]
>**有关高精度系统的可支持性的说明**<br>
> 时间精度需要准确时间从权威时间源到终端设备进行端到端分布。  沿此路径在测量中增加不对称性的任何因素都会对精度产生负面影响，从而影响设备的精度。
>
>出于此原因，我们编写了文档[用于针对高精度环境配置 Windows 时间服务的支持边界](support-boundary.md)，其中概述了要实现高精度目标必须满足的环境要求。

### <a name="operating-system-requirements"></a>操作系统要求

高精度配置需要 Windows 10 或 Windows Server 2016。  时间拓扑中的所有 Windows 设备都必须满足此要求，包括更高层次的 Windows 时间服务器以及在虚拟化方案中运行时间敏感型虚拟机的 Hyper-V 主机。 所有这些设备都必须至少为 Windows 10 或 Windows Server 2016。

在下面所示的插图中，需要高精度的虚拟机运行 Windows 10 或 Windows Server 2016。  同样，虚拟机所在的 Hyper-V 主机以及上游 Windows 时间服务器也必须运行 Windows Server 2016。

![时间拓扑 - 1607](../media/Windows-Time-Service/Configuring-Systems-for-High-Accuracy/Topology2016.png)


>[!TIP] 
>**确定 Windows 版本**<br>
> 可以在命令提示符下运行命令 `winver` 来验证 OS 版本是否为 1607（或更高版本），以及 OS 版本是否为 14393（或更高版本），如下所示：
>
> ![Winver - 2016 1607](../media/Windows-Time-Service/Configuring-Systems-for-High-Accuracy/winver2016.png)

### <a name="system-configuration"></a>系统配置

达到高精度目标需要进行系统配置。  可以通过多种方式来执行此配置，包括直接在注册表中执行或通过组策略。  有关这些设置的详细信息，请参阅 Windows 时间服务技术参考 - [Windows 时间服务工具](Windows-Time-Service-Tools-and-Settings.md#windows-time-service-tools)。

#### <a name="windows-time-service-startup-type"></a>Windows 时间服务启动类型

Windows 时间服务 (W32Time) 必须持续运行。  为此，请将 Windows 时间服务的启动类型配置为“自动”启动。

![自动配置](../media/Windows-Time-Service/Configuring-Systems-for-High-Accuracy/AutomaticService.PNG)

#### <a name="cumulative-one-way-network-latency"></a>累积单向网络延迟

测量的不确定性和“干扰”随着网络延迟的增加而增加。  因此，网络延迟必须在合理的范围内。  具体要求取决于目标精度，[用于针对高精度环境配置 Windows 时间服务的支持边界](support-boundary.md)中提供了概述。

若要计算累积单向网络延迟，请将时间拓扑（从目标开始，到高精度第 1 层次时间源结束）中的 NTP 客户端 - 服务器节点对之间的各个单向延迟进行相加。

例如：请考虑包含高精度源、两个中间 NTP 服务器 A 和 B 以及按此顺序排列的目标计算机的时间同步层次结构。 若要获取目标和源之间的累计网络延迟，请测量以下项之间各自的平均 NTP 往返时间 (RTT)：

- 目标和时间服务器 B
- 时间服务器 B 和时间服务器 A
- 时间服务器 A 和源

可以使用收件箱 w32tm.exe 工具获取此度量。  若要实现此目的，请执行以下操作：

1. 从目标和时间服务器 B 执行计算。
    
    `w32tm /stripchart /computer:TimeServerB /rdtsc /samples:450 > c:\temp\Target_TsB.csv`

2. 从时间服务器 b 对（指向）时间服务器 a 执行计算。
    
    `w32tm /stripchart /computer:TimeServerA /rdtsc /samples:450 > c:\temp\Target_TsA.csv`

3. 从时间服务器 a 对源执行计算。
 
4. 接下来，添加在上一步中测量的平均 RoundTripDelay 并除以 2，获取目标和源之间的累计网络延迟。

#### <a name="registry-settings"></a>注册表设置

# <a name="minpollintervaltabminpollinterval"></a>[MinPollInterval](#tab/MinPollInterval)
配置允许系统轮询的最小间隔（以 log2 秒为单位）。

|  |  | 
|---------|---------|
|密钥位置     | HKLM:\SYSTEM\CurrentControlSet\Services\W32Time\Config        |
|设置    | 6        |
|结果 | 最小轮询间隔现为 64 秒。 |

以下命令将指示 Windows 时间获取更新的设置：

`w32tm /config /update`


# <a name="maxpollintervaltabmaxpollinterval"></a>[MaxPollInterval](#tab/MaxPollInterval)
配置允许系统轮询的最大间隔（以 log2 秒为单位）。

|  |  |  
|---------|---------|
|密钥位置     | HKLM:\SYSTEM\CurrentControlSet\Services\W32Time\Config        |
|设置    | 6        |
|结果 | 最大轮询间隔现为 64 秒。  |

以下命令将指示 Windows 时间获取更新的设置：

`w32tm /config /update`

# <a name="updateintervaltabupdateinterval"></a>[UpdateInterval](#tab/UpdateInterval)
相位校正调整之间的时钟周期数。

|  |  |  
|---------|---------|
|密钥位置     | HKLM:\SYSTEM\CurrentControlSet\Services\W32Time\Config       |
|设置    | 100        |
|结果 | 相位校正调整之间的时钟周期数现为 100。 |

以下命令将指示 Windows 时间获取更新的设置：

`w32tm /config /update`

# <a name="specialpollintervaltabspecialpollinterval"></a>[SpecialPollInterval](#tab/SpecialPollInterval)
配置启用 SpecialInterval 0x1 标志后的轮询间隔（以秒为单位）。

|  |  |  
|---------|---------|
|密钥位置     | HKLM:\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\NtpClient        |
|设置    | 64        |
|结果 | 轮询间隔现为 64 秒。 |

以下命令将重新启动 Windows 时间以获取更新的设置：

`net stop w32time && net start w32time`

# <a name="frequencycorrectratetabfrequencycorrectrate"></a>[FrequencyCorrectRate](#tab/FrequencyCorrectRate)

|  |  |  
|---------|---------|
|密钥位置     | HKLM:\SYSTEM\CurrentControlSet\Services\W32Time\Config      |
|设置    | 2        |


---
