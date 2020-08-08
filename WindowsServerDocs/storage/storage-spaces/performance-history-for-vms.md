---
title: 虚拟机的性能历史记录
ms.author: cosdar
manager: eldenc
ms.topic: article
author: cosmosdarwin
ms.date: 09/07/2018
ms.localizationpriority: medium
ms.openlocfilehash: dcf866d1de675f914d469783b1194e55adf63cb8
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87968724"
---
# <a name="performance-history-for-virtual-machines"></a>虚拟机的性能历史记录

> 适用于：Windows Server 2019

本主题中的[存储空间直通性能历史记录](performance-history.md)详细说明了为虚拟机 (VM) 收集的性能历史记录。 性能历史记录适用于每个正在运行的群集 VM。

   > [!NOTE]
   > 收集可能需要几分钟时间才能开始新创建或重命名的虚拟机。

## <a name="series-names-and-units"></a>序列名称和单位

为每个符合条件的 VM 收集这些系列：

| 系列                            | 计价单位             |
|-----------------------------------|------------------|
| `vm.cpu.usage`                    | %          |
| `vm.memory.assigned`              | 字节            |
| `vm.memory.available`             | 字节            |
| `vm.memory.maximum`               | 字节            |
| `vm.memory.minimum`               | 字节            |
| `vm.memory.pressure`              | -                |
| `vm.memory.startup`               | 字节            |
| `vm.memory.total`                 | 字节            |
| `vmnetworkadapter.bandwidth.inbound`  | 每秒位数 |
| `vmnetworkadapter.bandwidth.outbound` | 每秒位数 |
| `vmnetworkadapter.bandwidth.total`    | 每秒位数 |

此外， `vhd.iops.total` 为附加到 VM 的每个 vhd 聚合所有虚拟硬盘 (vhd) 系列（例如）。

## <a name="how-to-interpret"></a>如何解释


| 系列                            | 描述                                                                                                  |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------|
| `vm.cpu.usage`                    | 虚拟机使用的主机服务器处理器 () 的百分比。                                   |
| `vm.memory.assigned`              | 分配给虚拟机的内存量。                                                      |
| `vm.memory.available`             | 保持可用的内存量（指定的量）。                                       |
| `vm.memory.maximum`               | 如果使用动态内存，则这是可以分配给虚拟机的最大内存量。 |
| `vm.memory.minimum`               | 如果使用动态内存，则这是可以分配给虚拟机的最小内存量。 |
| `vm.memory.pressure`              | 虚拟机所需的内存比分配给虚拟机的内存的比率。            |
| `vm.memory.startup`               | 启动虚拟机所需的内存量。                                            |
| `vm.memory.total`                 | 内存总量。 |
| `vmnetworkadapter.bandwidth.inbound`  | 虚拟机在其所有虚拟网络适配器上接收的数据的速率。                        |
| `vmnetworkadapter.bandwidth.outbound` | 虚拟机在其所有虚拟网络适配器上发送的数据的速率。                            |
| `vmnetworkadapter.bandwidth.total`    | 虚拟机在其所有虚拟网络适配器上接收或发送的数据的总速率。          |

   > [!NOTE]
   > 计数器在整个间隔内进行测量，而不是采样。 例如，如果 VM 闲置了9秒，但高峰在第10秒钟内使用的主机 CPU 50%，则在 `vm.cpu.usage` 此10秒的时间间隔内，其平均记录为5%。 这可确保其性能历史记录捕获所有活动，并使干扰稳定。

## <a name="usage-in-powershell"></a>PowerShell 中的用法

使用[GET VM](/powershell/module/hyper-v/get-vm) cmdlet：

```PowerShell
Get-VM <Name> | Get-ClusterPerf
```

   > [!NOTE]
   > Get VM cmdlet 仅返回本地 (上的虚拟机或指定) 服务器上的虚拟机，而不是在群集上。

## <a name="additional-references"></a>其他参考

- [存储空间直通的性能历史记录](performance-history.md)
