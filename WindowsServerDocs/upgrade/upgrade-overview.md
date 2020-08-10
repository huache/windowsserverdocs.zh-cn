---
title: Windows Server 升级概述 | Microsoft Docs
description: 常规 Windows Server 升级信息，以及在实际执行升级之前应考虑的事项。
ms.topic: upgrade
author: RobHindman
ms.author: robhind
ms.date: 09/10/2019
ms.openlocfilehash: 1aa923287c26aa75916a418b6550e2dec6bbb6cd
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939247"
---
# <a name="overview-of-windows-server-upgrades"></a>Windows Server 升级概述

升级到更高版本 Windows Server 的过程可能会有很大的不同，具体视你从哪个操作系统入手和选择的路径而定。 我们使用以下术语来区分不同的操作，其中任何一个都可能涉及到新的 Windows Server 部署。

- **升级。** 也称为“就地升级”。 从操作系统的较旧版本移动到较新版本，同时仍在相同的物理硬件上。 本部分将介绍这种方法。

    > [!Important]
    > 公有或私有云公司也可能支持就地升级；但是，必须咨询云提供商以了解详细信息。 此外，无法在任何配置为“从 VHD 启动”的 Windows Server 上执行就地升级。 不支持从 Windows Storage Server 版本就地升级到 Windows Server 2019。 可以改为执行迁移或安装。

- **安装。** 也称为“全新安装”。 从操作系统的较旧版本移动到较新版本，同时删除较旧的操作系统。

- **迁移。** 通过迁移到另一组硬件或虚拟机，从旧版操作系统迁移到新版操作系统。

- **群集操作系统滚动升级。** 升级群集节点的操作系统，且无需停止 Hyper-V 或横向扩展文件服务器工作负载。 利用此功能可以避免出现可能影响服务级别协议的故障时间。 有关详细信息，请参阅[群集操作系统滚动升级](../failover-clustering/cluster-operating-system-rolling-upgrade.md)

- **许可证转换。** 使用简单的命令和相应的许可证密钥，通过一个步骤将发行版的特定版本转换成同一发行版的另一个版本。 我们称之为“许可证转换”。 例如，如果服务器正在运行 Windows Server 2016 Standard，可以将其转换为 Windows Server 2016 Datacenter。

## <a name="which-version-of-windows-server-should-i-upgrade-to"></a>应升级到 Windows Server 的哪个版本？

建议升级到 Windows Server 的最新版本：Windows Server 2019。 通过运行最新版本的 Windows Server，可使用最新功能（包括最新的安全功能）并提供最佳性能。

但是，我们意识到并非总是能达到此效果。 可以使用下图根据当前使用的版本，来确定可以升级到哪个 Windows Server 版本：

![可用的就地升级路径](media/upgrade-paths.png)

通常，Windows Server 可以通过至少一个（有时甚至是两个）版本进行升级。 例如，可以将 Windows Server 2012 R2 和 Windows Server 2016 就地升级到 Windows Server 2019。

还可以从操作系统的评估版本升级到零售版本，从旧的零售版本升级到较新版本，或者在某些情况下，从操作系统的批量许可版本升级到普通零售版本。 有关就地升级以外的升级选项的详细信息，请参阅 [Windows Server 的升级和转换选项](../get-started/supported-upgrade-paths.md)。
