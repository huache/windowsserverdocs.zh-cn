---
title: 虚拟机大小调整
description: 针对每个工作负荷类型的大小建议。
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: helohr
ms.date: 12/02/2019
ms.tgt_pltfrm: na
ms.topic: article
author: Heidilohr
manager: daveba
ms.openlocfilehash: 964dba2fc1a3cc1cf0e9cfe2392d40b9ea8f5ece
ms.sourcegitcommit: cbf0c7c37797c22af989639fac82fc0eee94497f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700906"
---
# <a name="virtual-machine-sizing-guidance"></a>虚拟机大小调整指南

不管是在远程桌面服务上还是在 Windows 虚拟桌面上运行虚拟机，不同类型的工作负荷需要的会话主机虚拟机 (VM) 配置是不同的。 若要尽可能完善体验，请根据用户需求缩放部署。

## <a name="multi-session-recommendations"></a>多会话建议

下表列出了建议用于每个虚拟中心处理单元 (vCPU) 的最大用户数，以及每个工作负荷的最低 VM 配置。 这些建议基于[远程桌面工作负荷](remote-desktop-workloads.md)。

| 工作负荷类型 | 每个 vCPU 的最大用户数 | vCPU/RAM/OS 存储最小值 | Azure 实例示例 | 配置文件容器存储最小值 |
| --- | --- | --- | --- | --- |
| 轻型 | 6 | 2 vCPU，8 GB RAM，16 GB 存储 | D2s_v3、F2s_v2 | 30 GB |
| 中 | 4 | 4 vCPU，16 GB RAM，32 GB 存储 | D4s_v3、F4s_v2 | 30 GB |
| 重型 | 2 | 4 vCPU，16 GB RAM，32 GB 存储 | D4s_v3、F4s_v2 | 30 GB |
| 电源 | 1 | 6 vCPU，56 GB RAM，340 GB 存储 | D4s_v3、F4s_v2、NV6 | 30 GB |

## <a name="single-session-recommendations"></a>单会话建议

关于单会话方案的 VM 大小调整建议，我们建议每个 VM 至少使用两个物理 CPU 核心（通常使用四个支持超线程的 vCPU）。 如果需要更具体的关于单会话方案的 VM 大小调整建议，请询问特定于工作负荷的软件供应商。 单会话 VM 的 VM 大小调整可能会与物理设备指南一致。

## <a name="general-virtual-machine-recommendations"></a>常规虚拟机建议

如需运行操作系统的 VM 要求，请参阅 [Windows 10 计算机规格和系统要求](https://www.microsoft.com/windows/windows-10-specifications)。

对于需要服务级别协议 (SLA) 的生产工作负荷，建议使用 OS 磁盘中的高级 SSD 存储。 如需更多详细信息，请参阅[虚拟机的 SLA](https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_8/)。

对于经常使用图形密集型程序进行视频渲染、3D 设计和模拟的用户来说，图形处理单元 (GPU) 是一个不错的选择。 若要详细了解图形加速，请参阅[选择图形渲染技术](rds-graphics-virtualization.md)。 Azure 有多个图形加速部署选项和多种可用的 GPU VM 大小。 请在 [GPU 优化虚拟机大小](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-gpu)中了解详细信息。

[B 系列可突增 VM](https://docs.microsoft.com/azure/virtual-machines/windows/b-series-burstable) 适用于并非始终需要最高 CPU 性能的用户。 若要详细了解 VM 类型和大小，请参阅 [Azure 中 Windows 虚拟机的大小](https://docs.microsoft.com/azure/virtual-machines/windows/sizes)，并请查看[我们的虚拟机系列页](https://azure.microsoft.com/pricing/details/virtual-machines/series/)上的定价信息。

## <a name="test-your-workload"></a>测试工作负荷

最后，我们建议你使用模拟工具，通过压力测试和实际使用情况模拟来测试部署。 请确保系统具有足以满足用户需求的响应能力和复原能力，并记得更改负载大小以避免意外情况。
