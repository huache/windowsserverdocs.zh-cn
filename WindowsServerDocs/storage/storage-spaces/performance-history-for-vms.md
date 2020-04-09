---
title: 虚拟机的性能历史记录
ms.author: cosdar
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 09/07/2018
ms.localizationpriority: medium
ms.openlocfilehash: aefc9c3c33cb93be241aae4ef18d815a9f8defef
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856140"
---
# <a name="performance-history-for-virtual-machines"></a>虚拟机的性能历史记录

> 适用于： Windows Server 2019

本主题中的[性能历史记录存储空间直通](performance-history.md)详细说明了为虚拟机（VM）收集的性能历史记录。 性能历史记录适用于每个正在运行的群集 VM。

   > [!NOTE]
   > 收集可能需要几分钟时间才能开始新创建或重命名的虚拟机。

## <a name="series-names-and-units"></a>序列名称和单位

为每个符合条件的 VM 收集这些系列：

| 序列                            | 单位             |
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

此外，为附加到 VM 的每个 VHD 聚合所有虚拟硬盘（VHD）序列，如 `vhd.iops.total`。

## <a name="how-to-interpret"></a>如何解释


| 序列                            | 说明                                                                                                  |
|-----------------------------------|--------------------------------------------------------------------------------------------------------------|
| `vm.cpu.usage`                    | 虚拟机使用其主机服务器的处理器的百分比。                                   |
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
   > 计数器在整个间隔内进行测量，而不是采样。 例如，如果 VM 闲置了9秒，但高峰在第10秒钟内使用了50% 的主机 CPU，则其 `vm.cpu.usage` 将在10秒的时间间隔内平均地记录为5%。 这可确保其性能历史记录捕获所有活动，并使干扰稳定。

## <a name="usage-in-powershell"></a>在 PowerShell 中的用法

使用[GET VM](https://docs.microsoft.com/powershell/module/hyper-v/get-vm) cmdlet：

```PowerShell
Get-VM <Name> | Get-ClusterPerf
```

   > [!NOTE]
   > Get VM cmdlet 仅返回本地（或指定）服务器上的虚拟机，而不是在群集上返回。

## <a name="see-also"></a>另请参阅

- [存储空间直通的性能历史记录](performance-history.md)
