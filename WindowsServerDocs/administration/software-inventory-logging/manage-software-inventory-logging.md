---
title: 管理软件清单日志记录
description: 描述如何管理软件清单日志记录
ms.topic: article
ms.assetid: 812173d1-2904-42f4-a9e2-de19effec201
author: brentfor
ms.author: brentf
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: dba46b75da685f5b2cb74e8e08c53db9aa643aba
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628264"
---
# <a name="manage-software-inventory-logging"></a>管理软件清单日志记录

>适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2

本文档介绍如何管理软件清单日志记录，这是一项功能，可帮助数据中心管理员在一段时间内轻松记录其部署的 Microsoft 软件资产管理数据。 本文档介绍如何管理软件清单日志记录。 在 Windows Server 2012 R2 中使用软件清单日志记录之前，请确保在每个需要列出清单的系统上安装 Windows 更新 [kb 3000850](https://support.microsoft.com/kb/3000850) 和 [kb 3060681](https://support.microsoft.com/kb/3060681) 。 Windows Server 2016 无需进行 Wndows 更新。 此功能在要记录清单的每台服务器上以本地方式运行。 它不会从远程服务器收集数据。

软件清单日志记录功能还可添加到 Windows Server 2012 R2 之前的两个 Windows Server 版本。 你可以安装以下更新以将软件清单日志记录功能添加到 Windows Server 2012 和 Windows Server 2008 R2 SP1：

- **Windows Server 2012 (Standard 或 Datacenter Edition) **

> [!NOTE]
> 请确保在应用以下更新程序包之前安装了 [WMF 4.0](https://www.microsoft.com/download/details.aspx?id=40855) 。

-  Windows Server 2012 的 WMF 4.0 更新包：[KB 3119938](https://support.microsoft.com/kb/3119938)

- **Windows Server 2008 R2 SP1**

> [!NOTE]
> 请确保在应用以下更新程序包之前安装了 [WMF 4.0](https://www.microsoft.com/download/details.aspx?id=40855) 。


- 需要 [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653)


- Windows Server 2008 R2 的 WMF 4.0 更新包： [KB 3109118](https://support.microsoft.com/kb/3109118)


可通过两种主要方法使用此功能列出清单：

1.  每小时启动 SIL 日志记录功能，以从 SIL 数据源收集并通过网络将有效负载转发到指定目标 (URI)。

2.  按任何间隔使用 PowerShell 或 WMI 手动查询 SIL 数据。

启动 SIL 日志记录涉及到一些规划和预测，但与手动查询数据相比具有明显优势。 对于数据中心管理员，使用 SIL 日志记录有以下三个主要优势：

-   可以随时间推移收集持续的历史记录（日志），从而可以从单个源实现灵活而全面的报告。

-   可以克服对许多清单工具十分典型的计算机发现难题。

-   可以克服对许多清单工具十分典型的信任边界难题以及对提升用户权限的需要，同时维持一定级别的安全性，因为会使用 SSL 在 HTTPS 上对数据加密。

软件清单日志记录在默认情况下会安装，但日志记录在默认情况下不会启动。 软件清单日志记录的所有配置是使用 PowerShell cmdlet 进行。 软件清单日志记录只有少量配置选项。 本文档介绍这些选项及其预期用途，以及用于数据收集（如果使用上面的第二种方法）的 cmdlet。

**本文档内容**

本文档中提及的配置选项包括：

-   [启动和停止软件清单日志记录](manage-software-inventory-logging.md#BKMK_Step1)

-   [随时间推移进行的软件清单日志记录](manage-software-inventory-logging.md#BKMK_Step2)

-   [显示软件清单日志记录数据](manage-software-inventory-logging.md#BKMK_Step3)

-   [删除软件清单日志记录所记录的数据](manage-software-inventory-logging.md#BKMK_Step4)

-   [备份和还原软件清单日志记录所记录的数据] 管理-软件-清单-记录 md # BKMK_Step5) 

-   [读取软件清单日志记录所记录和发布的数据](manage-software-inventory-logging.md#BKMK_Step6)

-   [软件清单日志记录安全](manage-software-inventory-logging.md#BKMK_Step7)

-   [使用 Windows Server 软件清单日志记录中的日期和时间设置](manage-software-inventory-logging.md#BKMK_Step8)

-   [在装载的虚拟硬盘中启用和配置软件清单日志记录](manage-software-inventory-logging.md#BKMK_Step10)

-   [在不带 KB 3000850 的 Windows Server 2012 R2 中使用软件清单日志记录的概述](manage-software-inventory-logging.md#BKMK_Step11)

-   [在不带 KB 3000850 的 Windows Server 2012 R2 Hyper-V 环境中使用软件清单日志记录](manage-software-inventory-logging.md#BKMK_Step12)

> [!NOTE]
> 此主题将介绍一些 Windows PowerShell cmdlet 示例，你可以使用它们来自动执行所述的一些步骤。 有关详细信息，请参阅使用 Cmdlet。


## <a name="starting-and-stopping-software-inventory-logging"></a><a name="BKMK_Step1"></a>启动和停止软件清单日志记录
必须在运行 Windows Server 2012 R2 的计算机上启用软件清单日志记录每日收集和通过网络进行的转发，才能记录软件清单。

> [!NOTE]
> 你可以使用 **[Get-SilLogging](/previous-versions/windows/powershell-scripting/dn283396(v=wps.630))** PowerShell cmdlet 检索有关软件清单日志记录服务的信息，包括它是在运行还是已停止。

#### <a name="to-start-software-inventory-logging"></a>启动软件清单日志记录

1.  使用有本地管理员权限的帐户登录服务器。

2.  以管理员身份打开 PowerShell。

3.  在 PowerShell 提示符处，输入 **[Start-SilLogging](/previous-versions/windows/powershell-scripting/dn283391(v=wps.630))**

> [!NOTE]
> 可以设置目标而无需设置证书指纹，但如果这样做，转发会失败，数据会在本地存储最多 30 天（这是默认值，在此之后数据会删除）。 对目标设置有效的证书哈希（并在 LocalMachine/Personal 存储空间中安装有效证书）后，只要目标配置为接受具有此证书的此数据，则本地存储的数据将转发至目标（请参阅 [Software Inventory Logging Aggregator](Software-Inventory-Logging-Aggregator.md) ，了解有关详细信息）。

#### <a name="to-stop-software-inventory-logging"></a>停止软件清单日志记录

1.  使用有本地管理员权限的帐户登录服务器。

2.  以管理员身份打开 PowerShell。

3.  在 PowerShell 提示符处，输入 **[Stop-SilLogging](/previous-versions/windows/powershell-scripting/dn283394(v=wps.630))**

## <a name="configuring-software-inventory-logging"></a>配置软件清单日志记录
配置软件清单日志记录以便将数据持续转发到聚合服务器有三个步骤：

1.  使用 **set-sillogging – TargetUri** 指定聚合服务器的 web 地址， (必须以 "https://" ) 开头。

2.  使用 **set-sillogging – CertificateThumbprint** 指定有效 SSL 证书的指纹哈希，该哈希将用于对聚合服务器的数据传输进行身份验证 (需要将聚合服务器配置为接受哈希) 。

3.  在将从中转发数据的本地服务器的 **本地计算机/个人存储区**（或 **/LocalMachine/MY**）中（为网络）安装有效的 SSL 证书。

最好在使用 **Start-SilLogging** 之前完成这些步骤。  如果想要在使用 **Start-SilLogging** 之后使用它们，停止并重启 SIL 即可。  或者，可以使用 Publish-SilData Cmdlet 确保聚合服务器具有此服务器的完备数据。

有关整体设置 SIL 框架的全面指南，请参阅 [Software Inventory Logging Aggregator](software-inventory-logging-aggregator.md)。  特别地，如果 **Publish-SilData** 生成错误或 SIL 日志记录失败，请参阅疑难解答部分。

## <a name="software-inventory-logging-over-time"></a><a name="BKMK_Step2"></a>随时间推移进行的软件清单日志记录
如果软件清单日志记录已由管理员启动，便会开始每小时收集数据并转发到聚合服务器（目标 URI）。 第一次转发是 [Get-SilData](/previous-versions/windows/powershell-scripting/dn283388(v=wps.630)) 在某个时间点检索并显示在控制台上的相同数据的完整数据集。 此后，SIL 会在每个间隔检查数据，如果自上一次收集以来数据中未进行任何更改，则仅将一个小型标识确认转发到目标聚合服务器。 如果有任何值发生了更改，则 SIL 会再次发送完整数据集。

> [!IMPORTANT]
> 如果在任何间隔目标 URI 不可访问或通过网络进行的数据传输出于任何原因未成功，则收集的数据会在本地存储最多 30 天（这是默认值，在此之后数据会删除）。 在下一次将数据成功转发到目标聚合服务器时，本地存储的所有数据都会进行转发，本地缓存的数据会删除。

## <a name="displaying-software-inventory-logging-data"></a><a name="BKMK_Step3"></a>显示软件清单日志记录数据
除了在前一个部分介绍的 PowerShell cmdlet，还可以使用六个其他 cmdlet 来收集软件清单日志记录数据：

-   **[Get-SilComputer](/previous-versions/windows/powershell-scripting/dn283392(v=wps.630))**：显示特定服务器和与操作系统相关数据的时间点值，以及物理主机的 FQDN 或主机名（如果可用）。

-   **[Get-SilComputerIdentity (KB 3000850)](/previous-versions/windows/powershell-scripting/dn858074(v=wps.630))**：显示由 SIL 用于各个服务器的标识符。

-   **[Get-SilData](/previous-versions/windows/powershell-scripting/dn283388(v=wps.630))**：显示所有软件清单日志记录数据的时间点集合。

-   **[Get-SilSoftware](/previous-versions/windows/powershell-scripting/dn283397(v=wps.630))**：显示计算机上安装的所有软件的时间点标识。

-   **[Get-SilUalAccess](/previous-versions/windows/powershell-scripting/dn283389(v=wps.630))**：显示从两天之前发出的服务器的唯一客户端设备请求和客户端用户请求总数。

-   **[Get-SilWindowsUpdate](/previous-versions/windows/powershell-scripting/dn283393(v=wps.630))**：显示计算机上安装的所有 Windows 更新的时间点列表。

软件清单日志记录 cmdlet 的典型用例情景是管理员使用 [Get-SilSoftware](/previous-versions/windows/powershell-scripting/dn283397(v=wps.630)) 对软件清单日志记录查询所有软件清单日志记录数据的时间点集合。

**输出示例**

```
PS C:\> Get-SilData

ID                 : 961FF8A1-8549-4BEC-8DF6-3B3E32C26FFA
UUID               : B49ACB4C-7D9C-4806-9917-AE750BB3DA84
VMGUID             : E84CCCBD-0D0F-486B-A424-9780C7CF92E4
Name               : Server01Guest.Test.Contoso.com
HypervisorHostName : Server01.Test.Contoso.com

ID          : {F0C3E5D1-1ADE-321E-8167-68EF0DE699A5}
Name        : Microsoft Visual C++ 2010  x86 Redistributable - 10.0.40219
InstallDate : 12/5/2013
Publisher   : Microsoft Corporation
Version     : 10.0.40219

ID          : {89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
Name        : Microsoft Silverlight
InstallDate : 3/20/2014
Publisher   : Microsoft Corporation
Version     : 5.1.30214.0

ChassisSerialNumber       : 4452-0564-0284-2290-0113-6804-05
CollectedDateTime         : 10/27/2014 4:01:33 PM
Model                     : Virtual Machine
Name                      : Server01Guest.Test.Contoso.com
NumberOfCores             : 1
NumberOfLogicalProcessors : 1
NumberOfProcessors        : 1
OSName                    : Microsoft Windows Server 2012 R2 Datacenter
OSSku                     : 8
OSSuite                   : 400
OSSuiteMask               : 400
OSVersion                 : 6.3.9600
ProcessorFamily           : 179
ProcessorManufacturer     : GenuineIntel
ProcessorName             : Intel(R) Xeon(R) CPU           E5440  @ 2.83GHz
SystemManufacturer        : Microsoft Corporation

```

> [!NOTE]
> 此 cmdlet 的输出与此功能结合使用的所有其他 **Get-Sil** cmdlet 相同，不过是以异步方式提供给控制台，因此对象的顺序可能并非总是相同。
>
> 无需启动软件清单日志记录，即可使用 **Get-Sil** cmdlet。

## <a name="deleting-data-logged-by-software-inventory-logging"></a><a name="BKMK_Step4"></a>删除软件清单日志记录所记录的数据
软件清单日志记录意图不在于充当一个关键任务组件。 它的设计目的是在保持高水平的可靠性的同时尽可能小地影响本地系统操作。 这也允许管理员手动删除软件清单日志记录数据库和支持文件 (\Windows\System32\LogFiles\SIL directory) 中的每个文件，以满足操作需求。

#### <a name="to-delete-data-logged-by-software-inventory-logging"></a>删除软件清单日志记录所记录的数据

1. 在 PowerShell 中，使用 **[Stop-SilLogging](/previous-versions/windows/powershell-scripting/dn283394(v=wps.630))** 命令停止软件清单日志记录。

2. 打开 Windows 资源管理器。

3. 中转到**\Windows\System32\Logfiles\SIL \\ **

4. 删除文件夹中的所有文件。

## <a name="backing-up-and-restoring-data-logged-by-software-inventory-logging"></a><a name="BKMK_Step5"></a>备份和还原软件清单日志记录所记录的数据
如果通过网络进行的转发失败，则软件清单日志记录会暂时存储每小时的数据集合。 日志文件存储在 \Windows\System32\LogFiles\SIL\ 目录中。 可以使用定期计划的服务器备份来备份此软件清单日志记录数据。

> [!IMPORTANT]
> 如果出于任何原因而需要进行操作系统的修复安装或升级，则本地存储的所有日志文件都会丢失。如果此数据对于操作至关重要，则建议在进行新操作系统安装之前进行备份。 修复或升级之后，只需还原到相同位置。

> [!NOTE]
> 如果出于任何原因管理 SIL 在本地记录的数据的保留期变得很重要，则可以通过更改此处的注册表值进行配置： \ HKEY_LOCAL_MACHINE \\ SOFTWARE\Microsoft\Windows\SoftwareInventoryLogging。 默认值为30天。

## <a name="reading-data-logged-and-published-by-software-inventory-logging"></a><a name="BKMK_Step6"></a>读取软件清单日志记录所记录和发布的数据
由 SIL 记录、但在本地存储 (如果转发到目标 URI 失败) 或成功转发到目标聚合服务器的数据）存储在二进制文件中， (每天的数据) 。 若要在 PowerShell 中显示此数据，请使用 [Import-BinaryMiLog](https://technet.microsoft.com/library/dn262592.aspx) cmdlet。

## <a name="software-inventory-logging-security"></a><a name="BKMK_Step7"></a>软件清单日志记录安全
需要本地服务器上的管理权限才能成功地从软件清单日志记录 WMI 和 PowerShell API 检索数据。

若要成功利用软件清单日志记录功能的完整功能，以便随时间推移持续地（以小时为间隔）将数据转发到聚合点，管理员需要使用客户端证书确保将安全的 SSL 会话用于通过 HTTPS 进行的数据传输。 可以在以下位置找到 HTTPS 身份验证的基本概述： [HTTPS 身份验证](/previous-versions/windows/it-pro/windows-server-2003/cc736680(v=ws.10))。

在 Windows Server 上本地存储的任何数据（仅当该功能已启动，但出于任何原因而无法访问目标时才这样进行）只能使用本地服务器上的管理权限来访问。

## <a name="working-with-date-and-time-settings-in-windows-server-2012-r2-software-inventory-logging"></a><a name="BKMK_Step8"></a>在 Windows Server 2012 R2 软件清单日志记录中使用日期和时间设置

-   使用 [Set-SilLogging](/previous-versions/windows/powershell-scripting/dn283387(v=wps.630)) -TimeOfDay 设置 SIL 日志记录运行的时间时，必须指定日期和时间。会设置日历日期，在本地系统时间达到该日期之前，不会进行日志记录。

-   当使用 [get-silsoftware](/previous-versions/windows/powershell-scripting/dn283397(v=wps.630))或 [get-silwindowsupdate](/previous-versions/windows/powershell-scripting/dn283393(v=wps.630))时，"InstallDate" 将始终显示12：00： 00 (（无意义的值）。

-   当使用 [get-silualaccess](/previous-versions/windows/powershell-scripting/dn283389(v=wps.630))时，"SampleDate" 将始终显示11：59： 00 (，这是一个毫无意义的值。日期是这些 cmdlet 查询的相关数据。

## <a name="enabling-and-configuring-software-inventory-logging-in-a-mounted-virtual-hard-disk"></a><a name="BKMK_Step10"></a>在装载的虚拟硬盘中启用和配置软件清单日志记录
软件清单日志记录还支持脱机虚拟机上的配置和启用。 这种情况的实际用途旨在涵盖跨数据中心的广泛部署的 "黄金映像" 设置，以及配置从本地到云部署的最终用户映像。

为了支持这些用途，软件清单日志记录具有与每个可配置选项相关联的注册表项。  可以在 \ HKEY_LOCAL_MACHINE SOFTWARE\Microsoft\Windows\SoftwareInventoryLogging. 下找到这些注册表值。 \\

| 函数 | 值名称 | 数据 | 对应的 Cmdlet（仅在正在运行的操作系统中可用） |
| --- | --- | --- | --- |
|启动/停止功能|CollectionState|1 或 0|[Start-SilLogging](/previous-versions/windows/powershell-scripting/dn283391(v=wps.630))、 [Stop-SilLogging](/previous-versions/windows/powershell-scripting/dn283394(v=wps.630))|
|指定网络上的目标聚合点|TargetUri|字符串|[Set-SilLogging](/previous-versions/windows/powershell-scripting/dn283387(v=wps.630)) -TargetURI|
|为目标 Web 服务器指定用于 SSL 身份验证的证书的证书指纹或哈希|CertificateThumbprint|字符串|[Set-SilLogging](/previous-versions/windows/powershell-scripting/dn283387(v=wps.630)) -CertificateThumbprint|
|指定功能应启动的日期和时间（如果设置的值根据本地系统时间是将来时间）|CollectionTime|默认：2000-01-01T03:00:00|[Set-SilLogging](/previous-versions/windows/powershell-scripting/dn283387(v=wps.630)) -TimeOfDay|

若要在脱机 VHD（未运行虚拟机操作系统）上修改这些值，必须首先装载 VHD，然后可以使用以下命令进行更改：

-   [Reg load](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742053(v=ws.11))

-   [Reg delete](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742145(v=ws.11))

-   [Reg add](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742162(v=ws.11))

-   [Reg unload](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742043(v=ws.11))

软件清单日志记录会在操作系统启动时检查这些值，并执行相应操作。

## <a name="overview-of-using-software-inventory-logging-in-windows-server-2012-r2-without-kb-3000850"></a><a name="BKMK_Step11"></a>在不带 KB 3000850 的 Windows Server 2012 R2 中使用软件清单日志记录的概述
在 [KB 3000850](https://support.microsoft.com/kb/3000850)中对软件清单日志记录功能和默认设置进行了以下更改：

-   在启动 SIL 日志记录时收集和通过网络进行的转发的默认间隔从每天更改为每小时（每小时中的随机时间）。

-   默认数据有效负载减少为仅包含来自 Get-SilComputer、Get-SilComputerIdentity 和 Get-SilSoftware 的对象。

-   删除了 Hyper-V 环境中来宾到主机的通道通信。

## <a name="using-software-inventory-logging-in-a-windows-server-2012-r2-hyper-v-environment-without-kb-3000850"></a><a name="BKMK_Step12"></a>在不带 KB 3000850 的 Windows Server 2012 R2 Hyper-V 环境中使用软件清单日志记录

> [!NOTE]
> 随着安装 [KB 3000850](https://support.microsoft.com/kb/3000850) 更新，会删除此功能。

在 Windows Server 2012 R2 Hyper-v 主机上使用软件清单日志记录时，如果已在来宾 () 中启动了 SIL 日志记录，则可以从本地运行的 Windows Server 2012 R2 来宾检索 SIL 数据。 不过，只有在使用 Get-sildata 和 Get-sildata Powershell cmdlet 时才可以这样做，并且仅可在主机和来宾中使用 WIndows Server 2012 R2。此功能的用途是允许向租户（或大型公司中的其他实体）提供来宾虚拟机的数据中心管理员在虚拟机监控程序主机上捕获软件清单数据，并在随后将所有这些数据转发到聚合器（或目标 URI）。

以下两个示例显示 PowerShell 控制台上的输出在运行一个 Windows Server 2012 R2 Hyper-v 主机（SIL 日志记录已启动）的 Windows Server 2012 R2 Hyper-v 主机上的)  (显示内容。你会注意到，使用单独 Get-SilData 的第一个示例会按预期方式输出来自主机的所有数据。还包含来自来宾的所有 SIL 数据，不过是采用折叠格式。若要展开并查看来自来宾的这些数据，只需剪切并粘贴以下第二个示例中使用的代码段。来自来宾的 SIL 数据对象始终在对象中关联了虚拟机 GUID。

> [!NOTE]
> 由于 SIL 数据在控制台上输出，因此在使用 Get-SilData cmdlet 时，数据流中的对象并不始终按预测顺序输出。在以下两个示例中，文本进行了颜色编码（蓝色用于物理主机数据，绿色用于虚拟来宾数据），只是为了用作本文档的说明工具。

**输出示例 1**

![示例输出报告的图像](../media/software-inventory-logging/SILHyper-VExample1.png)

**输出示例 2** (w/get-sildata 函数) 

![示例输出报告的图像](../media/software-inventory-logging/SILHyper-VExample2.png)

## <a name="see-also"></a>另请参阅
[软件清单日志记录入门](get-started-with-software-inventory-logging.md) 
[软件清单日志记录聚合](software-inventory-logging-aggregator.md) 
 器[Windows PowerShell](/powershell/module/softwareinventorylogging/?view=winserver2012R2-ps) 
 中的软件清单日志记录 cmdlet[导入-import-binarymilog](https://technet.microsoft.com/library/dn262592.aspx) 
[导出-import-binarymilog](https://technet.microsoft.com/library/dn262591.aspx)