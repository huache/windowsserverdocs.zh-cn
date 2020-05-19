---
ms.assetid: 6086947f-f9ef-4e18-9f07-6c7c81d7002c
title: Windows 时间服务工具和设置
author: Teresa-Motiv
ms.author: v-tea
ms.date: 02/24/2020
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: 2f6ba34381e813247d0838853f688abf13fbd2fa
ms.sourcegitcommit: 1d83ca198c50eef83d105151551c6be6f308ab94
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605537"
---
# <a name="windows-time-service-tools-and-settings"></a>Windows 时间服务工具和设置

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows 10 或更高版本

在本主题中，你将了解 Windows 时间服务 (W32Time) 的工具和设置。  

如果只想同步已加入域的客户端计算机的时间，请参阅 [Configure a client computer for automatic domain time synchronization](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc816884%28v%3dws.10%29)（配置客户端计算机以自动同步域时间）。 有关如何配置 Windows 时间服务的其他主题，请参阅[在何处查找 Windows 时间服务配置信息](windows-time-service-top.md)。  

> [!CAUTION]  
> 不应使用 **Net time** 命令来配置或设置 Windows 时间服务运行的时间。  
>
> 此外，在运行 Windows XP 或更早版本的较旧计算机上，**Net time /querysntp** 命令会显示网络时间协议 (NTP) 服务器的名称。可以将某台计算机配置为与该 NTP 服务器同步，但仅当计算机的时间客户端配置为 NTP 或 AllSync 时，才可使用该服务器。 该命令已被弃用。  

大多数域成员计算机的时间客户端类型为 NT5DS，这意味着它们会从域层次结构同步时间。 通常情况下，这方面唯一的例外是充当林根域的主域控制器 (PDC) 仿真器操作主机的域控制器。 PDC 仿真器操作主机通常配置为使用外部时间源来同步时间。 若要查看计算机的时间客户端配置（从 Windows Server 2008 和 Windows Vista 开始），请从提升的命令提示符处运行 **W32tm /query /configuration** 命令，然后在命令输出中读取“类型”行。 有关详细信息，请参阅 [Windows 时间服务的工作原理](How-the-Windows-Time-Service-Works.md)。 另外，可以运行 **reg query HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Parameters** 命令，并在命令输出中读取 **NtpServer** 的值。  

> [!IMPORTANT]  
> 在 Windows Server 2016 之前，W32Time 服务并不是为了满足时间敏感型应用程序的需要。 但是，现在可以通过 Windows Server 2016 的更新在域中实现可达到一毫秒准确性的解决方案。 有关详细信息，请参阅 [Windows 2016 精确时间](accurate-time.md)和[用于针对高精度环境配置 Windows 时间服务的支持边界](support-boundary.md)。  

## <a name="windows-time-service-tools"></a>Windows 时间服务工具  

以下工具与 Windows 时间服务相关联。  

### <a name="w32tmexe-windows-time"></a>W32tm.exe：Windows 时间  

**类别**  

此工具是 Windows（Windows XP 及更高版本）和 Windows Server（Windows Server 2003 及更高版本）的默认安装的一部分。  

**版本兼容性**  

此工具在 Windows（Windows XP 及更高版本）和 Windows Server（Windows Server 2003 及更高版本）的默认安装上运行。  

可以使用 W32tm.exe 来配置 Windows 时间服务设置并诊断时间服务问题。 W32tm.exe 是用于配置、监视 Windows 时间服务或排查其问题的首选命令行工具。  

下表描述了可通过 W32tm.exe 使用的参数。  

**W32tm.exe 主参数**  

