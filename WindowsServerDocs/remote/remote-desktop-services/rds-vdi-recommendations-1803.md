---
title: 针对虚拟桌面基础结构 (VDI) 角色优化 Windows 10 版本 1803
description: 建议的设置和配置，可最大程度减少用作 VDI 映像的 Windows 10 1803 桌面的开销
ms.author: robsmi
ms.topic: article
author: jaimeo
ms.openlocfilehash: 4ba432e13785694844229a41f2966eb7cf65fa7e
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078634"
---
# <a name="optimizing-windows-10-version-1803-for-a-virtual-desktop-infrastructure-vdi-role"></a>针对虚拟桌面基础结构 (VDI) 角色优化 Windows 10 版本 1803

本文帮助你选择可为虚拟化桌面基础结构 (VDI) 环境提供最佳性能的 Windows 10 版本 1803（内部版本 17134）设置。 本指南中的所有设置都是建议考虑的设置，并非一定要采用这些设置。

在 VDI 环境中，优化 Windows 10 性能的关键方法是尽量减少应用图形重绘，将不会对 VDI 环境带来重要优势的活动置于后台，并一般性地将运行的进程减到最少。 次要目标是将基本映像中的磁盘空间用量减到最少。 使用 VDI 实现（可能最小的基准或“黄金”映像大小）可以轻微减少虚拟机监控程序中的内存用量，并小幅减少向使用者交付桌面映像所需的网络操作总数。

> [!NOTE]
> 此处建议的设置可应用于其他 Windows 10 版本 1803 安装，包括物理设备或其他虚拟设备上的安装。 本主题中的任何建议都不应影响 Windows 10 版本 1803 的支持性。

