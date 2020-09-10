---
title: 管理用户访问日志记录记录
description: 描述如何管理用户访问日志记录
ms.topic: article
ms.assetid: 4f039017-4152-47eb-838e-bb6ef730b638
author: brentfor
ms.author: brentf
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0c2380c27d6d08e788658cf946f92322c3a1eabb
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628129"
---
# <a name="manage-user-access-logging"></a>管理用户访问日志记录记录

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本文档介绍如何管理用户访问日志记录 (UAL)。

UAL 是可以帮助服务器管理员量化本地服务器上的角色和服务唯一客户端请求数量的功能。

默认安装并启用 UAL，它以几乎实时的方式收集数据。 UAL 只有少量配置选项。 本文档描述了这些选项和它们的拟定用途。

若要详细了解 UAL 的优点，请参阅 [用户访问日志记录入门](get-started-with-user-access-logging.md)。

**本文档内容**

本文档中提及的配置选项包括：

-   禁用和启用 UAL 服务

-   收集和删除数据

-   删除 UAL 记录的数据

-   在大容量环境中管理 UAL

-   从损坏状态恢复

-   启用工作文件夹使用情况许可证跟踪

## <a name="disabling-and-enabling-the-ual-service"></a><a name="BKMK_Step1"></a>禁用和启用 UAL 服务
默认情况下，UAL 处于启用状态，在运行 Windows Server 2012 或更高版本的计算机安装和启动时默认运行。 管理员可能想要关闭并禁用 UAL，以服从隐私要求或其他操作需求。 可以使用 "服务" 控制台、命令行或 PowerShell cmdlet 关闭 UAL。 但是，若要确保下次计算机启动时 UAL 不会再次运行，你还需要禁用服务。 以下过程介绍如何关闭和禁用 UAL。

> [!NOTE]
> 你可以使用 `Get-Service UALSVC` PowerShell cmdlet 检索有关 UAL 服务的信息，包括它是在运行还是已停止，以及是启用还是禁用状态。

#### <a name="to-stop-and-disable-the-ual-service-by-using-the-services-console"></a>使用服务控制台停止和禁用 UAL 服务的步骤

1.  使用有本地管理员权限的帐户登录服务器。

2.  在“服务器管理器”中，指向 **“工具”**，然后单击 **“服务”**。

3.  向下滚动并选择**User Access Logging Service**。单击**停止服务**。

4.  右键 \- 单击服务名称，然后选择 " **属性**"。 在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“禁用”**，然后单击 **“确定”**。

#### <a name="to-stop-and-disable-ual-from-the-command-line"></a>从命令行停止并禁用 UAL 的步骤

1.  使用有本地管理员权限的帐户登录服务器。

2.  按 Windows 徽标键 + R，然后键入“cmd”**** 打开命令提示符窗口。

    > [!IMPORTANT]
    > 如果出现了“用户帐户控制”**** 对话框，请确认其所显示的操作是你要采取的操作，然后单击“是”****。

3.  键入“net stop ualsvc”****，然后按 Enter。

4.  键入“netsh ualsvc set opmode mode=disable”****，然后按 Enter。

下面一个或多个 Windows PowerShell cmdlet 执行的功能与前面的过程相同。 在同一行输入每个 cmdlet（即使此处可能因格式限制而出现多行换行）。

你也可以通过使用服务停止和 Disable-Ual Windows PowerShell 命令停止和禁用 UAL。

```
Stop-service ualsvc
```

```
Disable-ual
```

如果以后想要重新启动和重新启用 UAL，可以使用以下过程来执行此操作。

#### <a name="to-start-and-enable-the-ual-service-by-using-the-services-console"></a>使用服务控制台启动和启用 UAL 服务的步骤

1.  使用有本地管理员权限的帐户登录服务器。

2.  在“服务器管理器”中，指向 **“工具”**，然后单击 **“服务”**。

3.  向下滚动并选择**User Access Logging Service**。单击**启用服务**。

4.  右键单击该服务名称，然后选择 **“属性”**。 在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

#### <a name="to-start-and-enable-ual-from-the-command-line"></a>从命令行启动并启用 UAL 的步骤

1.  使用本地管理员凭据登录服务器

2.  按 Windows 徽标键 + R，然后键入“cmd”**** 打开命令提示符窗口。

    > [!IMPORTANT]
    > 如果出现了“用户帐户控制”**** 对话框，请确认其所显示的操作是你要采取的操作，然后单击“是”****。

3.  键入“net start ualsvc”****，然后按 Enter。

4.  键入“netsh ualsvc set opmode mode=enable”****，然后按 Enter。

下面一个或多个 Windows PowerShell cmdlet 执行的功能与前面的过程相同。 在同一行输入每个 cmdlet（即使此处可能因格式限制而出现多行换行）。

你也可以通过使用服务启动和 Ual 启用 Windows PowerShell 命令启动和启用 UAL。

```
Enable-ual
```

```
Start-service ualsvc
```

