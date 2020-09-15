---
title: Windows Server 版本 1803 中的新增功能
description: 计算、标识、管理、自动化、网络、安全性、存储方面的新增功能。
ms.topic: article
author: greg-lindsay
ms.author: greglin
ms.localizationpriority: high
ms.date: 05/07/2018
ms.openlocfilehash: e372ba924eeefc552dc7f65310a77749d8707971
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078594"
---
# <a name="whats-new-in-windows-server-version-1803"></a>Windows Server 版本 1803 中的新增功能

> 适用于：Windows Server（半年频道）

<img src=../media/landing-icons/new.png style='float:left; padding:.5em;' alt=Icon showing a newspaper>&nbsp;若要了解 Windows 中的最新功能，请参阅 [Windows Server 中的新增功能](whats-new-in-windows-server.md)。 本部分的内容介绍 Windows Server 版本 1803 中的新增功能和更改的功能。 此处列出的新功能和更改在你使用此版本时最可能具有最大影响力。 另请参阅 [Windows Server Semi-Annual Channel update](https://cloudblogs.microsoft.com/windowsserver/2018/03/29/windows-server-semi-annual-channel-update/)（Windows Server 半年频道更新）。

## <a name="windows-admin-center"></a>Windows Admin Center

Project Honolulu 现称为 **Windows Admin Center**。
<br>&nbsp;
> [!video https://www.youtube.com/embed/WCWxAp27ERk?autoplay=false]

[Windows Admin Center](../manage/windows-admin-center/overview.md) 整合了有关本地和远程服务器管理的各个方面。 Windows Admin Center 是本地部署的基于浏览器的管理体验，不需要 Internet 连接，可让你全面控制 Windows Server 部署的各个方面。

## <a name="windows-server-release-strategy"></a>Windows Server 发布策略

Windows Server 版本 1709 作为半年频道中的第一版于 2017 年 9 月发布。 半年频道的发布频率较高，每隔几个月就会处理一次那些希望快速创新的用户的反馈。 这是对发布频率为 2-3 年一次的长期服务频道的补充。

根据遥测和反馈，这些频道已表现出它们非常符合下述常规策略：
- 半年频道非常适用于现代应用程序和创新方案，如容器和微服务。
- 长期服务频道是软件定义数据中心和超融合基础设施 (HCI) 等核心基础设施方案的首选版本。

半年频道和长期服务频道的具体方案如下：

| 说明 | 长期服务频道 | 半年频道 |
|--|--|--|
| 建议方案 | 常规用途文件服务器、第一和第三方工作负荷、传统应用、基础设施角色、软件定义数据中心和超融合基础设施 | 容器化应用程序、容器主机和受益于更快创新的应用程序方案 |
| 最新发布 | 每 2 - 3 年 | 每 6 个月 |
| 支持 | 5 年的主要支持 + 5 年的外延支持 | 18 个月 |
| 版本 | 所有可用的 Windows Server 版本 | 标准版和数据中心版 |
| 谁可以使用 | 所有频道的所有客户 | 仅软件保障客户和云客户 |
| 安装选项 | Server Core 和带桌面体验的 Server | 容器主机的 Server Core、容器映像和 Nano Server 容器映像 |

## <a name="application-platform-and-containers"></a>应用程序平台和容器

- 优化
    - 从 Windows Server 版本 1709 开始，Server Core 基本容器映像减少了 30%。
    - 应用程序兼容性也有所提升，这有助于实现传统应用程序的容器化。
    - 借助各种修复和优化，容器启动性能和运行时性能也有所提升。
- 容器网络：添加了 Localhost 和 http 代理支持，并改进了容器的可伸缩性和启动时间。
- 工具：增强了针对 Curl.exe、Tar.exe 和 SSH 的支持，以完善用于构建和调试方案的 PowerShell。

### <a name="server-core-container-image"></a>Server Core 容器映像

应用程序兼容性更好的较小 Server Core 容器现已推出。 详细信息请在[此处](https://techcommunity.microsoft.com/t5/virtualization/bg-p/Virtualization)获取。

- 已删除未使用的可选功能和角色。 有关详细信息，请参阅 [Server Core 容器不存在的角色、角色服务和功能](../administration/server-core/server-core-container-removed-roles.md)。
    - 下载文件大小降低到 1.58 GB，比 Windows Server 版本 1709 降低了 30%。
    - 占用磁盘容量降低到 3.61 GB，比 Windows Server 版本 1709 降低了 20%。
- Nano Server 容器映像小于 100 MB

### <a name="windows-subsystem-for-linux-wsl"></a>适用于 Linux 的 Windows 子系统 (WSL)

WSL 使服务器管理员可以使用 Windows Server 上的 Linux 中的现有工具和脚本。 [命令行博客](https://devblogs.microsoft.com/commandline/tag/wsl/)中展示的许多改进现在都是 Windows Server 的一部分，包括后台任务、DriveFS、WSLPath 和更多其他内容。

### <a name="kubernetes"></a>Kubernetes

Kubernetes（通常称作 K8s）是用于自动部署、缩放和管理在 [Cloud Native Computing Foundation](https://www.cncf.io) 管理下开发的容器化应用程序的开源系统。

使用 Windows Server 版本 1709，用户就能利用 Windows 上的 Kubernetes 网络功能，其中包括：
- 共享 Pod 分区：基础架构和工作线程 Pod 现在共享一个网络分区（类似于 Linux 命名空间）。
- 终结点优化：由于分区共享，容器服务需要跟踪至少半数的终结点。
- 数据路径优化：虚拟筛选平台和主机网络服务的改进实现了基于内核的负载均衡。

伴随着 Windows Server 版本 1803 的发布，更多功能会出现在即将发布的 Kubernetes 里：
- 针对 Kubernetes 协调的 Windows 容器的[存储插件](https://github.com/Microsoft/K8s-Storage-Plugins)。
- 通过各种计划（例如我们与 [Tigera on Project Calico](https://cloudblogs.microsoft.com/windowsserver/2017/12/07/securing-modernized-apps-and-simplified-networking-on-windows-with-calico/) 支持的合作）推出的云规模网络功能。
- Windows 平台支持 Hyper-V 隔离的 Pod，允许每个 Pod 使用多个容器。

### <a name="application-compatibility-and-feature-parity-issues-fixed"></a>应用程序兼容性和功能奇偶一致性问题已修复

- Microsoft 消息队列 (MSMQ) 现已安装在 Server Core 容器中。
- 中断 ASP.net 性能计数器的问题已修复。
- 在容器中运行的服务器接收不到关闭通知的问题已修复。
    - 具体而言，基于 Server Core 和 Nano Server 容器的映像的通知被更改为 CTRL_SHUTDOWN_EVENT。 此外，它扩展了基于 Server Core 容器的映像中的通知，使之影响所有在容器中运行的进程，包括向容器中运行的服务发送服务关闭通知。
- docker pull 和 docker load 之间的不兼容性已修复。docker pull 和 docker load 具有决定是否需要 BitLocker 保护使固定数据驱动器变可写的策略设置 (FDVDenyWriteAccess)。

## <a name="storage"></a>存储

借助此版本，可以阻止“文件服务器资源管理器服务”启动时在所有卷上创建变更日志（也称为 USN 日志）。 这可以节省每个卷的空间，但会禁用实时文件分类。 有关详细信息，请参阅[文件服务器资源管理器概述](../storage/fsrm/fsrm-overview.md)。

## <a name="features-added-to-server-core"></a>添加到 Server Core 的功能

Windows 部署服务 (WDS) 角色中的传输服务器角色已添加到 Server Core。

传输服务器只包含 WDS 的核心网络部分。 可以使用传输服务器创建从独立服务器传输数据（包括操作系统映像）的多播命名空间。 如果想要一个 PXE 服务器，以便客户端通过 PXE 启动并下载你自己的自定义安装应用程序，则也可使用它。 如果想要使用这些方案之一，则应使用此选项。

可以使用以下 Windows PowerShell 命令来启用 Server Core 上的传输服务器服务：

```
Install-WindowsFeature -Name WDS
```

## <a name="additional-references"></a>其他参考

[Windows Server 版本信息](./windows-server-release-info.md)<br>
[Windows 10 版本 1803 IT 专业人员内容中的新增功能](/windows/whats-new/whats-new-windows-10-version-1803)