|参数 |说明 |
| --- | --- |
|**w32tm /?** |显示 W32tm 命令行帮助 |
|**w32tm /register** |注册将作为服务运行的时间服务，并将其默认配置信息添加到注册表。 |
|**w32tm /unregister** |注销时间服务并从注册表中删除其所有配置信息。 |
|**w32tm /monitor [/domain:\<*domain name*>] [/computers:\<*name*>[,\<*name*>[,\<*name*>...]]] [/threads:\<*num*>]** |监视 Windows 时间服务。<p>**/domain**：指定要监视的域。 如果未指定域名，或未指定 **/domain** 和 **/computers** 选项，则使用默认域。 此选项可以多次使用。<p>**/computers**：监视给定列表的计算机。 计算机名称以逗号分隔，不含空格。 如果名称以 **\*** 为前缀，则将其视为 PDC。 此选项可以多次使用。<p>**/threads**：指定要同时分析的计算机数。 默认值为 3。 允许的范围为 1-50. |
|**w32tm /ntte \<NT *time epoch*>** |将 Windows NT 系统时间（以 10<sup>-7</sup> 秒为单位，从 1601 年 1 月 1 日 0 点开始进行度量）转换为可读格式。 |
|**w32tm /ntpte \<NTP *time epoch*>** |将 NTP 时间（以 2<sup>-32</sup> 秒为单位，从 1900 年 1 月 1 日 0 点开始进行度量）转换为可读格式。 |
|**w32tm /resync [/computer:\<*computer*>] [/nowait] [/rediscover] [/soft]** |告知计算机应该尽快重新同步其时钟，并丢弃所有累积的错误统计信息。<p>**/computer:\<*computer*>** ：指定应重新同步的计算机。 如果未指定，则本地计算机会重新同步。<p>**/nowait**：不等待重新同步，立即返回。 否则，请等待重新同步完成，然后再返回。<p>**/rediscover**：重新检测网络配置并重新发现网络源，然后重新同步。<p>**/soft**：使用现有错误统计信息重新同步。 不实用，为兼容性而提供。 |
|**w32tm /stripchart /computer:\<*target*> [/period:\<*refresh*>] [/dataonly] [/samples:\<*count*>] [/rdtsc]** |显示此计算机和另一台计算机之间偏移量的带状图。<p>**/computer:\<*target*>** ：将用作偏移量度量基准的计算机。<p>**/period:\<*refresh*>** ：采样间隔时间，以秒为单位。 默认值为 2 秒。<p>**/dataonly**：仅显示数据，不显示图形。<p>**/samples:\<*count*>** ：收集 \<*count*> 个样本，然后停止。 如果未指定，则按 Ctrl+C 后才会停止收集样本。<br/><br/>**/rdtsc**：对于每个示例，此选项输出逗号分隔的值以及 **RdtscStart**、**RdtscEnd**、**FileTime**、**RoundtripDelay** 和 **NtpOffset** 标头，而不输出文本图形。<br/><ul><li>**RdtscStart**：在生成 NTP 请求之前收集的 [RDTSC（读取时间戳计数器）](https://en.wikipedia.org/wiki/Time_Stamp_Counter)值。</li><li>**RdtscEnd**：在接收和处理 NTP 响应之后收集的 RDTSC 值。</li><li>**FileTime**：NTP 请求中使用的本地 FILETIME 值。</li><li>**RoundtripDelay**：从生成 NTP 请求到处理收到的 NTP 响应之间所用的时间（以秒为单位），根据 NTP 往返计算结果进行计算。</li><li>**NTPOffset**：本地计算机和 NTP 服务器之间的时间偏移量（以秒为单位），根据 NTP 偏移量计算结果进行计算。</li></ul> |
|**w32tm /config [/computer:\<*target*>] [/update] [/manualpeerlist:\<*peers*>] [/syncfromflags:\<*source*>] [/LocalClockDispersion:\<*seconds*>] [/reliable:(YES\|NO)] [/largephaseoffset:\<*milliseconds*>]** |**/computer:\<*target*>** ：调整 \<*target*> 的配置。 如果未指定，则默认值为本地计算机。<p>**/update**：通知时间服务配置已更改，使更改生效。<p>**/manualpeerlist:\<*peers*>** ：将手动对等列表设置为 \<*peers*>，它是以空格分隔的 DNS 和/或 IP 地址的列表。 指定多个对等方时，此选项必须用引号引起来。<p>**/syncfromflags:\<*source*>** ：设置 NTP 客户端应从哪些源同步。 \<*source*> 应该是这些以逗号分隔的关键字的列表（不区分大小写）：<ul><li>**MANUAL**：包括手动对等列表中的对等方。</li><li>**DOMHIER**：从域层次结构中的域控制器 (DC) 同步。</li></ul>**/LocalClockDispersion:\<*seconds*>** ：配置 W32Time 在无法从已配置的源获取时间时将采用的内部时钟的准确性。<p>**/reliable:(YES\|NO)** ：设置此计算机是否为可靠的时间源。 此设置仅对域控制器有用。<ul><li>**YES**：此计算机是可靠的时间服务。</li><li>**NO**：此计算机不是可靠的时间服务。</li></ul>**/largephaseoffset:\<*milliseconds*>** ：设置 W32Time 将其视为峰值的本地时间和网络时间之间的时间差。 |
|**w32tm /tz** |显示当前时区设置。 |
|**w32tm /dumpreg [/subkey:\<*key*>] [/computer:\<*target*>]** |显示与给定注册表项相关联的值。<p>默认项为 **HKLM\System\CurrentControlSet\Services\W32Time**（时间服务的根项）。<p>**/subkey:\<*key*>** ：显示与默认项的子项 <key> 相关联的值。<p>**/computer:\<*target*>** ：查询计算机 \<*target*> 的注册表设置 |
|**w32tm /query [/computer:\<*target*>] {/source \| /configuration \| /peers \| /status} [/verbose]** |显示计算机的 Windows 时间服务信息。 此参数首先在 Windows Vista 和 Windows Server 2008 的 Windows 时间客户端中提供。<p>**/computer:\<*target*>** ：查询 \<*target*> 的信息。 如果未指定，则默认值为本地计算机。<p>**/source**：显示时间源。<p>**/configuration**：显示运行时的配置以及设置的来源。 在详细模式下，也显示未定义或未使用的设置。<p>**/peers**：显示对等方及其状态的列表。<p>**/status**：显示 Windows 时间服务状态。<p>**/verbose**：设置详细模式以显示详细信息。 |
|**w32tm /debug {/disable \| {/enable /file:\<*name*> /size:/<*bytes*> /entries:\<*value*> [/truncate]}}** |启用或禁用本地计算机 Windows 时间服务专用日志。 此参数首先在 Windows Vista 和 Windows Server 2008 的 Windows 时间客户端中提供。<p>**/disable**：禁用专用日志。<p>**/enable**：启用专用日志。<ul><li>**file:\<*name*>** ：指定绝对文件名称。</li><li>**size:\<*bytes*>** ：指定循环日志记录的最大大小。</li><li>**entries:\<*value*>** ：包含通过数字指定且以逗号分隔的标志列表，用于指定应记录的信息的类型。 有效数值为 0 至 300。 数值范围和单个数字都有效，例如 0-100、103、106。 值 0-300 用于记录所有信息。</li></ul>**/truncate**：截断文件（如果存在）。 |

有关 **W32tm.exe** 的详细信息，请参阅 [Windows 帮助](https://support.microsoft.com/hub/4338813/windows-help?os=windows-10)。  

**示例**

如果要将本地 Windows 时间客户端设置为指向两个不同的时间服务器，一个名为 ntpserver.contoso.com，另一个名为 clock.adatum.com，请在命令行中键入以下命令，然后按 ENTER：

```cmd
w32tm /config /manualpeerlist:"ntpserver.contoso.com clock.adatum.com" /syncfromflags:manual /update
```

有关 Internet 上适用于外部时间同步的有效 NTP 服务器的列表，请参阅 [Internet 上可用的简单网络时间协议 (SNTP) 时间服务器的列表](https://go.microsoft.com/fwlink/?linkid=60401)。

若要从主机名为 CONTOSOW1 的基于 Windows 的客户端计算机检查 Windows 时间客户端配置，请运行以下命令：

```cmd
W32tm /query /computer:contosoW1 /configuration
```

此命令的输出是为 Windows 时间客户端设置的配置参数的列表。

## <a name="using-group-policy-to-configure-the-windows-time-service"></a>使用组策略配置 Windows 时间服务

Windows 时间服务将一些配置属性存储为注册表项。 可以使用组策略对象来配置此信息的大部分。 例如，可以使用 GPO 将计算机配置为 NTPServer 或 NTPClient、配置时间同步机制，或者将计算机配置为可靠时间源。  

> [!NOTE]  
> 可在 Windows Server 2003、Windows Server 2003 R2、Windows Server 2008 和 Windows Server 2008 R2 域控制器上配置 Windows 时间服务组策略设置，并且该设置只能应用于运行 Windows Server 2003、Windows Server 2003 R2、Windows Server 2008 和 Windows Server 2008 R2 的计算机。  

Windows 将 Windows 时间服务策略信息存储在**计算机配置\管理模板\系统\Windows 时间服务**下的 W32Time.admx 管理模板文件中。 它存储策略在注册表中定义的配置信息，并使用那些注册表项来配置 Windows 时间服务的注册表项。 因此，组策略定义的值会覆盖注册表的“Windows 时间服务”部分中的任何预先存在的值。

> [!IMPORTANT]  
> 某些预设 GPO 设置不同于相应的默认注册表项。 如果你计划使用 GPO 来配置任何 Windows 时间设置，请务必参阅 [Windows 时间服务组策略设置的预设值不同于 Windows Server 2003 中相应的 Windows 时间服务注册表项](https://go.microsoft.com/fwlink/?LinkId=186066)。 该问题适用于 Windows Server 2008 R2、Windows Server 2008、Windows Server 2003 R2 和 Windows Server 2003。

例如，假设你在“配置 Windows NTP 客户端”策略中编辑策略设置。

所做的更改存储在管理模板中的以下位置：

> **计算机配置\管理模板\系统\Windows 时间服务\时间提供程序\配置 Windows NTP 客户端**

Windows 将这些设置加载到以下子项下的注册表策略区域中：

> **HKLM\Software\Policies\Microsoft\W32time\TimeProviders\NtpClient**

然后，Windows 使用策略设置在以下子项下配置相关的 Windows 时间服务注册表项：

> **HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Time Providers\NTPClient\\**

下表列出了可以为 Windows 时间服务配置的策略，以及这些策略影响的注册表子项。

> [!NOTE]  
> 删除组策略设置后，Windows 会从注册表的策略区域中删除相应的条目。

|策略<sup>1</sup> |注册表位置<sup>2、</sup><sup>3</sup> |
| --- | --- |
|全局配置设置 |W32Time<br />W32Time\Config<br />W32Time\Parameters |
|时间提供程序\配置 Windows NTP 客户端 |W32Time\TimeProviders\NtpClient |
|时间提供程序\启用 Windows NTP 客户端 |W32Time\TimeProviders\NtpClient |
|时间提供程序\启用 Windows NTP 服务器 |W32Time\TimeProviders\NtpServer |

> <sup>1</sup> 类别路径：**计算机配置\管理模板\系统\Windows 时间服务**  
> <sup>2</sup> 子项：**HKLM\SOFTWARE\Policies\Microsoft**  
> <sup>3</sup> 子项：**HKLM\SYSTEM\CurrentControlSet\Services**

## <a name="enabling-w32time-logging"></a>启用 W32Time 日志记录

以下三个注册表项不属于 W32Time 默认配置，但可以添加到注册表中，以获取增强的日志记录功能。 可以通过在组策略对象编辑器中更改 **EventLogFlags** 设置的值，修改记录到系统事件日志中的信息。 默认情况下，时间服务会在每次切换到新的时间源时记录一个事件。

若要启用 W32Time 日志记录，请添加以下注册表项：  

|注册表项 |版本 |说明 |
| --- | --- | --- |
|**FileLogEntries** |所有版本 |控制 Windows 时间日志文件中创建的条目数。 默认值为 none，即不记录任何 Windows 时间活动。 有效值为 **0** 到 **300**。 此值不影响由 Windows 时间正常创建的事件日志条目 |
|**FileLogName** |所有版本 |控制 Windows 时间日志的位置和文件名。 默认值为空白，仅当更改 FileLogEntries 后才可更改此值。 有效值是 Windows 时间用于创建日志文件的完整路径和文件名。 此值不影响由 Windows 时间正常创建的事件日志条目。 |
|**FileLogSize** |所有版本 |控制 Windows 时间日志文件的循环日志记录行为。 定义 FileLogEntries 和 FileLogName 后，条目将定义允许日志文件到达的大小（以字节为单位），到达此大小后将用新条目覆盖最旧的日志条目 。 对于此设置，请使用 **1000000** 或更大的值。 此值不影响由 Windows 时间正常创建的事件日志条目。 |

## <a name="configuring-how-windows-time-service-resets-the-computer-clock"></a>配置 Windows 时间服务重置计算机时钟的方式

为了使 W32Time 逐步设置计算机时钟，偏移量必须小于 MaxAllowedPhaseOffset 值，并同时满足以下公式：  

- Windows Server 2016 及其更高版本：

  > |**CurrentTimeOffset**| &divide; (16 &times; **PhaseCorrectRate** &times; **pollIntervalInSeconds**) &le; **SystemClockRate** &divide; 2  

- Windows Server 2012 R2 及较早版本：

  > |**CurrentTimeOffset**| &divide; (**PhaseCorrectRate** &times; **UpdateInterval**) &le; **SystemClockRate** &divide; 2  

**CurrentTimeOffset** 值以时钟计时周期度量，其中，1 毫秒 = Windows 系统上的 10,000 个时钟计时周期。  

SystemClockRate 和 PhaseCorrectRate 也以时钟计时周期来度量 。 若要获取 SystemClockRate 值，可使用以下命令，并使用公式“秒数 &times; 1,000 &times; 10,000”将其从秒数转换为时钟计时周期数：  

```cmd
W32tm /query /status /verbose  
ClockRate: 0.0156000s  
```  

**SystemClockRate** 是指系统上的时钟速率。 使用 156,000 秒作为示例，SystemClockRate 值应为 = 0.0156000 &times; 1,000 &times; 10,000 = 156,000 个时钟计时周期。  

MaxAllowedPhaseOffset 也以秒为单位进行度量。 若要将其转换为时钟计时周期，请计算 **MaxAllowedPhaseOffset** &times; 1,000 &times; 10,000 的积。  

下面的示例演示如何在使用 Windows Server 2012 R2 或更低版本时应用这些计算。

**示例 1：时间相差 4 分钟**

你的时间为 11:05，从对等方收到的时间样本为 11:09，你认为后者是正确的。

> **PhaseCorrectRate** = 1  
>  
> **UpdateInterval** = 30,000 个时钟计时周期  
>  
> **SystemClockRate** = 156,000 个时钟计时周期  
>  
> **MaxAllowedPhaseOffset** = 10 分钟 = 600 秒 = 600 &times; 1,000 &times; 10,000 = 6,000,000,000 个时钟计时周期  
>  
> |**CurrentTimeOffset**| = 4 分钟 = 4 &times; 60 &times; 1,000 &times; 10,000 = 2,400,000,000 个时钟计时周期  
>  
> **CurrentTimeOffset** 是否 &le; **MaxAllowedPhaseOffset**？  
>  
> 2,400,000,000 &le; 6,000,000,000：TRUE  

那么，它是否满足上述公式？

> (|**CurrentTimeOffset**| &divide; (**PhaseCorrectRate** &times; **UpdateInterval**) &le; **SystemClockRate** &divide; 2)  

2,400,000,000 / (30,000 &times; 1) 是否 &le; 156,000 &divide; 2  

80,000 &le; 78,000：FALSE  

因此，W32tm 会立即调回时钟。  

> [!NOTE]  
> 在这种情况下，若要慢慢地调回时钟，还必须在注册表中调整 PhaseCorrectRate 或 UpdateInterval 的值，确保等式结果为“TRUE”  。  

**示例 2：时间相差 3 分钟**

> **PhaseCorrectRate** = 1  
> 
> **UpdateInterval** = 30,000 个时钟计时周期  
> 
> SystemClockRate = 156,000 个时钟计时周期  
> 
> **MaxAllowedPhaseOffset** = 10 分钟 = 600 秒 = 600 &times; 1,000 &times; 10,000 = 6,000,000,000 个时钟计时周期  
> 
> |**CurrentTimeOffset**| = 3 分钟 = 3 &times; 60 &times; 1,000 &times; 10,000 = 1,800,000,000 个时钟计时周期  
> 
> |**CurrentTimeOffset**|  是否 &le; **MaxAllowedPhaseOffset**？  
> 
> 1,800,000,000 &le; 6,000,000,000：TRUE  

那么，它是否满足上述公式？

> (|**CurrentTimeOffset**| &divide; (**PhaseCorrectRate** &times; **UpdateInterval**) &le; **SystemClockRate** &divide; 2)  
> 
> 3 分钟 &times; (1,800,000,000) &divide; (30,000 &times; 1) 是否 &le; 156,000 &divide; 2  
> 
> 60,000 &le; 78,000：TRUE  

在这种情况下，时钟会慢慢调回来。  

## <a name="reference-windows-time-service-registry-entries"></a>参考：Windows 时间服务注册表项

> [!WARNING]  
> 在排除故障或验证是否应用了必需的设置时，可参考有关这些注册表项的信息。 W32Time 在内部使用注册表的 W32Time 部分中的许多值来存储信息。 不要手动更改这些值。 在应用对注册表的修改之前，注册表编辑器或 Windows 不会对这些修改进行验证。 如果注册表包含无效值，则 Windows 可能会遇到不可恢复的错误。  

Windows 时间服务将信息存储在以下注册表子项下：

- [**HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Config**](#config)
- [**HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Parameters**](#parameters)
- [**HKLM\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\NtpClient**](#ntpclient)
- [**HKLM\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\NtpServer**](#ntpserver)

此外，出于故障排除目的，可以[添加用于配置日志的项](#enabling-w32time-logging)。

在下面的表中，“所有版本”是指包括 Windows 7、Windows 8、Windows 10、Windows Server 2008 和 Windows Server 2008 R2、Windows Server 2012 和 Windows Server 2012 R2、Windows Server 2016 以及 Windows Server 2019 在内的 Windows 版本。 某些项仅适用于更高的 Windows 版本。

> [!NOTE]  
> 注册表中的某些参数以时钟计时周期度量，某些参数以秒为单位度量。 若要将时间从时钟计时周期转换为秒，请使用以下转换系数：  
> - 1 分钟 = 60 秒  
> - 1 秒 = 1000 毫秒  
> - 1 毫秒 = Windows 系统上 10000 个时钟计时周期，如 [DateTime.Ticks 属性](https://docs.microsoft.com/dotnet/api/system.datetime.ticks)中所述。  
>  
> 例如，5 分钟变为 5 &times; 60 &times; 1000 &times; 10000 = 3,000,000,000 个时钟计时周期。  

### <a name="hklmsystemcurrentcontrolsetservicesw32timeconfig-subkey-entries"></a><a id="config"></a>“HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Config”子项条目

|注册表项 |版本 |说明 |
| --- | --- | --- |
|**AnnounceFlags** |所有版本 |控制是否将此计算机标记为可靠的时间服务器。 除非将计算机标记为时间服务器，否则不会将其标记为可靠。<ul><li>**0x00**： 不是时间服务器</li><li>**0x01**： 始终是时间服务器</li><li>**0x02**： 自动时间服务器</li><li>**0x04**： 始终可靠的时间服务器</li><li>**0x08**： 自动且可靠的时间服务器</li></ul><br />域成员的默认值为 **10**。 独立客户端和服务器的默认值为 **10**。 |
|**ChainDisable** | |控制是否禁用链接机制。 如果禁用了链接（设置为0），则只读域控制器 (RODC) 可以与任何域控制器同步，但是，不将其密码缓存在 RODC 上的主机将无法与 RODC 同步。 这是一项布尔设置，默认值为 **0**。|
|**ChainEntryTimeout** | |指定在将条目视为过期之前条目可以在链接表中保留的最长时间。 过期的条目可以在处理下一个请求或响应时删除。 默认值为 **16**（秒）。 |
|**ChainLoggingRate** | |控制在事件查看器中将指示成功和失败链接尝试次数的事件记录到系统日志的频率。 默认值为 **30**（分钟）。 |
|**ChainMaxEntries** | |控制链接表中允许的最大条目数。 如果链接表已满但不能删除过期的条目，则会丢弃任何传入请求。 默认值为 **128**（条目数）。 |
|**ChainMaxHostEntries** | |控制特定主机的链接表中允许的最大条目数。 默认值为 **4**（条目数）。 |
|**ClockAdjustmentAuditLimit** |Windows Server 2016 版本 1709 及更高版本；Windows 10 版本 1709 及更高版本 |指定可能记录到目标计算机上的 W32time 服务事件日志中的最小本地时钟调整。 默认值为 **800**（百万分率 - PPM）。 |
|**ClockHoldoverPeriod** |Windows Server 2016 版本 1709 及更高版本；Windows 10 版本 1709 及更高版本 |指示在不与时间源同步的情况下，系统时钟可以在名义上保持其准确性的最大秒数。 如果这段时间已过，而 W32time 未从任何输入提供程序获取新示例，W32time 就会开始重新发现时间源。 Default：7,800 秒。 |
|**EventLogFlags** |所有版本 |控制时间服务记录的具体事件。<ul><li>**0x1**： 时间跳转</li><li>**0x2**： 源更改</li></ul>域成员的默认值为 **2**。 独立客户端和服务器的默认值为 **2**。 |
|**FrequencyCorrectRate** |所有版本 |控制校正时钟的速率。 如果此值太小，则时钟不稳定，并且出现过度校正。 如果值太大，则时钟需要很长时间才能同步。 域成员的默认值为 **4**。 独立客户端和服务器的默认值为 **4**。<p>**注意** <br />零不是 **FrequencyCorrectRate** 注册表项的有效值。 在 Windows Server 2003、Windows Server 2003 R2、Windows Server 2008 和 Windows Server 2008 R2 计算机上，如果将该值设置为 **0**，则 Windows 时间服务会自动将其更改为 **1**。 |
|**HoldPeriod** |所有版本 |控制禁用峰值检测以使本地时钟快速进入同步状态的时间段。 峰值是指示时间停顿了几秒的时间样本，通常在一致返回良好时间样本后收到峰值。 域成员的默认值为 **5**。 独立客户端和服务器的默认值为 **5**。 |
|**LargePhaseOffset** |所有版本 |指定将大于或等于此值（以 10<sup>-7</sup> 秒为单位）的时间偏移视为峰值。 网络干扰（如流量过大）可能会导致出现峰值。 除非持续很长时间，否则将忽略峰值。 域成员的默认值为 **50000000**。 独立客户端和服务器的默认值为 **50000000**。 |
|**LastClockRate** |所有版本 |由 W32Time 维护。 它包含 Windows 操作系统使用的保留数据，对此设置的任何更改都可能导致不可预测的结果。 域成员的默认值为 **156250**。 独立客户端和服务器的默认值为 **156250**。 |
|**LocalClockDispersion** |所有版本 |控制在唯一时间源为内置 CMOS 时钟时必须采用的离差（以秒为单位）。 域成员的默认值为 **10**。 独立客户端和服务器的默认值为 **10**。 |
|**MaxAllowedPhaseOffset** |所有版本 |指定 W32Time 尝试使用时钟速率调整计算机时钟的最大偏移量（以秒为单位）。 当偏移量超过此速率时，W32Time 会直接设置计算机时钟。 域成员的默认值为 **300**。 独立客户端和服务器的默认值为 **1**。 有关详细信息，请参阅[配置 Windows 时间服务重置计算机时钟的方式](#configuring-how-windows-time-service-resets-the-computer-clock)。 |
|**MaxClockRate** |所有版本 |由 W32Time 维护。 它包含 Windows 操作系统使用的保留数据，对此设置的任何更改都可能导致不可预测的结果。 域成员的默认值为 **155860**。 独立客户端和服务器的默认值为 **155860**。 |
|**MaxNegPhaseCorrection** |所有版本 |指定服务可以进行的最大负向时间校正（以秒为单位）。 如果服务确定需要进行大于此值的更改，它将改为记录一个事件。<p>**注意**<br />值 **0xFFFFFFFF** 为特例。 此值表示服务始终校正时间。<p>域成员的默认值为 **0xFFFFFFFF**。 独立客户端和服务器的默认值为 **54,000**（15 小时）。|
|**MaxPollInterval** |所有版本 |指定系统轮询间隔允许的最大间隔（以 log2 秒为单位）。 请注意，当系统必须根据计划的时间间隔进行轮询时，提供程序可以在收到生成样本的请求时拒绝该请求。 域控制器的默认值为 **10**。 域成员的默认值为 **15**。 独立客户端和服务器的默认值为 **15**。 |
|**MaxPosPhaseCorrection** |所有版本 |指定服务可以进行的最大正向时间校正（以秒为单位）。 如果服务确定需要进行大于此值的更改，它将改为记录一个事件。<p>**注意**<br />值 **0xFFFFFFFF** 为特例。 此值表示服务始终校正时间。<p>域成员的默认值为 **0xFFFFFFFF**。 独立客户端和服务器的默认值为 **54,000**（15 小时）。 |
|**MinClockRate** |所有版本 |由 W32Time 维护。 它包含 Windows 操作系统使用的保留数据，对此设置的任何更改都可能导致不可预测的结果。 域成员的默认值为 **155860**。 独立客户端和服务器的默认值为 **155860**。 |
|**MinPollInterval** |所有版本 |指定系统轮询间隔允许的最小间隔（以 log2 秒为单位）。 请注意，虽然系统要求的采样频率不超过此频率，但提供程序可以在计划的时间间隔以外的时间生成样本。 域控制器的默认值为 **6**。 域成员的默认值为 **10**。 独立客户端和服务器的默认值为 **10**。 |
|**PhaseCorrectRate** |所有版本 |控制校正相位错误的速率。 指定较小的值会快速校正相位错误，但可能会导致时钟变得不稳定。 如果该值过大，则需要较长的时间来校正相位错误。<p>域成员的默认值为 **1**。 独立客户端和服务器的默认值为 **7**。<p>**注意**<br />零不是 **PhaseCorrectRate** 注册表项的有效值。 在 Windows Server 2003、Windows Server 2003 R2、Windows Server 2008 和 Windows Server 2008 R2 计算机上，如果将该值设置为 **0**，则 Windows 时间服务会自动将其更改为 **1**。 |
|**PollAdjustFactor** |所有版本 |控制是决定增大还是决定减小系统的轮询间隔。 值越大，导致轮询间隔减少的错误量就越小。 域成员的默认值为 **5**。 独立客户端和服务器的默认值为 **5**。 |
|**RequireSecureTimeSyncRequests** |Windows 8 及更高版本 |控制 DC 是否会响应使用较旧身份验证协议的时间同步请求。 如果启用此项（将其设置为 **1**），则 DC 不会响应使用此类协议的请求。 这是一项布尔设置，默认值为 **0**。 |
|**SpikeWatchPeriod** |所有版本 |指定可疑偏移量在被接受为正确偏移量之前必须持续的时间（以秒为单位）。 域成员的默认值为 **900**。 独立客户端和工作站的默认值为 **900**。 |
|**TimeJumpAuditOffset** |所有版本 |一个不带正负号的整数，指示时间跳跃审核阈值（以秒为单位）。 如果时间服务通过直接设置时钟调整了本地时钟，而且时间校正大于此值，则时间服务会记录一个审核事件。 |
|**UpdateInterval** |所有版本 |指定相位校正调整之间的时钟计时周期数。 域控制器的默认值为 **100**。 域成员的默认值为 **30,000**。 独立客户端和服务器的默认值为 **360,000**。<p>**注意**<br />零不是 **UpdateInterval** 注册表项的有效值。 在运行 Windows Server 2003、Windows Server 2003 R2、Windows Server 2008 和 Windows Server 2008 R2 的计算机上，如果将该值设置为 **0**，Windows 时间服务会自动将其更改为 **1**。|
|**UtilizeSslTimeData** |Windows 10 版本 1511 之后的 Windows 版本 |值为 **1** 表示 W32Time 使用多个 SSL 时间戳来播发非常不准确的时钟。 |

### <a name="hklmsystemcurrentcontrolsetservicesw32timeparameters-subkey-entries"></a><a id="parameters"></a>“HKLM\SYSTEM\CurrentControlSet\Services\W32Time\Parameters”子项条目

| 注册表项 | 版本 | 说明 |
| --- | --- | --- |
|**AllowNonstandardModeCombinations** |所有版本 |指示对等方之间的同步中允许非标准模式组合。 域成员的默认值为 **1**。 独立客户端和服务器的默认值为 **1**。 |
|**NtpServer** |所有版本 |指定以空格分隔的对等列表，计算机可从该列表中获取时间戳，其中每行包含一个或多个 DNS 名称或 IP 地址。 列出的每个 DNS 名称或 IP 地址必须是唯一的。 连接到域的计算机必须与更可靠的时间源同步，例如美国官方时钟。  <ul><li>0x01 SpecialInterval </li><li>0x02 UseAsFallbackOnly</li><li>0x04 SymmetricActive：有关此模式的详细信息，请参阅 [Windows 时间服务器：3.3 操作模式](https://go.microsoft.com/fwlink/?LinkId=208012)。</li><li>0x08 Client</li></ul><br />域成员上没有此注册表项的默认值。 独立客户端和服务器的默认值为 time.windows.com,0x1。<p>**注意**<br />有关可用 NTP 服务器的详细信息，请参阅 KB 262680：[Internet 上可用的简单网络时间协议 (SNTP) 时间服务器的列表](https://support.microsoft.com/help/262680/a-list-of-the-simple-network-time-protocol-sntp-time-servers-that-are) |
|**ServiceDll** |所有版本 |由 W32Time 维护。 它包含 Windows 操作系统使用的保留数据，对此设置的任何更改都可能导致不可预测的结果。 此 DLL 在域成员及独立客户端和服务器上的默认位置为 %windir%\System32\W32Time.dll。 |
|**ServiceMain** |所有版本 |由 W32Time 维护。 它包含 Windows 操作系统使用的保留数据，对此设置的任何更改都可能导致不可预测的结果。 域成员的默认值为 **SvchostEntry_W32Time**。 独立客户端和服务器的默认值为 **SvchostEntry_W32Time**。 |
|**Type** |所有版本 |指示要接受其同步的对等方：  <ul><li>**NoSync**。 时间服务不与其他源同步。</li><li>**NTP**： 时间服务从 NtpServer.  注册表项中指定的服务器进行同步。</li><li>**NT5DS**。 时间服务从域层次结构进行同步。  </li><li>**AllSync**。 时间服务使用所有可用的同步机制。  </li></ul>域成员的默认值为 NT5DS。 独立客户端和服务器的默认值为 NTP。 |

### <a name="hklmsystemcurrentcontrolsetservicesw32timetimeprovidersntpclient-subkey-entries"></a><a id="ntpclient"></a>“HKLM\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\NtpClient”子项条目

|注册表项 |版本 |说明 |
| --- | --- | --- |
|**AllowNonstandardModeCombinations** |所有版本 |指示对等方之间的同步中允许非标准模式组合。 域成员的默认值为 **1**。 独立客户端和服务器的默认值为 **1**。|
|**CompatibilityFlags** |所有版本 |指定以下兼容性标志和值：<ul><li>**0x00000001** - DispersionInvalid</li><li>**0x00000002** - IgnoreFutureRefTimeStamp</li><li>**0x80000000** - AutodetectWin2K</li><li>**0x40000000** - AutodetectWin2KStage2</li></ul>域成员的默认值为 **0x80000000**。 独立客户端和服务器的默认值为 **0x80000000**。 |
|**CrossSiteSyncFlags** |所有版本 |确定服务是否选择计算机域之外的同步伙伴。 选项和值为：<ul><li>**0** - None</li><li>**1** - PdcOnly</li><li>**2** - All</li></ul>如果未设置 NT5DS 值，则将忽略此值。 域成员的默认值为 **2**。 独立客户端和服务器的默认值为 **2**。 |
|**DllName** |所有版本 |指定时间提供程序的 DLL 位置。<p>此 DLL 在域成员及独立客户端和服务器上的默认位置为 **%windir%\System32\W32Time.dll**。 |
|**Enabled** |所有版本 |指示当前时间服务是否启用了 NtpClient 提供程序。<ul><li>**1** - 是</li><li>**0** - 否</li></ul>域成员的默认值为 **1**。 独立客户端和服务器的默认值为 **1**。|
|**EventLogFlags** |所有版本 |指定 Windows 时间服务记录的事件。<ul><li>**0x1** - 可访问性更改</li><li>**0x2** - 大样本倾斜（仅适用于 Windows Server 2003、Windows Server 2003 R2、Windows Server 2008 和 Windows Server 2008 R2）</li></ul>域成员的默认值为 **0x1**。 独立客户端和服务器的默认值为 **0x1**。|
|**InputProvider** |所有版本 |指示是否启用 NtpClient 作为 InputProvider。如果启用，它将从 NtpServer 获取时间信息。 NtpServer 是一个时间服务器，它将返回对可用于同步本地时钟的时间样本，以响应网络上的客户端时间请求。 <ul><li>**1** - 是</li><li>**0** - 否</li></ul>域成员和独立客户端的默认值为 **1**。 |
|**LargeSampleSkew** |所有版本 |指定用于日志记录的大样本倾斜（以秒为单位）。 为遵守证券交易委员会 (SEC) 规范，应将此设置为 3 秒。 仅当为 0x2 大样本倾斜显式配置了 **EventLogFlags** 时，才会记录此设置的事件。 域成员的默认值为 3。 独立客户端和服务器的默认值为 3。 |
|**ResolvePeerBackOffMaxTimes** |所有版本 |指定重复尝试查找要与之同步的对等方失败时使等待间隔加倍的最大次数。 如果值为零，则表示等待间隔始终为最小值。 域成员的默认值为 **7**。 独立客户端和服务器的默认值为 **7**。 |
|**ResolvePeerBackoffMinutes** |所有版本 |指定尝试查找要与之同步的对等方之前等待的初始间隔（以分钟为单位）。 域成员的默认值为 **15**。 独立客户端和服务器的默认值为 **15**。  |
|**SpecialPollInterval** |所有版本 |指定手动对等的特殊轮询间隔（以秒为单位）。 启用 **SpecialInterval** 0x1 标志后，W32Time 会使用此轮询间隔，而不是由操作系统确定的轮询间隔。 域成员的默认值为 **3,600**。 独立客户端和服务器的默认值为 **604,800**。<br/><br/>内部版本 1703 的新值 SpecialPollInterval 是由 MinPollInterval 和 MaxPollInterval Config 注册表值所包含的。|
|**SpecialPollTimeRemaining** |所有版本 |由 W32Time 维护。 它包含 Windows 操作系统使用的保留数据。 它指定在计算机重启后 W32Time 重新同步之前的时间（以秒为单位）。 对此设置的任何更改都可能导致不可预测的结果。 域成员及独立客户端和服务器上的默认值均保留为空。 |

### <a name="hklmsystemcurrentcontrolsetservicesw32timetimeprovidersntpserver-subkey-entries"></a><a id="ntpserver"></a>“HKLM\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\NtpServer”子项条目

|注册表项 |版本 |说明 |
| --- | --- | --- |
|**AllowNonstandardModeCombinations** |所有版本 |指示允许在客户端与服务器的同步中使用非标准模式组合。 域成员的默认值为 **1**。 独立客户端和服务器的默认值为 **1**。 |
|**DllName** |所有版本 |指定时间提供程序的 DLL 位置。 此 DLL 在域成员及独立客户端和服务器上的默认位置为 **%windir%\System32\W32Time.dll**。  |
|**Enabled** |所有版本 |指示当前时间服务是否启用了 NtpServer 提供程序。 <ul><li>**1** - 是</li><li>**0** - 否</li></ul>域成员的默认值为 **1**。 独立客户端和服务器的默认值为 **1**。 |
|**InputProvider** |所有版本 |指示是否启用 NtpClient 作为 InputProvider。如果启用，它将从 NtpServer 获取时间信息。 NtpServer 是一个时间服务器，它将返回对可用于同步本地时钟的时间样本，以响应网络上的客户端时间请求。 <ul><li>**1** - 是</li><li>**0** - 否 </li></ul>域成员和独立客户端的默认值：1 |

## <a name="reference-pre-set-values-for-the-windows-time-service-gpo-settings"></a>参考：适用于 Windows 时间服务 GPO 设置的预设值  

下表列出了与 Windows 时间服务相关联的全局组策略设置以及与每项设置相关联的预设值。 有关每项设置的详细信息，请参阅本文前面部分的[参考：Windows 时间服务注册表项](#reference-windows-time-service-registry-entries)中介绍的相应注册表项。 以下设置包含在名为“全局配置设置”的单个 GPO 中。  

### <a name="pre-set-values-for-global-group-policy-settings"></a>“全局组策略”设置的预设值

|组策略设置|预设值|  
| --- | --- |
|**AnnounceFlags**|**10**|  
|**EventLogFlags**|**2**|  
|**FrequencyCorrectRate**|**4**|  
|**HoldPeriod**|**5**|  
|**LargePhaseOffset**|**1,280,000**|  
|**LocalClockDispersion**|**10**|  
|**MaxAllowedPhaseOffset**|**300**|  
|**MaxNegPhaseCorrection**|**54,000**（15 小时）|  
|**MaxPollInterval**|**15**|  
|**MaxPosPhaseCorrection**|**54,000**（15 小时）|  
|**MinPollInterval**|**10**|  
|**PhaseCorrectRate**|**7**|  
|**PollAdjustFactor**|**5**|  
|**SpikeWatchPeriod**|**90**|  
|**UpdateInterval**|**100**|  

### <a name="pre-set-values-for-configure-windows-ntp-client-settings"></a>“配置 Windows NTP 客户端”设置的预设值

下表列出了“配置 Windows NTP 客户端”GPO 的可用设置，以及与 Windows 时间服务相关联的预设值。 有关每项设置的详细信息，请参阅本文前面部分的[参考：Windows 时间服务注册表项](#reference-windows-time-service-registry-entries)中介绍的相应注册表项。  

|组策略设置|预设值|  
|------------------------|-----------------|  
|**NtpServer**|time.windows.com、**0x1**|  
|**Type**|默认选项：<ul><li>**NTP**。 在未加入域的计算机上使用。</li><li>**NT5DS：** 在加入域的计算机上使用。</li></ul>|  
|**CrossSiteSyncFlags**|**2**|  
|**ResolvePeerBackoffMinutes**|**15**|  
|**ResolvePeerBackoffMaxTimes**|**7**|  
|**SpecialPollInterval**|**3,600**|  
|**EventLogFlags**|**0**|  

## <a name="reference-network-ports-that-the-windows-time-service-uses"></a>参考：Windows 时间服务使用的网络端口

Windows 时间遵循 NTP 规范，该规范要求使用 UDP 端口 123 进行所有时间同步通信。 Windows 时间始终保留此端口。 计算机同步其时钟或向另一台计算机提供时间时，这种通信在 UDP 端口 123 上完成。  

> [!NOTE]  
> 如果计算机是有多个网络适配器的计算机（也称为多宿主计算机），则无法基于网络适配器选择性地启用 Windows 时间服务。  

## <a name="related-information"></a>相关信息  

以下资源包含与此部分相关的其他信息。  

- IETF RFC 数据库中的 RFC 1305  