## <a name="collecting-ual-data"></a><a name="BKMK_Step2"></a>收集 UAL 数据
除了在上一节中介绍的 PowerShell cmdlet 以外，还可以使用12个其他 cmdlet 来收集 UAL 数据：

-   **Get-UalOverview**：提供 UAL 相关的细节和已安装产品和角色的历史资料。

-   **Get-UalServerUser**：为本地或目标服务器提供客户端用户访问数据。

-   **Get-UalServerDevice**：为本地或目标服务器提供客户端设备访问数据。

-   **Get-UalUserAccess**：向本地或目标服务器上安装的每个角色或产品提供客户端用户访问数据。

-   **Get-UalDeviceAccess**：向本地或目标服务器上安装的每个角色或产品提供客户端设备访问数据。

-   **Get-UalDailyUserAccess**：在一年中的每一天提供客户端用户访问数据。

-   **Get-UalDailyDeviceAccess**：提供一年中的每一天的客户端设备访问数据。

-   **Get-UalDailyAccess**：在一年中的每一天提供客户端设备及用户访问数据。

-   **Get-UalHyperV**：提供与本地或目标服务器相关的虚拟机数据。

-   **Get-UalDns**：提供本地或目标 DNS 服务器的 DNS 客户端特定数据。

-   **Get-UalSystemId**：提供系统指定数据以唯一标识本地或目标服务器。

`Get-UalSystemId` 旨在为来自该服务器的所有其他有对应关系的数据，提供一个服务器的特定配置文件。如果服务器在中的某个参数中进行了任何更改，则 `Get-UalSystemId` 会创建新配置文件的其中一个参数。  `Get-UalOverview` 旨在向管理员提供一个在服务器上安装和正在使用的角色列表。

> [!NOTE]
> 默认情况下，会安装打印和文件服务和文件服务的基本功能。 因此，管理员可以期望总是看见有关这些的信息如同安装了完整角色那样显示。由于 UAL 为这些服务器角色收集了特定数据，Hyper-V 和 DNS 包括了单独的 UAL cmdlet。

UAL cmdlet 的一个典型用例场景应该是由管理员请求 UAL 以获取某个日期范围内的特定客户端访问。这可以通过多种方式完成。下面是用于请求一个日期范围内特定设备访问的推荐方法。

```
PS C:\Windows\system32>Gwmi -Namespace "root\AccessLogging" -query "SELECT * FROM MsftUal_DeviceAccess WHERE LastSeen >='1/01/2013' and LastSeen <='3/31/2013'"

```

这将以 IP 地址的方式，返回一个在那个日期范围内发出过服务器请求的全部特定客户端设备的冗长列表。

每个唯一客户端的 "ActivityCount" 限制为每天65535。同样，仅当按照日期发出查询的时候，方需从 PowerShell 调用 WMI。所有其他 UAL cmdlet 参数都可以如预期那样在 PS 查询内使用，如下面示例所示：

```
PS C:\Windows\system32> Get-UalDeviceAccess -IPAddress "10.36.206.112"

ActivityCount    : 1
FirstSeen        : 6/23/2012 5:06:50 AM
IPAddress        : 10.36.206.112
LastSeen         : 6/23/2012 5:06:50 AM
ProductName      : Windows Server 2012 Datacenter
RoleGuid         : 10a9226f-50ee-49d8-a393-9a501d47ce04
RoleName         : File Server
TenantIdentifier : 00000000-0000-0000-0000-000000000000
PSComputerName

```

UAL 最多可保留两年的历史记录。 为了允许管理员在服务运行时检索 UAL 数据，UAL 会将活动数据库文件的副本（当前 .mdb）复制到一个名为 *guid.empty* 的文件中，以便 WMI 提供程序的使用为每24小时一次。

在每年的头一天，UAL 会创建一个新的 *GUID.mdb*。 旧的 *GUID* 将保留为用于提供程序的存档。  两年后，原始的 *GUID.mdb* 将被覆盖。

> [!IMPORTANT]
> 下面的步骤只能由高级用户执行，并且通常会由测试自己的 UAL 应用程序编程接口仪表的开发者使用……

#### <a name="to-adjust-the-default-24-hour-interval-to-make-data-visible-to-the-wmi-provider"></a>调整默认的 24 小时间隔，使数据对 WMI 提供者可见

1.  使用有本地管理员权限的帐户登录服务器。

2.  按 Windows 徽标键 + R，然后键入“cmd”**** 打开命令提示符窗口。

3.  添加注册表值：  **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\WMI\AutoLogger\Sum\PollingInterval (REG_DWORD)**。

    > [!WARNING]
    > 不正确地编辑注册表可能会对系统造成严重损坏。 在更改注册表之前，应当备份计算机上任何有价值的数据。

    下面的示例演示如何添加一个两分钟的间隔 (不推荐为长期运行状态) ： **REG add HKLM\System\CurrentControlSet\Control\WMI \\ AutoLogger\Sum/v POLLINGINTERVAL/T REG \_ DWORD/d 120000/f**

    时间值以毫秒为单位。 最小值是 60 秒，最大值是七天，默认值是 24 小时。