> [!TIP]
> GitHub 上的 [TheVDIGuys](https://github.com//TheVDIGuys) 中提供了本主题中所述的用于实现优化的脚本，以及一个可以使用 **LGPO.exe** 导入的 GPO 导出文件。

## <a name="vdi-optimization-principles"></a>VDI 优化原则

VDI 环境通过网络向计算机用户提供完整的桌面会话（包括应用程序）。 VDI 环境通常使用基本操作系统映像，该映像是随后要向用户提供的（使其能够完成工作）的桌面的基础。 VDI 实现有一些变体，例如“持久性”、“非持久性”和“桌面会话”。 切换会话时，持久类型会保留对 VDI 桌面操作系统所做的更改。 切换会话时，非持久类型不会保留对 VDI 桌面操作系统所做的更改。 对于用户而言，此桌面与其他虚拟或物理设备略有不同，不过需要通过网络来访问它。

优化设置在参照设备上发生。 VM 是生成映像的理想位置，因为可以保存状态、创建检查点和备份，以及执行其他有用的任务。 首先在基础 VM 上安装默认操作系统，然后通过删除不需要的应用、安装 Windows 更新、安装其他更新、删除临时文件、应用设置等，来根据 VDI 的用法优化基础 VM。

还存在持久性和远程桌面服务 (RDS) 等其他类型的 VDI。 本主题不会深入介绍这些技术，而是侧重于参考环境中的其他因素（例如主机优化）介绍 Windows 基本映像的设置。

### <a name="persistent-vdi"></a>持久性 VDI

从根本上讲，持久性 VDI 是每次重启都能保存操作系统状态的 VM。 VDI 解决方案的其他软件层可让用户轻松顺畅地访问为其分配的 VM（通常是使用单一登录解决方案）。

持久性 VDI 有多种不同的实现：

- 传统虚拟机，其中的 VM 具有自身的虚拟磁盘文件，可正常启动，切换会话时可保存更改，在本质上只是普通的 VM。 差别在于用户访问此 VM 的方式。 可能会提供一个 Web 门户让用户登录，然后用户会自动定向到为其分配的一个或多个 VDI VM。

- 包含个人虚拟磁盘的基于映像的持久性虚拟机。 在此类实现中，一个或多个主机服务器包含基本/黄金映像。 将会创建一个 VM 以及一个或多个虚拟磁盘，并将此磁盘分配为持久性存储。

    - 启动 VM 时，会将基本映像的副本读入 VM 的内存。 同时，会将一个持久性虚拟磁盘分配到该 VM，以前发生的任何操作系统更改将通过复杂的过程合并。

    - 事件日志写入、日志写入等更改将重定向到分配给该 VM 的读/写虚拟磁盘。

    - 在此情况下，操作系统和应用服务可以使用传统的服务软件（例如 Windows Server 更新服务）或其他管理技术正常运行。

### <a name="non-persistent-vdi"></a>非持久性 VDI

如果非持久性 VDI 实现基于基本映像或“黄金”映像，则优化主要在基本映像中执行，然后通过本地设置和本地策略执行。

使用基于映像的非持久性 VDI 时，基本映像是只读的。 启动非持久性 VDI VM 时，会将基本映像的副本流式传输到 VM。 从启动开始一直到下一次重新启动为止所发生的活动将重定向到临时位置。 通常为用户提供一个网络位置用于存储其数据。 在某些情况下，用户的配置文件将与标准 VM 合并，以便为用户提供设置。

维护是基于单一映像的非持久性 VDI 需要考虑的一个重要方面。 通常每隔一月提供操作系统的更新。
使用基于映像的 VDI 时，可以执行一系列过程来获取映像的更新：

- 给定主机上派生自基本映像的所有 VM 必须已关闭或禁用。 这意味着，用户将重定向到其他 VM。

- 然后，基本映像将会打开并启动。 然后执行所有维护活动，例如操作系统更新、.NET 更新、应用更新，等等。

- 此时将会应用需要应用的任何新设置。

- 此时会执行任何其他维护。

- 然后，基本映像关闭。

- 基本映像是密封的，设置为传回到生产环境。

-允许用户重新登录。

> [!NOTE]
> Windows 10 定期自动执行一系列维护任务。 有一个计划的任务设置为默认在每天当地时间凌晨 3:00 运行。 此计划任务执行一系列任务，包括 Windows 更新清理。 可以使用以下 PowerShell 命令查看自动执行的所有维护类别：
>
>```powershell
>Get-ScheduledTask | ? {$_.Settings.MaintenanceSettings}
>```
>

非持久性 VDI 的弊端之一是当用户注销时，几乎所有的操作系统活动都将被丢弃。 用户的配置文件和/或状态可能会保存，但虚拟机本身会丢弃自上次启动以来所做的几乎所有更改。 因此，针对每次切换会话都会保存状态的 Windows 计算机所做的优化并不适用。

根据 VDI VM 的体系结构，PreFetch 和 SuperFetch 等功能无助于切换会话时的状态保存，因为 VM 重启后会丢弃所有优化设置。 索引可能会给资源带来一定的浪费，传统的碎片整理等磁盘优化方法也是如此。

### <a name="to-sysprep-or-not-sysprep"></a>运行或者不运行 Sysprep

Windows 10 有一项名为[系统准备工具](/windows-hardware/manufacture/desktop/sysprep--system-preparation--overview)（通常简写为“Sysprep”）的内置功能。 使用 Sysprep 工具可以准备一个自定义的 Windows 10 映像供复制。 Sysprep 进程确保生成的操作系统具有独特性，可在生产环境中正常运行。
运行或者不运行 Sysprep 都有适当的理由。 使用 VDI 时，你可能希望能够自定义默认用户配置文件，后续用户在使用此映像登录时，可将此配置文件用作模板。 你可能已经安装了所需的应用，同时希望能够控制每个应用的设置。

替代方法是使用标准 .ISO 进行安装（也许可以使用无人参与的安装应答文件），并使用任务序列来安装或删除应用程序。 还可以使用任务序列在映像中设置本地策略设置（也许可以使用[本地组策略对象实用工具 (LGPO)](/archive/blogs/secguide/lgpo-exe-local-group-policy-object-utility-v1-0)）。

#### <a name="vdi-optimization-categories"></a>VDI 优化类别

- 全局操作系统设置

    - UWP 应用清理

    - 可选功能清理

    - 本地策略设置

    - 系统服务

    -   计划任务

    -   应用 Windows 更新

    -   自动 Windows 跟踪

    -   完成（密封）映像之前的磁盘清理

-   用户设置

-   虚拟机监控程序/主机设置

- [使用注册表设置优化 Windows 10 网络性能](#tuning-windows-10-network-performance-by-using-registry-settings)

- [Windows 受限流量限制功能基线](https://go.microsoft.com/fwlink/?linkid=828887)指南中所述的其他设置。

- [磁盘清理](#disk-cleanup-including-using-the-disk-cleanup-wizard)

### <a name="universal-windows-platform-app-cleanup"></a>通用 Windows 平台应用清理

VDI 映像的目标之一是尽量精简。 减小映像大小的方法之一是删除环境中用不到的 UWP 应用程序。 UWP 应用附带一些应用程序主文件（称为有效负载）。 每个用户的配置文件中存储了有关应用程序特定设置的少量数据。 此外，“所有用户”配置文件中也包含少量的数据。

执行 UWP 应用清理时，只需建立连接并设置好计时即可。 如果将基本映像部署到了未建立网络连接的设备，则 Windows 10 无法连接到 Microsoft Store 和下载应用，并会在你尝试卸载应用时安装应用。

如果修改用于安装 Windows 10 的 .WIM 基本映像，并在安装之前从 .WIM 中删除了不需要的 UWP 应用，则应用不会开始安装，并且配置文件创建时间会缩短。 本部分稍后会提供有关如何从安装 .WIM 文件中删除 UWP 应用的信息。

对于 VDI，一种良好的策略是在基本映像中预配所需的应用，然后限制或阻止访问 Microsoft Store。 在普通的计算机上，Store 应用会定期在后台更新。 在维护期间，可以在应用其他更新的同时更新 UWP 应用。

#### <a name="delete-the-payload-of-uwp-apps"></a>删除 UWP 应用的有效负载

不需要的 UWP 应用仍保留在文件系统中，它们会消耗少量的磁盘空间。 对于永远不需要的应用，可以使用 PowerShell 命令从基本映像中删除不需要的 UWP 应用的有效负载。

事实上，如果使用本部分稍后提供的链接从安装 .WIM 文件中删除这些应用，则应该可以从极少量的 UWP 应用着手。

运行以下命令枚举正在运行的 Windows 10 操作系统中预配的 UWP 应用，如以下截断的 PowerShell 示例输出中所示：

```powershell

    Get-AppxProvisionedPackage -Online

    DisplayName  : Microsoft.3DBuilder
    Version      : 13.0.10349.0
    Architecture : neutral
    ResourceId   : \~
    PackageName  : Microsoft.3DBuilder_13.0.10349.0_neutral_\~_8wekyb3d8bbwe
    Regions      :
```

预配到系统的 UWP 应用可以在安装操作系统期间作为任务序列的一部分删除，也可以在安装操作系统后删除。 这可能是首选的方法，因为这样可使创建或维护映像的整个过程模块化。 开发脚本后，如果后续的生成发生更改，则你可以编辑现有的脚本，而无需从头开始重复该过程。 下面是有关本主题的信息的链接：

[在执行任务序列期间删除 Windows 10 内置应用](/archive/blogs/mniehaus/removing-windows-10-in-box-apps-during-a-task-sequence)

[使用 Powershell 从 Windows 10 WIM 文件中删除内置应用 - 版本 1.3](https://gallery.technet.microsoft.com/Removing-Built-in-apps-65dc387b)

[Windows 10 1607：部署功能更新时防止应用回滚](/archive/blogs/mniehaus/windows-10-1607-keeping-apps-from-coming-back-when-deploying-the-feature-update)

然后运行 [Remove-AppxProvisionedPackage](/powershell/module/dism/remove-appxprovisionedpackage?view=win10-ps) PowerShell 命令删除 UWP 应用有效负载：

```powershell
Remove-AppxProvisionedPackage -Online -PackageName
```

应在每个独特的环境中评估每个 UWP 应用的适用性。 可以使用默认设置安装 Windows 10 版本 1803，然后留意哪些应用正在运行并消耗了内存。 例如，可以考虑删除自动启动的应用、在“开始”菜单中自动显示信息的应用（例如“天气”和“新闻”），以及在环境中没有作用的应用。

有一个“内置”的 UWP 应用称为“照片”，它采用默认设置“有新的相册可用时显示通知”。  照片应用可能会占用大约 145 MB 的内存；特别是，即使不使用它，它也会占用专用的工作集内存。  目前，无法针对所有用户更改“有新的相册可用时显示通知”设置，因此，建议在不需要照片应用时将其删除。

### <a name="clean-up-optional-features"></a>清理可选功能

#### <a name="managing-optional-features-with-powershell"></a>使用 PowerShell 管理可选功能

 若要枚举当前已安装的 Windows 功能，请运行以下 PowerShell 命令：

```powershell
Get-WindowsOptionalFeature -Online
```

可按以下示例中所示启用或禁用特定的 Windows 可选功能：

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName "DirectPlay"
```

有关详细信息，请参阅 [Windows PowerShell 论坛](/answers/topics/windows-server-powershell.ht)。

#### <a name="enable-or-disable-windows-features-by-using-dism"></a>使用 DISM 启用或禁用 Windows 功能

可以使用内置的 **Dism.exe** 工具来枚举和控制 Windows 可选功能。 可以设置一个在执行安装操作系统的任务序列期间运行的 Dism.exe 脚本。

### <a name="local-policy-settings"></a>本地策略设置

适用于 VDI 环境中 Windows 10 的很多优化都可以使用 Windows 策略来进行。 此处列出的设置可在本地应用到基本映像。 然后未以任何其他方式（例如，按组策略）指定等效的设置，则仍会应用这些设置。

某些决策可能基于环境的具体情况，例如：

-   是否允许 VDI 环境访问 Internet？

-   VDI 解决方案是持久性还是非持久性的？

具体而言，以下设置不会与安全相关的任何设置相冲突。 选择这些设置是为了删除不适用于 VDI 环境的设置。

> [!NOTE]
> 在此组策略设置表中，带星号的项摘自 [Windows 受限流量限制功能基线](https://go.microsoft.com/fwlink/?linkid=828887)。

| 策略设置 | 项 | 子项 | 可能的设置和备注 |
|--|--|--|--|
| **本地计算机策略 \\ 计算机配置 \\ Windows 设置 \\ 安全设置** |  |  |  |
| **网络列表管理器策略** | 所有网络属性 | 网络位置 | 用户不能更改位置 |
| **本地计算机策略 \\ 计算机配置 \\ 管理模板 \\ 控制面板** |  |  |  |
| \***控制面板** | 允许在线提示 |  | 已禁用（设置不会联系 Microsoft 内容与服务来检索提示和帮助内容） |
| **\*控制面板**\\ 个性化 | 不显示锁屏界面 |  | 已启用（此策略设置控制是否向用户显示锁屏界面。 如果启用此策略设置，则在登录之前无需按 CTRL + ALT + DEL 的用户在锁定电脑后会看到选定的磁贴。） |
| **\*控制面板**\\ 个性化 | 强制特定的默认锁屏界面和登录图像 | [![用于设置锁屏界面图像的 UI 插图](media/lock-screen-image-settings.png)](media/lock-screen-image-settings.png) | 已启用（使用此设置可以指定在没有任何用户登录的情况下显示的默认锁屏界面和登录图像，以及将指定的图像设置为所有用户的默认图像 - 替换默认图像。）使用低分辨率的简单图像可以减少每次呈现图像时通过网络传输的数据量。 |
| **\*控制面板**\\ 区域和语言选项\\手写个性化 | 关闭自动学习 |  | 已启用（如果启用此策略设置，则会停止自动学习，并删除所有存储的数据。 用户无法在控制面板中配置此设置） |
| **本地计算机策略 \\ 计算机配置 \\ 管理模板 \\ 网络** |  |  |  |
| **后台智能传输服务 (BITS)** | 不允许 BITS 客户端使用 Windows 分支缓存 |  | 启用 |
| **后台智能传输服务 (BITS)** | 不允许计算机作为 BITS 对等缓存客户端 |  | 启用 |
| **后台智能传输服务 (BITS)** | 不允许计算机作为 BITS 对等缓存服务器 |  | 启用 |
| **后台智能传输服务 (BITS)** | 允许 BITS 对等缓存 |  | 禁用 |
| **BranchCache** | 打开 BranchCache |  | 禁用 |
| \***字体** | 启用字体提供程序 |  | 已禁用（Windows 不会连接到联机字体提供程序，只会枚举本地安装的字体。） |
| **热点身份验证** | 启用热点身份验证 |  | 禁用 |
| **Microsoft 对等网络服务** | 关闭 Microsoft 对等网络服务 |  | 启用 |
| **网络连接状态指示器**（请注意，在隔离的网络中可以使用本部分所述的其他一些设置） | 指定被动轮询 | 禁用被动轮询（复选框） | 已启用（如果在隔离的网络中操作，或者使用静态 IP 地址，请使用此设置。） |
| **脱机文件** | 允许或不允许使用“脱机文件”功能 |  | 禁用 |
| **\*TCPIP 设置**\\ IPv6 转换技术 | 设置 Teredo 状态 | 已禁用状态 | 已启用（处于禁用状态时，不会在主机上显示 Teredo 界面。） |
| **\*WLAN 服务**\\ WLAN 设置 | 允许 Windows 自动连接到建议的开放热点、联系人共享的网络以及提供付费服务的热点 |  | 已禁用（“连接到建议的开放热点”、“连接到我的联系人共享的网络”和“启用付费服务”将会关闭，并会阻止此设备上的用户启用这些设置。） |
| **本地计算机策略 \\ 计算机配置 \\ 管理模板 \\ 开始菜单和任务栏** |  |  |  |
| \***通知** | 关闭通知网络的使用 |  | 已启用（如果启用此策略设置，则应用程序和系统功能将无法通过 WNS 或通知轮询 API 从网络接收通知。） |
| **本地计算机策略 \\ 计算机配置 \\ 管理模板 \\ 系统** |  |  |  |
| **设备安装** | 在设备上安装通用驱动程序时，不发送 Windows 错误报告 |  | 启用 |
| **设备安装** | 禁止在通常会提示创建还原点的设备活动过程中创建系统还原点 |  | 启用 |
| **设备安装** | 禁止从 Internet 进行设备元数据检索 |  | 启用 |
| **设备安装** | 当设备驱动程序在安装过程中请求附加软件时，禁止 Windows 发送错误报告 |  | 启用 |
| **设备安装** | 安装设备过程中禁用“找到新硬件”气球 |  | 启用 |
| **文件系统**\\NTFS | 短名称创建选项 | 已在所有卷上禁用 | 启用 |
| \***组策略** | 使用应用 URI 处理程序配置 Web 到应用链接 |  | 已禁用（禁用 Web 到应用链接，http(s) URI 将在默认浏览器中打开，而不是启动关联的应用。） |
| \***组策略** | 在此设备上继续体验 |  | 已禁用（Windows 设备不可由其他设备发现，且不能参与跨设备体验） |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭对所有 Windows 更新功能的访问 |  | 已启用（如果启用此策略设置，则会删除所有 Windows 更新功能。 这包括阻止从“开始”菜单以及 Internet Explorer 的“工具”菜单中的“Windows 更新”超链接访问 Windows 更新网站 https://windowsupdate.microsoft.com 。 Windows 自动更新也会禁用；你不会收到 Windows 更新提供的关键更新，也不会收到相关通知。 此策略设置还会阻止设备管理器自动安装 Windows 更新网站中的驱动程序更新。） |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭自动根证书更新 |  | 已启用（如果启用此策略设置，当你看到不受信任的根证书颁发机构颁发的证书时，你的计算机不会联系 Windows 更新网站来查看 Microsoft 是否已将该 CA 添加到受信任颁发机构列表。）  **注意：** 仅当你有最新证书吊销列表的替代方案时，才使用此策略。 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭事件查看器“Events.asp”链接 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭手写个性化数据共享 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭手写识别错误报告 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭帮助和支持中心“你知道吗?” 内容 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭帮助和支持中心 Microsoft 知识库搜索 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 如果 URL 连接指向 Microsoft.com，则关闭 Internet 连接向导 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭 Web 发布和在线订购向导的 Internet 下载 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭 Internet 文件关联服务 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 如果 URL 连接指向 Microsoft.com，则关闭注册 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭“订购打印”照片任务 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭文件和文件夹的“发布到 Web”任务 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭 Windows Messenger 客户体验改善计划 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭 Windows 客户体验改善计划 |  | 启用 |
| **\*Internet 通信管理**\\ Internet 通信设置 | 关闭 Windows 网络连接状态指示器的活动测试 |  | 已启用（此策略设置将关闭 Windows 网络连接状态指示器 (NCSI) 为了确定你的计算机是否连接到 Internet 或限制性更高的网络而执行的活动测试。在确定连接级别过程中，NCSI 将执行两项活动测试中的一项：从专用 Web 服务器下载某个页面，或者针对专用地址发出 DNS 请求。 如果启用此策略设置，则 NCSI 不会运行这两项活动测试中的任何一项。 这可能会减弱 NCSI 以及使用 NCSI 的其他组件确定 Internet 访问状态的能力）注意：如果需要此功能，可以使用其他一些策略将 NCSI 测试重定向到内部资源。 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭 Windows 错误报告 |  | 启用 |
| **Internet 通信管理**\\ Internet 通信设置 | 关闭 Windows 更新设备驱动程序搜索 |  | 启用 |
| **登录** | 显示首次登录动画 |  | 禁用 |
| **登录** | 关闭锁屏界面上的应用通知 |  | 启用 |
| **登录** | 关闭 Windows 启动声音 |  | 启用 |
| **电源管理** | 选择当前电源计划 | 高性能 | 启用 |
| **恢复** | 允许将系统还原到默认状态 |  | 禁用 |
| \***存储运行状况** | 允许下载磁盘故障预测模型的更新 |  | 已禁用（不会下载磁盘故障预测模型的更新） |
| \***Windows 时间服务**\\ 时间提供程序 | 启用 Windows NTP 客户端 |  | 已禁用（如果禁用或不配置此策略设置，则本地计算机时钟时间不会与 NTP 服务器同步）**注意**：请慎重考虑此设置。 已加入域的 Windows 设备应使用 **NT5DS**。 父域 DC 可以使用 NTP。 PDCe 角色可以使用 NTP。 虚拟机有时使用“增强功能”或“集成服务”。 |
| **故障排除和诊断**\\ 计划内维护 | 配置计划内维护行为 |  | 禁用 |
| **故障排除和诊断**\\ Windows 启动性能诊断 | 配置方案执行级别 |  | 禁用 |
| **故障排除和诊断**\\ Windows 内存泄漏诊断 | 配置方案执行级别 |  | 禁用 |
| **故障排除和诊断**\\ Windows 资源耗尽检测和解决方法 | 配置方案执行级别 |  | 禁用 |
| **故障排除和诊断**\\ Windows 关机性能诊断 | 配置方案执行级别 |  | 禁用 |
| **故障排除和诊断**\\ Windows 待机/恢复性能诊断 | 配置方案执行级别 |  | 禁用 |
| **故障排除和诊断**\\ Windows 系统响应性能诊断 | 配置方案执行级别 |  | 禁用 |
| \***用户配置文件** | 关闭广告 ID |  | 已启用（如果启用此策略设置，将会关闭广告 ID。 应用无法对跨应用的体验使用该 ID。） |
| **本地计算机策略 \\ 计算机配置 \\ 管理模板 \\ Windows 组件** |  |  |  |
| **将功能添加到 Windows 10** | 阻止向导运行 |  | 启用 |
| \***应用隐私** | 允许 Windows 应用访问帐户信息 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问帐户信息；组织中的员工无法更改此设置） |
| \***应用隐私** | 允许 Windows 应用访问通话历史记录 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问通话历史记录；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问通讯录 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问联系人；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问有关其他应用的诊断信息 | 所有应用的默认设置：强制拒绝 | 已启用（如果禁用或不配置此策略设置，则组织中的员工可以使用设备上的“设置”\>“隐私”来决定是否允许 Windows 应用获取有关其他应用的诊断信息） |
| \***应用隐私** | 允许 Windows 应用访问电子邮件 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制允许”选项，则允许 Windows 应用访问电子邮件；组织中的员工无法更改此设置） |
| \***应用隐私** | 允许 Windows 应用访问位置 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问位置；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问消息 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问位置；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问运动数据 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问运动数据；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问通知 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问通知；组织中的员工无法更改此设置） |
| \***应用隐私** | 允许 Windows 应用访问任务 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问任务；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问日历 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问日历；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问相机 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问相机；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问麦克风 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问麦克风；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问受信任的设备 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用访问受信任的设备；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用与未配对的设备通信 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用与未配对的无线设备通信；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用访问电台 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则 Windows 应用将无法访问控制电台；组织中的员工无法更改此设置。） |
| **应用隐私** | 允许 Windows 应用拨打电话 | 所有应用的默认设置：强制拒绝 | 已启用（不允许 Windows 应用拨打电话；组织中的员工无法更改此设置。） |
| \***应用隐私** | 允许 Windows 应用在后台运行 | 所有应用的默认设置：强制拒绝 | 已启用（如果选择“强制拒绝”选项，则不允许 Windows 应用在后台运行；组织中的员工无法更改此设置。） |
| **自动播放策略** | 设置“自动运行”的默认行为 | 不执行任何自动运行命令 | 启用 |
| \***自动播放策略** | 关闭自动播放 |  | 已启用（如果启用此策略设置，则会在 CD-ROM 和可移动媒体驱动器或所有驱动器上禁用自动播放。） |
| \***云内容** | 不显示 Windows 提示 |  | 已启用（此策略设置可防止向用户显示 Windows 提示。） |
| \***云内容** | 关闭 Microsoft 消费者体验 |  | 已启用（如果启用此策略设置，用户不再会看到 Microsoft 提供的个性化建议，以及有关其 Microsoft 帐户的通知。） |
| \***数据收集和预览版** | 允许遥测 | 0 - 安全性 [仅适用于企业版] | 已启用（0 值设置仅适用于运行企业版、教育版、IoT 版或 Windows Server 版的设备。） |
| \***数据收集和预览版** | 请不要显示反馈通知 |  | 启用 |
| \***数据收集和预览版** | 切换对 Insider 版本的用户控制 |  | 禁用 |
| **传递优化** | 下载模式 | 下载模式：简单 (99) | 99 = 没有对等的简单下载模式。 传递优化仅使用 HTTP 下载，而不会尝试联系传递优化云服务。 |
| **桌面窗口管理器** | 不允许调用 Flip3D |  | 启用 |
| **桌面窗口管理器** | 不允许使用窗口动画 |  | 启用 |
| **桌面窗口管理器** | 对“开始”屏幕背景图片使用纯色 |  | 启用 |
| **Edge UI** | 允许轻扫边缘 |  | 禁用 |
| **Edge UI** | 禁用帮助提示 |  | 启用 |
| \***文件资源管理器** | 配置 Windows Defender SmartScreen |  | 已禁用（对所有用户关闭 SmartScreen。 用户尝试运行 Internet 中的可疑应用时不会看到警告。） |
|  |  |  | **注意**：如果未连接到 Internet，此设置可防止计算机尝试联系 Microsoft 获取 SmartScreen 信息。 |
| **文件资源管理器** | 不显示“安装了新应用程序”通知 |  | 启用 |
| \***查找我的设备** | 打开/关闭“查找我的设备” |  | 已禁用（如果关闭“查找我的设备”，则不会注册设备及其位置，“查找我的设备”功能将不起作用。 此外，用户无法在其设备上查看活动数字化器的上次使用位置。） |
| **游戏资源管理器** | 禁止下载游戏信息 |  | 启用 |
| **游戏资源管理器** | 关闭游戏更新 |  | 启用 |
| **游戏资源管理器** | 禁止跟踪“游戏”文件夹中的上次游戏时间 |  | 启用 |
| **家庭组** | 阻止计算机加入家庭组 |  | 启用 |
| \***Internet Explorer** | 允许 Microsoft 服务在用户向地址栏中键入内容时提供增强建议 |  | 已禁用（用户在地址栏中键入内容时将不会收到增强建议。 此外，用户将无法更改“建议”设置。） |
| **Internet Explorer** | 禁用 Internet Explorer 软件更新的定期检查 |  | 启用 |
| **Internet Explorer** | 禁止显示初始屏幕 |  | 启用 |
| **Internet Explorer** | 自动安装新版本的 Internet Explorer |  | 禁用 |
| **Internet Explorer** | 阻止参与客户体验改善计划 |  | 启用 |
| **Internet Explorer** | 阻止运行“首次运行”向导 | 直接转到主页 | 启用 |
| **Internet Explorer** | 设置标签页进程增长 | 低 | 启用 |
| **Internet Explorer** | 指定新标签页的默认行为 | 新建标签页 | 启用 |
| **Internet Explorer** | 关闭加载项性能通知 |  | 启用 |
| \***Internet Explorer** | 关闭 Web 地址的自动完成功能 |  | 已启用（如果启用此策略设置，当用户输入网址时，系统不会向其显示匹配项。 用户无法更改网址自动填充的设置。） |
| \***Internet Explorer** | 关闭浏览器地理位置 |  | 已启用（如果启用此策略设置，则会关闭浏览器地理位置支持。） |
| **Internet Explorer** | 禁止重新打开上次浏览会话 |  | 启用 |
| \***Internet Explorer** | 打开建议网站 |  | 已禁用（如果禁用此策略设置，则会关闭入口点以及与与此功能相关的功能。） |
| **\*Internet Explorer**\\ 兼容性视图 | 关闭兼容性视图 |  | 已启用（如果启用此策略设置，则用户无法使用“兼容性视图”按钮或管理“兼容性视图”站点列表。） |
| **Internet Explorer**\\ Internet 控制面板<strong>\\</strong> 高级页 | 在网页中播放动画 |  | 禁用 |
| **Internet Explorer**\\ Internet 控制面板\\ 高级页 | 在网页中播放视频 |  | 禁用 |
| **\*Internet Explorer**\\ Internet 控制面板\\ 高级页 | 关闭通过页面预测而快速翻页功能 |  | 已启用（Microsoft 将收集你的浏览历史记录，以便改进通过页面预测快速翻页的工作方式。 此功能对于适用于桌面版的 Internet Explorer 不可用。 如果启用此策略设置，将关闭通过页面预测快速翻页功能，下一网页将不会加载到后台。） |
| **Internet Explorer**\\ Internet 设置\\ 高级设置\\ 浏览 | 关闭电话号码检测 |  | 启用 |
| **Internet Explorer**\\ Internet 设置\\ 高级设置\\ 多媒体 | 允许 Internet Explorer 播放使用备用编解码器的媒体文件 |  | 禁用 |
| \***定位和传感器** | 关闭定位 |  | 已启用（如果启用此策略设置，则会关闭定位功能，并会阻止此计算机上的所有程序使用定位功能中的位置信息。） |
| **定位和传感器** | 关闭传感器 |  | 启用 |
| **定位和传感器 /** Windows 定位程序 | 关闭 Windows 定位程序 |  | 启用 |
| \***地图** | 关闭地图数据的自动下载和更新 |  | 已启用（如果启用此设置，则会关闭地图数据的自动下载和更新。） |
| \***地图** | 在“脱机地图”设置页面关闭未经请求的网络流量 |  | 已启用（如果启用此策略设置，则会关闭在离线地图设置页上生成网络流量的功能。 注意：这可能会关闭整个设置页。） |
| \***消息** | 允许消息服务云同步 |  | 已禁用（此策略设置允许将手机短信备份和还原到 Microsoft 的云服务。） |
| \***Microsoft Edge** | 允许使用地址栏下拉列表建议 |  | 禁用 |
| \***Microsoft Edge** | 允许对书籍库进行配置更新 |  | 已禁用（关闭 Microsoft Edge 中的兼容性列表。） |
| \***Microsoft Edge** | 允许 Microsoft 兼容性列表 |  | 已禁用（如果禁用此设置，则不会在浏览器导航期间使用 Microsoft 兼容性列表。） |
| \***Microsoft Edge** | 允许“新建选项卡”页面中的 Web 内容 |  | 已禁用（打开新标签页时，指示 Microsoft Edge 打开空白页面。） |
| \***Microsoft Edge** | 配置自动填充 |  | 已禁用（禁用地址栏自动填充。） |
| \***Microsoft Edge** | 配置 Do Not Track |  | 已启用（如果启用此设置，则始终向要求跟踪信息的网站发送“禁止跟踪”请求。） |
| \***Microsoft Edge** | 配置密码管理器 |  | 已禁用（如果禁用此设置，则员工无法使用密码管理器本地保存其密码。） |
| \***Microsoft Edge** | 配置地址栏中的搜索建议 |  | 已禁用（用户无法在 Microsoft Edge 的地址栏中看到搜索建议。） |
| \***Microsoft Edge** | 配置“开始”页面 |  | 已启用（如果启用此设置，则可以配置一个或多个“开始”页面。） 如果此设置已启用，还必须包含这些页面的 URL，使用尖括号分隔多个页面，格式如下：\<support.contoso.com\>\<support.microsoft.com\> Windows 10，版本 1703 或更高版本：如果不想要将流量发送到 Microsoft，可以使用 \<about:blank\> 值，如果这是配置的唯一 URL，则不管设备是否已加入域，都会采用此设置。 |
| \***Microsoft Edge** | 配置 Windows Defender SmartScreen |  | 已禁用（将会关闭 Windows Defender SmartScreen；员工无法打开它。） |
|  |  |  | **注意**：请考虑在环境中使用此设置。 如果未连接到 Internet，此设置可防止计算机尝试联系 Microsoft 获取 SmartScreen 信息。 |
| \***Microsoft Edge** | 阻止在 Microsoft Edge 中打开首次运行网页 |  | **已启用**（首次打开 Microsoft Edge 时，用户不会看到“首次运行”页。） |
| **OneDrive** | 用户登录到 OneDrive 之前阻止 OneDrive 产生网络流量 |  | **已启用**（启用此设置可以在用户登录到 OneDrive 或者开始向本地计算机同步文件之前，防止 OneDrive 同步客户端 (OneDrive.exe) 生成网络流量（检查更新等）。） |
| \***OneDrive** | 禁止使用 OneDrive 进行文件存储 |  | **已启用**（除非在本地或外部使用 OneDrive。） |
| **OneDrive** | 默认情况下将文档保存到 OneDrive |  | **已禁用**（除非在本地或外部使用 OneDrive。） |
| **RSS 源** | 阻止自动发现源和网页快讯 |  | **Enabled** |
| \***RSS 源** | 关闭源和网页快讯的后台同步 |  | **已启用**（如果启用此策略设置，则会禁止在后台同步源和网页快讯。） |
| \***搜索** | 允许使用 Cortana |  | **已禁用**（关闭 Cortana 时，用户仍可以使用搜索功能在设备上查找信息。） |
| **搜索** | 允许在锁屏界面上方使用 Cortana |  | **已禁用** |
| \***搜索** | 允许搜索和 Cortana 使用位置 |  | **已禁用** |
| **搜索** | 不允许 Web 搜索 |  | **Enabled** |
| \***搜索** | 请勿搜索 Web 或在“搜索”中显示 Web 结果 |  | **已启用**（如果启用此策略设置，则不会在 Web 上执行查询，并且当用户在搜索中执行查询时不会显示 Web 结果。） |
| **搜索** | 阻止从控制面板中将 UNC 位置添加到索引 |  | **Enabled** |
| **搜索** | 阻止对脱机文件缓存中的文件编制索引 |  | **Enabled** |
| \***搜索** | 设置在“搜索”中共享的信息 | 匿名信息 | **已启用**（共享使用情况信息，但不共享搜索历史记录、Microsoft 帐户信息或特定的位置。） |
| \***软件保护平台** | 关闭 KMS 客户端联机 AVC 验证 |  | **已启用**（启用此设置可防止此计算机将其激活状态相关的数据发送到 Microsoft。） |
| \***语音** | 允许自动更新语音数据 |  | **已禁用**（不会定期检查更新的语音模型） |
| \***Store** | 关闭更新的自动下载和安装 |  | **已启用**（如果启用此设置，则会关闭应用更新的自动下载和安装。） |
| \***Store** | 关闭 Win8 设备上的更新自动下载 |  | **已启用**（如果启用此设置，则会关闭应用更新的自动下载。） |
| **Store** | 停止向最新版本的 Windows 提供更新 |  | **Enabled** |
| \***同步你的设置** | 不同步 | 允许用户打开同步（未选择） | **已启用**（如果启用此策略设置，则会关闭“同步你的设置”，“同步你的设置”组的任何成员都不会在此设备上同步。） |
| **文本输入** | 改进墨迹书写和键入识别 |  | **已禁用** |
| **Windows Defender 防病毒**\\ MAPS | 加入 Microsoft MAPS |  | **已禁用**（如果禁用或不配置此设置，则你不会加入 Microsoft MAPS。） |
| **Windows Defender 防病毒**\\ MAPS | 需要进行进一步分析时发送文件样本 | 永不发送 | **已启用**（仅适用于未选择接收 MAPS 诊断数据的情况） |
| **Windows Defender 防病毒**\\ 报告 | 关闭增强型通知 |  | **已启用**（如果启用此设置，则不会在客户端上显示 Windows Defender 防病毒增强通知。） |
| **Windows Defender 防病毒**\\ 签名更新 | 定义用于下载定义更新的源的顺序 | FileShares | **已启用**（如果启用此设置，则会按指定的顺序联系定义更新源。 从一个指定的源成功下载定义更新后，将不会联系列表中的剩余源。） |
| **Windows 错误报告** | 自动发送操作系统所生成错误报告的内存转储 |  | **已禁用** |
| **Windows 错误报告** | 禁用 Windows 错误报告 |  | **Enabled** |
| **Windows 游戏录制和广播** | 启用或禁用 Windows 游戏录制和广播 |  | **已禁用** |
| **Windows Installer** | 控制基线文件缓存大小的上限 | 5 | **Enabled** |
| **Windows Installer** | 禁止创建系统还原检查点 |  | **Enabled** |
| **Windows Mail** | 关闭社区功能 |  | **Enabled** |
| **Windows Media Player** | 不显示首次使用对话框 |  | **Enabled** |
| **Windows Media Player** | 阻止媒体共享 |  | **Enabled** |
| **Windows 移动中心** | 关闭 Windows 移动中心 |  | **Enabled** |
| **Windows 可靠性分析** | 配置可靠性 WMI 提供程序 |  | **已禁用** |
| **Windows 更新** | 允许自动更新立即安装 |  | **Enabled** |
| **Windows 更新** | 不要连接任何 Windows 更新 Internet 位置 |  | **已启用**（启用此策略会禁用该功能，并且可能会导致无法连接到 Windows Store 等公共服务。） **注意：** 仅当设备被配置为使用“指定 Intranet Microsoft 更新服务位置”连接到 Intranet 更新服务时才应用此策略。 |
| **Windows 更新** | 删除对所有 Windows 更新功能的访问权限 |  | **Enabled** |
| **\*Windows 更新**\\ 适用于企业的 Windows 更新 | 管理预览版 | 设置接收预览版的行为： | **已启用**（选择“禁用预览版”会阻止在设备上安装预览版。 这可以防止用户通过“设置”-\>“更新和安全性”选择加入 Windows 预览体验计划。） |
|  |  | 禁用预览版 |  |
| **\*Windows 更新**\\ 适用于企业的 Windows 更新 | 选择何时接收预览版和功能更新 | 半年频道 | **已启用**（启用此策略可以指定要接收的预览版或功能更新级别，以及接收时间。） |
|  |  | 延迟：365 天； |  |
|  |  | 暂停开始时间：yyyy-mm-dd |  |
| **Windows 更新**\\ 适用于企业的 Windows 更新 | 选择何时接收质量更新 | 1. 30 天；2. 从 yyyy-mm-dd 开始暂停接收质量更新 | **Enabled** |
| **Windows 受限流量自定义策略设置** | 用户登录到 OneDrive 之前阻止 OneDrive 产生网络流量 |  | **已启用**（若要在用户登录到 OneDrive 或者开始向本地计算机同步文件之前，防止 OneDrive 同步客户端 (OneDrive.exe) 生成网络流量（检查更新等），请启用此设置。） |
| **Windows 受限流量自定义策略设置** | 关闭 Windows Defender 通知 |  | **已启用**（如果启用此策略设置，则 Windows Defender 不会发送包含有关设备运行状况和安全性的关键信息的通知。） |
| **本地计算机策略 \\ 用户配置 \\ 管理模板** |  |  |  |
| **控制面板**\\ 区域和语言选项 | 关闭在我键入时提供文本预测的功能 |  | **Enabled** |
| **桌面** | 不将最近打开的文档的共享添加到网络位置 |  | **Enabled** |
| **桌面** | 关闭 Aero Shake 窗口最小化鼠标手势 |  | **Enabled** |
| **桌面** / Active Directory | Active Directory 搜索的最大大小 | 2500 | **Enabled** |
| **开始菜单和任务栏** | 不允许将 Store 应用固定到任务栏 |  | **Enabled** |
| **开始菜单和任务栏** | 不在跳转列表中显示或跟踪来自远程位置的项目 |  | **Enabled** |
| **开始菜单和任务栏** | 解析 shell 快捷方式时不使用基于搜索的方法 |  | **已启用**（系统不会执行最后一个驱动器搜索。 它只会显示一条消息，指出找不到文件。） |
| **开始菜单和任务栏** | 从任务栏中删除人员栏 |  | **已启用**（将从任务栏中删除人员图标，并从任务栏设置页中删除相应的设置切换开关，用户无法将人员固定到任务栏。） |
| **开始菜单和任务栏** | 关闭功能广告气球通知 |  | **已启用**（用户无法将 Store 应用固定到任务栏。 如果 Store 应用已固定到任务栏，下次登录时会将它从任务栏中删除。） |
| **开始菜单和任务栏** | 关闭用户跟踪 |  | **Enabled** |
| **开始菜单和任务栏** / 通知 | 关闭 toast 通知 |  | **Enabled** |
| **Windows 组件** / 云内容 | 关闭所有的 Windows 聚焦功能 |  | **Enabled** |
| **Edge UI** | 关闭应用使用情况跟踪 |  | **Enabled** |
| **文件资源管理器** | 关闭缩略图的缓存 |  | **Enabled** |
| **文件资源管理器** | 禁止在文件资源管理器搜索框中显示最近的搜索条目 |  | **Enabled** |
| **文件资源管理器** | 关闭隐藏的 thumbs.db 文件中的缩略图缓存 |  | **Enabled** ||

### <a name="notes-about-network-connectivity-status-indicator"></a>有关网络连接状态指示器的说明

上述组策略设置包括用于关闭检查系统是否已连接到 Internet 的设置。 如果你的环境根本不用连接或者只是间接连接到 Internet，则你可以设置一个组策略设置用于从任务栏中删除“网络”图标。 从任务栏中删除“网络”图标的原因是，如果关闭 Internet 连接检查，即使网络正常，“网络”图标也会附带一个黄色的标志。 若要通过组策略设置删除网络图标，可在以下位置找到相关说明：

| Windows 更新或适用于企业的 Windows 更新 | 选择何时接收质量更新 | 1. 30 天；2. 从 yyyy-mm-dd 开始暂停接收质量更新 | 启用 |
|--|--|--|--|
| **本地计算机策略 \\ 用户配置 \\ 管理模板** |  |  |  |
| **开始菜单和任务栏** | 删除网络图标 |  | **已启用**（网络图标不会显示系统通知区域。） |

有关网络连接状态指示器 (NCSI) 的详细信息，请参阅：[网络连接状态图标](https://techcommunity.microsoft.com/t5/networking-blog/bg-p/NetworkingBlog)

### <a name="system-services"></a>系统服务

如果你正在考虑禁用系统服务以节省资源，请格外注意，考虑禁用的服务不能是其他某个服务的组件。

此外，其中的大多数建议与针对带有桌面体验的 Windows Server 2016 提供的建议相同；有关详细信息，请参阅[有关在带有桌面体验的 Windows Server 2016 中禁用系统服务的指导](../../security/windows-services/security-guidelines-for-disabling-system-services-in-windows-server.md)。

请注意，有很多看似适合禁用的任务已设置为手动服务启动类型。 这意味着，这些服务不会自动启动，除非特定的应用程序或服务对你考虑禁用的服务触发了请求，否则这些服务不会启动。 已设置为手动启动类型的服务通常不会在此处列出。

| Windows 服务 | 项 | 备注 |
|--|--|--|
| CDPUserService | 此用户服务用于互联设备平台方案 | 注意：这是一个基于用户的服务，因此，必须禁用模板服务。 |
| 已连接的用户体验和遥测 | 启用支持应用程序内部和已连接的用户体验的功能。 此外，如果在“反馈和诊断”中启用了诊断和使用情况隐私选项设置，则此服务会管理诊断和使用情况信息的事件驱动式收集与传输（用于改进 Windows 平台的体验和质量）。 | 在断开连接的网络中考虑禁用 |
| 联系人数据 | 为联系人数据编制索引以加速联系人搜索。 如果停止或禁用此服务，搜索结果中可能会缺少联系人。 | (PimIndexMaintenanceSvc) 注意：这是一个基于用户的服务，因此，必须禁用模板服务。 |
| 诊断策略服务 | 启用 Windows 组件的问题检测、故障排除和解决。 如果此服务已停止，则诊断将不再正常运行。 |  |
| 已下载的地图管理器 | 可让应用程序访问已下载的地图的 Windows 服务。 应用程序在访问下载的地图时会按需启动此服务。 禁用此服务可防止应用访问地图。 |  |
| 地理定位服务 | 监视系统的当前位置并管理地理围栏 |  |
| GameDVR 和广播用户服务 | 此用户服务用于游戏录制和实时广播 | 注意：这是一个基于用户的服务，因此，必须禁用模板服务。 |
| MessagingService | 支持短信和相关功能的服务。 | 注意：这是一个基于用户的服务，因此，必须禁用模板服务。 |
| 优化驱动器 | 通过优化存储驱动器上的文件，帮助计算机更有效地运行。 | 一般情况下，VDI 解决方案无法受益于磁盘优化。 这些“驱动器”并非传统的驱动器，通常只是一种临时存储分配。 |
| Superfetch | 维持和不断改进系统性能。 | 一般不会改进 VDI 的性能，尤其是非持久性 VDI（考虑到每次重新启动都会丢弃操作系统状态）。 |
| 触摸键盘和手写面板服务 | 启用触摸键盘、手写面板笔和墨迹功能 |  |
| Windows 错误报告 | 允许在程序停止运行或无响应时报告错误，并允许传送现有的解决方案。 此外，允许生成诊断和修复服务的日志。 如果此服务已停止，错误报告可能无法正常工作，并且诊断服务和修复结果可能不会显示。 | 使用 VDI 时，诊断通常是在脱机情况下执行的，而不是在主流生产环境中执行的。 此外，某些客户仍会禁用 WER。 在许多情况下（包括无法安装设备或无法安装更新时），WER 会占用微量的资源。 |
| Windows Media Player 网络共享服务 | 使用通用即插即用向其他联网的播放器和媒体设备共享 Windows Media Player 库 | 除非客户在网络上共享 WMP 库，否则不需要启用。 |
| Windows 移动热点服务 | 提供与另一台设备共享手机网络数据连接的功能。 |  |
| Windows 搜索 | 提供文件、电子邮件和其他内容的内容索引、属性缓存和搜索结果。 | 可能不需要启用，尤其是使用非持久性 VDI 时 |

#### <a name="per-user-services-in-windows"></a>Windows 中的基于用户的服务

[基于用户的服务](/windows/application-management/per-user-services-in-windows)是当用户登录到 Windows 或 Windows Server 时创建的，当用户注销时停止并删除的服务。这些服务在用户帐户的安全上下文中运行 - 相比于以往在与预配置帐户关联的资源管理器中或者以任务形式运行此类服务相比，这可以改善资源管理。

### <a name="scheduled-tasks"></a>计划任务

与 Windows 中的其他项一样，在考虑禁用某个项之前需确保不再需要该项。

下面列出的任务在每次重新启动后都会保留状态的计算机上执行优化或数据收集。 如果 VDI VM 任务在重新启动时会丢弃自上次启动以来所做的所有更改，则针对物理计算机的优化没有作用。

可以使用以下 PowerShell 代码获取所有当前计划的任务（包括说明）：

`Get-ScheduledTask | Select-Object -Property TaskPath,TaskName,State,Description |Export-CSV -Path C:\Temp\W10_1803_SchTasks.csv -NoTypeInformation`

有效的“计划任务名称”值包括：

- OneDrive 独立更新任务 v2
- Microsoft 兼容性评估程序
- ProgramDataUpdater
- StartupAppTask
- CleanupTemporaryState
- Proxy (代理)
- UninstallDeviceTask
- ProactiveScan
- Consolidator
- UsbCeip
- 数据完整性扫描
- 用于故障修复的数据完整性扫描
- ScheduledDefrag
- SilentCleanup
- Microsoft-Windows-DiskDiagnosticDataCollector
- 诊断
- StorageSense
- DmClient
- DmClientOnScenarioDownload
- 文件历史记录（维护模式）
- ScanForUpdates
- ScanForUpdatesAsUser
- SmartRetry
- 通知
- WindowsActionDialog
- WinSAT Cellular
- MapsToastTask
- ProcessMemoryDiagnosticEvents
- RunFullMemoryDiagnostic
- MNO 元数据分析程序
- LPRemove
- GatherNetworkInfo
- WiFiTask
- Sqm-Tasks
- AnalyzeSystem
- MobilityManager
- VerifyWinRE
- RegIdleBackup
- FamilySafetyMonitor
- FamilySafetyRefreshTask
- IndexerAutomaticMaintenance
- SpaceAgentTask
- SpaceManagerTask
- HeadsetButtonPress
- SpeechModelDownloadTask
- ResPriStaticDbSync
- WsSwapAssessmentTask
- SR
- SynchronizeTimeZone
- Usb-Notifications
- QueueReporting
- UpdateLibrary
- 计划的启动
- sih
- XblGameSaveTask

### <a name="apply-windows-and-other-updates"></a>应用 Windows 更新和其他更新

从 Microsoft 更新或内部资源应用可用的更新，包括 Windows Defender 签名。 此时非常适合应用其他可用的更新，包括适用于 Microsoft Office（如果已安装）的更新。

### <a name="automatic-windows-traces"></a>自动 Windows 跟踪

Windows 默认配置为收集并保存有限的诊断数据。 目的是启用诊断，或者在需要进一步执行故障排除时记录数据。 可以通过启动“计算机管理”应用，展开“系统工具”、“性能”、“数据收集器集”，然后选择“事件跟踪会话”，来找到自动系统跟踪。

“事件跟踪会话”和“启动事件跟踪会话”下显示的某些跟踪无法停止，也不应将其停止。 其他跟踪（例如 **WiFiSession**）可以停止。 若要停止“事件跟踪会话”下的某个正在运行的跟踪，请右键单击该跟踪，然后选择“停止”。 若要防止启动时自动启动该跟踪，请执行以下步骤：

1.  选择“启动事件跟踪会话”文件夹

2.  找到所需的跟踪，然后双击该跟踪。

3.  选择“跟踪会话”选项卡。

4.  清除标有“已启用”的框。

5.  选择“确定”  。

下面是使用 VDI 时可考虑禁用的一些系统跟踪：

| 名称 | 备注 |
|--|--|
| AppModel | 跟踪的集合，其中一个跟踪是 phone |
| CloudExperienceHostOOBE |  |
| DiagLog |  |
| NtfsLog |  |
| TileStore |  |
| UBPM |  |
| WiFiDriverIHVSession | 如果不使用 WiFi 设备 |
| WiFiSession |  |

#### <a name="servicing-the-operating-system-and-apps"></a>为操作系统和应用提供服务

应在在映像优化过程中的某个时间点应用可用的 Windows 更新。 可将 Windows 更新设置为安装其他 Microsoft 产品以及 Windows 的更新。 若要进行此设置，请打开“Windows 设置”，然后依次选择“更新和安全性”、“高级选项”。 选择“更新 Windows 时提供其他 Microsoft 产品的更新”并将其设置为“打开”。

如果你要在基本映像中安装 Microsoft Office 等 Microsoft 应用程序，则最好是使用此设置。 这样，在将映像投放到服务后，Office 就可以保持最新状态。 还可以下载 .NET 更新；某些非 Microsoft 组件（例如 Adobe）也会通过 Windows 更新提供更新。

对于非持久性 VDI VM，一个非常重要的考虑因素是安全更新，包括安全软件定义文件。 这些更新可能会每天发布一次，甚至更频繁地发布。 可通过某种方式保留这些更新，包括 Windows Defender 和非 Microsoft 组件。

对于 Windows Defender，可能最好是安装更新，即使是在非持久性 VDI 上。 几乎每次建立登录会话都会应用更新，但这些更新的规模较小，应该不会造成问题。 此外，VM 在更新时不会减慢速度，因为只会应用最新可用的更新。 更新非 Microsoft 定义文件时可能也是如此。

> [!NOTE]
> 通过 Windows Store 更新 Store 应用（UWP 应用）。 新版 Office（例如 Microsoft 365）在已直接连接到 Internet 的情况下可通过自身的机制更新，在未连接到 Internet 的情况下可通过管理技术更新。

### <a name="windows-defender-optimization-with-vdi"></a>使用 VDI 进行 Windows Defender 优化

Microsoft 最近发布了有关 VDI 环境中的 Windows Defender 的文档。 有关详细信息，请参阅[在虚拟桌面基础结构 (VDI) 环境中的 Windows Defender 防病毒部署指南](/windows/security/threat-protection/windows-defender-antivirus/deployment-vdi-windows-defender-antivirus)。

上述文章提供了为黄金 VDI 映像提供服务，以及如何维护正在运行的 VDI 客户端的过程。 当 VDI 计算机需要更新其 Windows Defender 签名时，为减少网络带宽，请分阶段重新启动，并尽量将重新启动安排在下班时间。 Windows Defender 签名更新可以包含在文件共享的内部，如果可行，请将这些文件共享放在 VDI 虚拟机所在的相同网段或者与之靠近的网段。

有关使用 VDI 优化 Windows Defender 的更多信息，请参阅本部分开头所列的文章。

### <a name="tuning-windows-10-network-performance-by-using-registry-settings"></a>使用注册表设置优化 Windows 10 网络性能

如果环境中 VDI 或物理计算机的工作负荷主要依赖于网络，则此措施尤为重要。 本部分中的设置更注重性能而不是网络，描述如何为目录条目等项目设置额外的缓冲和缓存。

请注意，本部分中的某些设置仅基于注册表，应该先将其整合到基本映像，然后再将映像部署到生产用途。

Windows 产品小组在 Microsoft.com 上发布的 [Windows Server 2016 性能优化准则](/windows-server/administration/performance-tuning/)中阐述了以下设置。

#### <a name="disablebandwidththrottling"></a>DisableBandwidthThrottling

HKLM\\System\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters\\DisableBandwidthThrottling

适用于 Windows 10。 默认值为 **0**。 默认情况下，SMB 重定向程序会限制高延迟网络连接的吞吐量，在某些情况下可以避免与网络相关的超时。 将此注册表值设置为 **1** 可禁用此限制，从而在高延迟网络连接上实现更高的文件传输吞吐量，因此请考虑此设置。

#### <a name="fileinfocacheentriesmax"></a>FileInfoCacheEntriesMax

HKLM\\System\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters\\FileInfoCacheEntriesMax

适用于 Windows 10。 默认值为 **64**，有效范围为 1 - 65536。 此值用于确定可以由客户端缓存的文件元数据量。 在访问大量文件时，增加该值可以减少网络流量并提高性能。 请尝试将此值增大至 **1024**。

#### <a name="directorycacheentriesmax"></a>DirectoryCacheEntriesMax

HKLM\\System\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters\\DirectoryCacheEntriesMax

适用于 Windows 10。 默认值为 **16**，有效范围为 1 - 4096。 此值用于确定可以由客户端缓存的目录信息量。 在访问大量目录时，增加该值可以减少网络流量并提高性能。 请考虑将此值增大至 **1024**。

#### <a name="filenotfoundcacheentriesmax"></a>FileNotFoundCacheEntriesMax

HKLM\\System\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters\\FileNotFoundCacheEntriesMax

适用于 Windows 10。 默认值为 **128**，有效范围为 1 - 65536。 此值用于确定可由客户端缓存的文件名信息量。 在访问大量文件名时，增加该值可以减少网络流量并提高性能。 请考虑将此值增大至 **2048**。

#### <a name="dormantfilelimit"></a>DormantFileLimit

HKLM\\System\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters\\DormantFileLimit

适用于 Windows 10。 默认值为 **1023**。 此参数指定应用程序关闭文件后应在共享资源上保持打开状态的文件的数量上限。 如果有数千个客户端连接到 SMB 服务器，请考虑将此值减小至 **256**。

可以使用 [Set-SmbClientConfiguration](/powershell/module/smbshare/set-smbclientconfiguration) 和 [Set-SmbServerConfiguration](/powershell/module/smbshare/set-smbserverconfiguration) Windows PowerShell cmdlet 配置其中的许多 SMB 设置。 也可以使用 Windows PowerShell 配置仅限注册表的设置，如以下示例所示：

`Set-ItemProperty -Path "HKLM:\\SYSTEM\\CurrentControlSet\\Services\\LanmanWorkstation\\Parameters" RequireSecuritySignature -Value 0 -Force`

### <a name="additional-settings-from-the-windows-restricted-traffic-limited-functionality-baseline-guidance"></a>Windows 受限流量限制功能基线指南中所述的其他设置

对于未直接连接到 Internet，或者想要减少发送到 Microsoft 和其他服务的数据的环境，Microsoft 发布了使用 [Windows 安全基准](/windows/device-security/windows-security-baselines)所用的相同过程创建的基线。

[Windows 受限流量限制功能基线](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services)设置在“组策略”表中标有星号。

### <a name="disk-cleanup-including-using-the-disk-cleanup-wizard"></a>磁盘清理（包括使用磁盘清理向导）

对于主映像 VDI 实现，磁盘清理可能特别有用。 准备、更新并配置主映像后，最后要执行的任务之一就是磁盘清理。 Windows 中内置的磁盘清理向导可帮助清理磁盘空间，最大程度地实现节省。

> [!NOTE]
> 我们不再开发磁盘清理向导。 Windows 将使用其他方法来提供磁盘清理功能。



下面是针对各种磁盘清理任务的建议。 在实施其中的任何建议之前，应该进行测试：

1. 应用所有更新后运行磁盘清理向导（以提升的权限）。 包括类别“传递优化”和“Windows 更新清理”。 可以结合 **/SAGESET:11** 选项使用 **Cleanmgr.exe** 将此过程自动化。 此选项会设置注册表值，稍后可以使用磁盘清理向导中的每个可用选项来自动完成磁盘清理。

   1.  在干净安装的测试 VM 上，运行 **Cleanmgr.exe /SAGESET:11** 只会显示默认启用的两个自动磁盘清理选项：

   - 下载的程序文件

   - Internet 临时文件

   2. 如果设置更多选项或所有选项，这些选项会根据前一命令 (**Cleanmgr.exe /SAGESET:11**) 中提供的索引值记录到注册表中。 在此示例中，我们使用了值 *11* 作为索引来完成后续的自动磁盘清理过程。

   3. 运行 **Cleanmgr.exe /SAGESET:11** 之后，会看到许多磁盘清理选项类别。 可以选择每个选项，然后选择“确定”。 你会发现，磁盘清理向导已消失。 但是，所选的设置已保存在注册表中，可以通过运行 **Cleanmgr.exe /SAGERUN:11** 来调用它们。

2. 清理卷影复制存储（如果已使用）。 为此，请在提升权限的提示符下运行以下命令：

   - **vssadmin list shadows**

   - **vssadmin list shadowstorage**

       如果这些命令的输出为 *No items found that satisfy the query.* ，则表示未使用 VSS 存储。

3. 清理临时文件和日志。 在权限提升的命令提示符下运行以下命令：

   - **Del C:\\\*.tmp /s**

   - **Del C:\\Windows\\Temp\\.**

   - **Del %temp%\\.**

4. 使用以下命令删除系统上未使用的所有配置文件：

   **wmic path win32_UserProfile where LocalPath="c:\\\\users\\\\\<user\>" Delete**

### <a name="remove-onedrive"></a>删除 OneDrive

删除 OneDrive 涉及到删除包、卸载并删除 \*.lnk 文件。 可以使用以下示例 PowerShell 代码帮助从映像中删除 OneDrive：

```azurecli

Taskkill.exe /F /IM "OneDrive.exe"
Taskkill.exe /F /IM "Explorer.exe"`
    if (Test-Path "C:\\Windows\\System32\\OneDriveSetup.exe")`
     { Start-Process "C:\\Windows\\System32\\OneDriveSetup.exe"`
         -ArgumentList "/uninstall"`
         -Wait }
    if (Test-Path "C:\\Windows\\SysWOW64\\OneDriveSetup.exe")`
     { Start-Process "C:\\Windows\\SysWOW64\\OneDriveSetup.exe"`
         -ArgumentList "/uninstall"`
         -Wait }
Remove-Item -Path
"C:\\Windows\\ServiceProfiles\\LocalService\\AppData\\Roaming\\Microsoft\\Windows\\Start Menu\\Programs\\OneDrive.lnk" -Force
Remove-Item -Path "C:\\Windows\\ServiceProfiles\\NetworkService\\AppData\\Roaming\\Microsoft\\Windows\\Start Menu\\Programs\\OneDrive.lnk" -Force \# Remove the automatic start item for OneDrive from the default user profile registry hive
Start-Process C:\\Windows\\System32\\Reg.exe -ArgumentList "Load HKLM\\Temp C:\\Users\\Default\\NTUSER.DAT" -Wait
Start-Process C:\\Windows\\System32\\Reg.exe -ArgumentList "Delete HKLM\\Temp\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run /v OneDriveSetup /f" -Wait
Start-Process C:\\Windows\\System32\\Reg.exe -ArgumentList "Unload HKLM\\Temp" -Wait Start-Process -FilePath C:\\Windows\\Explorer.exe -Wait
```

如果对本文中的信息有任何疑问，请联系 Microsoft 客户团队、查看 Microsoft VDI 博客、在 Microsoft 论坛中发布消息，或联系 Microsoft。