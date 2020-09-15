---
title: 每月 Delta 更新 ISV 支持（无 WSUS）
description: Windows Server Update Service (WSUS) 主题 - 独立软件供应商 (ISV) 如何临时使用每月 Delta 更新而非 WSUS Express 更新交付来减小包大小
ms.topic: get-started article
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2b983b06a9f8bf4c2a6d5c72aef13689a72b3684
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624473"
---
# <a name="monthly-delta-update-isv-support-without-wsus"></a>每月 Delta 更新 ISV 支持（无 WSUS）

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows 10

Windows 10 更新下载可能会很大，因为每个包都包含以前发布的所有修复以确保一致性和简单性。

从版本 7 开始，Windows 已能够通过称为 [Express](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc708456(v=ws.10)#Anchor_2) 的功能减小 Windows 更新下载的大小，虽然使用者设备默认情况下支持该功能，但是 Windows 10 企业版设备需要具有 Windows Server Update Services (WSUS) 才能利用 Express。 如果你有 WSUS 可用，请参阅 [Express 更新交付 ISV 支持](express-update-delivery-ISV-support.md)。 我们建议使用它来启用 Express 更新交付。

如果你当前未安装 WSUS，但在此期间需要较小的更新包大小，则可以使用每月 Delta 更新。 Delta 更新大大减小了包大小，但没有使用 WSUS Express 更新交付时减小得那么多。 我们建议你尽可能部署 WSUS Express 更新以最大限度地减小包大小。 下面是一个图表，其中比较了 Windows 10 版本 1607 的 Delta、“累积”和 Express 下载大小：

![下载大小比较](../../media/express-update-delivery-isv-support/delta-1.png)

## <a name="what-is-monthly-delta-update"></a>什么是每月 Delta 更新？

每月安全更新有两种变体：Delta 和“累积”。

每月 Delta 更新是新推出的临时解决方案，适用于没有 WSUS 可用来帮助减小更新包大小的 ISV。

>[!IMPORTANT]
>**Delta 更新可用于 Windows 10 版本 1607（周年更新）、版本 1703（创意者更新）和版本 1709 (Fall Creators Update) 的服务。** 对于版本 1709 之后的版本，你将需要实现一个支持 [Express 更新交付](express-update-delivery-ISV-support.md)的部署基础结构以继续利用增量更新。

通过使用每月 Delta 更新，各个包将仅包含一个月的更新。 每月累积包含直至该更新版本的所有更新，导致生成每月增大的大型文件。 Delta 更新和每月更新都是在每月的第二个周二发布的，也称为“周二更新”。 下表比较了 Delta 更新和累积更新：

|                    | 每月 **Delta** 更新                                                                                                                                                                                                       | 每月**累积**更新                                                                                                                                                                                             |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Scope**          | **仅包含该月的新修补程序**的单一更新                                                                                                                                                                           | 包含该月和所有以前月份的所有新修补程序的单一更新                                                                                                                                                   |
| **应用程序**    | 只有应用了上个月的更新时才能应用（“累积”或 Delta）                                                                                                                                           | 任何时候都可以应用                                                                                                                                                                                                |
| **交付**       | **仅发布到 Windows 更新目录**，可以从中下载该更新以用于其他工具或流程。 不提供给连接到 Windows 更新的电脑                                                         | 发布到 Windows 更新（所有使用者电脑都将安装它）、WSUS 和 Windows 更新目录                                                                                                                |

Delta 更新和累积更新具有相同的 KB 编号和相同的分类，并且在相同的时间发布。 可以通过目录中的更新标题或 msu 的名称来区分更新：

- 2017-02 基于 x64 的系统的 Windows 10 版本 1607 的 *\***Delta 更新**\**   (KB1234567)
- 2017-02 基于 x86 的系统的 Windows 10 版本 1607 的 *\***累积更新**\**   (KB1234567)

### <a name="when-to-use-monthly-delta-update"></a>何时使用每月 Delta 更新

如果客户端设备的更新大小是一个顾虑，我们建议对具有上个月的更新的设备使用 Delta 更新，对落在后面的设备使用累积更新。 这样，所有设备仅需要单个更新便可保持最新。 这需要在整个更新管理过程中进行少量调整，因为你必须根据组织中各个设备的最新情况部署不同的更新：

![下载大小比较](../../media/express-update-delivery-isv-support/delta-2.png)

### <a name="prevent-deployment-of-delta-and-cumulative-updates-in-the-same-month"></a>防止在同一月份部署 Delta 更新和累积更新

由于 Delta 更新和累积更新同时可用，因此，了解在同一月份同时部署这两个更新会发生什么情况非常重要。

如果你批准并部署相同版本的 Delta 更新和累积更新，则不仅会生成额外的网络流量（因为两者都将下载到电脑），而且在重启后，你可能无法将计算机重新引导到 Windows。

如果意外地同时安装了 Delta 更新和累积更新，并且你的计算机无法引导，则可以通过以下步骤进行恢复：

1. 引导到 WinRE 命令提示符
2. 列出处于挂起状态的包：

    `x:\windows\system32\dism.exe /image:<drive letter for windows directory> /Get-Packages >> <path to text file>`

    > **示例**：` x:\windows\system32\dism.exe /image:c:\ /Get-Packages >> c:\temp\packages.txt`

3. 打开你通过管道将 **get-packages** 的返回结果传送到的文本文件。 如果发现存在任何尚未安装的修补程序，请针对每个包名称运行 **remove-package**：

   `dism.exe /image:<drive letter for windows directory> /remove-package /packagename:<package name>`

    > **示例**：`x:\windows\system32\dism.exe /image:c:\ /remove-package /packagename:Package_for_KB4014329~31bf3856ad364e35~amd64~~10.0.1.0`

    >[!NOTE]
    >不要删除卸载挂起修补程序。

>[!IMPORTANT]
>**Delta 更新可用于 Windows 10 版本 1607（周年更新）、版本 1703（创意者更新）和版本 1709 (Fall Creators Update) 的服务。** 对于版本 1709 之后的版本，你将需要实现一个支持 [Express 更新交付](express-update-delivery-ISV-support.md)的部署基础结构以继续利用增量更新。