4.  使用服务控制台停止和重启 User Access Logging Service。

## <a name="deleting-data-logged-by-ual"></a>删除 UAL 记录的数据
UAL 意图不在于充当一个关键任务组件。 它的设计目的是在保持高水平的可靠性的同时尽可能小地影响本地系统操作。 这也允许管理员手动删除 UAL 数据库和支持文件 (\Windows\System32\LogFilesSUM\ directory) 中的每个文件，以满足操作需求。

#### <a name="to-delete-data-logged-by-ual"></a>删除 UAL 记录的数据的步骤

1. 停止 User Access Logging Service。

2. 打开 Windows 资源管理器。

3. 请参阅**\Windows\System32\Logfiles\SUM \\ **。

4. 删除文件夹中的所有文件。

## <a name="managing-ual-in-high-volume-environments"></a>在大容量环境中管理 UAL
本部分描述了在高客户端容量的服务器上使用 UAL 时，管理员可以期待什么：

UAL 可以记录的最大访问次数是每天 65,535。不建议在直接连接到 Internet 的服务器，如直接连接到 Internet 的 web 服务器上，或在极高性能是服务器主要功能的应用场景下（如在 HPC 工作负载环境中）使用 UAL。 UAL 主要用于小型、中型和企业内部网方案，其中应有高容量，但并不像处理面向 Internet 的流量的部署那样高。

**内存中的 UAL**：因为 UAL 使用可扩展存储引擎 (ESE) ，所以 UAL 的内存要求将随着时间的推移 (或) 的客户端请求数量而增加。 但由于系统要求它最小化对系统性能的影响，这些存储空间又会被释放。

**磁盘上的 UAL**： UAL 的硬盘要求大致如下所示：

-   0 条唯一客户端记录：22 M

-   50,000 条唯一客户端记录：80 M

-   500,000 条唯一客户端记录：384 M

-   1,000,000 条唯一客户端记录：729 M

## <a name="recovering-from-a-corrupt-state"></a>从损坏状态恢复
本部分讨论了 UAL 在高级别上使用的可扩展存储引擎 (ESE) ，以及在 UAL 数据损坏或不可恢复时管理员可以执行的操作。

UAL 使用 ESE 来优化系统资源的使用，并支持防止损坏。  有关 ESE 优点的详细信息，请参阅 MSDN 上的 [可扩展存储引擎](/windows/win32/extensible-storage-engine/extensible-storage-engine) 。

每次 UAL 服务启动 ESE，都会执行一次软恢复。 有关详细信息，请参阅 MSDN 上的 [可扩展存储引擎文件](/windows/win32/extensible-storage-engine/extensible-storage-engine-files) 。

如果软恢复出现问题，ESE 将执行崩溃恢复。 有关详细信息，请参阅 MSDN 上的 [JetInit 函数](/windows/win32/extensible-storage-engine/jetinit-function) 。

如果 UAL 仍然无法以现有的 ESE 文件集启动，它将删除 \Windows\System32\LogFiles\SUM\ 目录中的所有文件。 删除这些文件后，将重启 User Access Logging Service 并创建新文件。 随后将如同在新安装的计算机上那样恢复 UAL 服务。

> [!IMPORTANT]
> UAL 数据库目录中的文件永远不能移动或修改。 这样做将启动恢复步骤，包括这个部分中描述的清理线程。 如果需要 \Windows\System32\LogFiles\SUM\ 目录的备份，那么必须一起备份此目录中的每个文件，以便恢复操作能够按预期执行。

## <a name="enable-work-folders-usage-license-tracking"></a>启用工作文件夹使用情况许可证跟踪
工作文件夹服务器可以使用 UAL 报告客户端使用情况。 与 UAL 不同，工作文件夹日志记录未默认打开。 可以使用以下 regkey 更改启用它：

```
Reg add HKLM\Software\Microsoft\Windows\CurrentVersion\SyncShareSrv /v EnableWorkFoldersUAL /t REG_DWORD /d 1
```

添加 regkey 后，必须在服务器上重启 SyncShareSvc 服务，以启用日志记录。

启用日志记录后，客户端每次连接到服务器时，2 条信息性事件会记录到“Windows 日志\应用程序”通道。 对于工作文件夹，每个用户可以拥有一个或多个连接到服务器的客户端设备，并每 10 分钟检查一次数据更新。 如果服务器遇到 1000 名用户且每名用户有 2 个设备，那么应用程序日志将每 70 分钟执行一次覆盖操作，这让对非相关问题进行故障排除变得困难。 若要避免这种情况，可以暂时禁用用户访问日志记录服务，或增加服务器的 Windows 日志通道的大小。

## <a name="see-also"></a><a name="BKMK_Links"></a>另请参阅

- [用户访问日志记录入门](get-started-with-user-access-logging.md)