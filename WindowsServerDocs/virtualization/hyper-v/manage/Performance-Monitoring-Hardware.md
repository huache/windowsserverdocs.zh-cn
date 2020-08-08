---
title: 在 Hyper-v 虚拟机中启用 Intel 性能监视硬件
description: 如何在 Hyper-v 计算机中启用 Intel 的性能监视硬件。 还涉及如何启用性能监视硬件影响实时迁移。
ms.reviewer: ifufondu
author: ifeomaufondu-ms
ms.author: ifufondu
manager: chhuybre
ms.topic: article
ms.date: 09/20/2019
ms.openlocfilehash: 73ab88d6ee5d50ae8b433a064a7cea7c249094a2
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87996746"
---
# <a name="enable-intel-performance-monitoring-hardware-in-a-hyper-v-virtual-machine"></a>在 Hyper-v 虚拟机中启用 Intel 性能监视硬件

Intel 处理器包含称为性能监视硬件 (的功能，如 PMU、PEBS、LBR) 。 性能优化软件（如 Intel VTune 放大器）使用这些功能来分析软件性能。  在 Windows Server 2019 和 Windows 10 版本1809之前，在启用 Hyper-v 时，主机操作系统和 Hyper-v 来宾虚拟机均无法使用性能监视硬件。  从 Windows Server 2019 和 Windows 10 版本1809开始，默认情况下，主机操作系统有权访问性能监视硬件。  Hyper-v 来宾虚拟机默认情况下不具有访问权限，但 Hyper-v 管理员可以选择授予对一个或多个来宾虚拟机的访问权限。  本文档介绍向来宾虚拟机公开性能监视硬件所需的步骤。

## <a name="requirements"></a>要求

若要在虚拟机中启用性能监视硬件，需要：

- 具有性能监视硬件的 Intel 处理器 (例如，PMU、PEBS、LBR) 。  请参阅 Intel 的[此文档]( https://software.intel.com/en-us/vtune-amplifier-cookbook-configuring-a-hyper-v-virtual-machine-for-hardware-based-hotspots-analysis)，以确定系统支持的性能监视硬件。
- Windows Server 2019 或 Windows 10 版本 1809 (10 月2018更新) 或更高版本
- _不带_[嵌套虚拟化](/virtualization/hyper-v-on-windows/user-guide/nested-virtualization)并且也处于停止状态的 hyper-v 虚拟机

若要在虚拟机中启用即将开始的 Intel 处理器跟踪 (IPT) 性能监视硬件，需要：

- 支持 IPT 和 PT2GPA 功能的 Intel 处理器。  请参阅 Intel 的[此文档]( https://software.intel.com/en-us/vtune-amplifier-cookbook-configuring-a-hyper-v-virtual-machine-for-hardware-based-hotspots-analysis)，以确定系统支持的性能监视硬件。
- Windows Server 版本 1903 (SAC) 或 Windows 10 版本 1903 (可以2019更新) 或更高版本
- _不带_[嵌套虚拟化](/virtualization/hyper-v-on-windows/user-guide/nested-virtualization)并且也处于停止状态的 hyper-v 虚拟机

## <a name="enabling-performance-monitoring-components-in-a-virtual-machine"></a>在虚拟机中启用性能监视组件

若要为特定的来宾虚拟机启用不同的性能监视组件，请使用 `Set-VMProcessor` PowerShell cmdlet，同时以管理员身份运行：

``` Powershell
# Enable all components except IPT
Set-VMProcessor MyVMName -Perfmon @("pmu", "lbr", "pebs")
```

``` Powershell
# Enable a specific component
Set-VMProcessor MyVMName -Perfmon @("pmu")
```

``` Powershell
# Enable IPT
Set-VMProcessor MyVMName -Perfmon @("ipt")
```

``` Powershell
# Disable all components
Set-VMProcessor MyVMName -Perfmon @()
```
> [!NOTE]
> 启用性能监视组件时，如果 `"pebs"` 指定了，则 `"pmu"` 还必须指定。
> PEBS 仅支持 PMU 版本 >= 4 的硬件。
> 启用主机的物理处理器不支持的组件将导致虚拟机启动失败。

## <a name="effects-of-enabling-performance-monitoring-hardware-on-saverestore-export-and-live-migration"></a>启用性能监视硬件的影响保存/还原、导出和实时迁移

Microsoft 不建议在具有不同 Intel 硬件的系统之间实时迁移或保存/还原具有性能监视硬件的虚拟机。 性能监视硬件的特定行为通常不是体系结构，并且是在 Intel 硬件系统之间进行更改。  在不同系统之间移动正在运行的虚拟机可能会导致非体系结构计数器的不可预知的行为。