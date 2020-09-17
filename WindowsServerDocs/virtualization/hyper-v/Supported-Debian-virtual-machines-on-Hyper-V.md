---
title: Hyper-V 上支持的 Debian 虚拟机
description: 列出每个版本中包含的 Linux integration services 和功能
ms.topic: article
ms.assetid: 3cc62c10-02a3-4633-960c-23bf91a45bd5
ms.author: benarm
author: BenjaminArmstrong
ms.date: 04/07/2020
ms.openlocfilehash: c0ea0a8e9a030c8d35bf3042b16108523753b36b
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746542"
---
# <a name="supported-debian-virtual-machines-on-hyper-v"></a>Hyper-V 上支持的 Debian 虚拟机

>适用于： Windows Server 2019，Hyper-v Server 2019，Windows Server 2016，Hyper-v Server 2016，Windows Server 2012 R2，Hyper-v Server 2012 R2，Windows 10，Windows 8。1

以下功能分发映射指示每个版本中的功能。 表后面列出了每个分发的已知问题和解决方法。

## <a name="table-legend"></a>表图例

* **内置** 的-.lis 作为此 Linux 分发的一部分包含在内。 Microsoft 提供的 .LIS 下载包不适用于此分发版，因此不安装它。 **Lsmod**所示的内置 .lis (内核模块版本号，例如) 不同于 Microsoft 提供的 .lis 下载包上的版本号。 不匹配不会指示内置的 .LIS 版本已过期。

* &#10004; 功能可用

*  (*空白*) -功能不可用

| **功能**                                                                                                                                  | **Windows Server 操作系统版本** | **10.0-10.3 (buster) ** | **9.0-9.12 (stretch) ** | **8.0-8.11 (jessie) ** | **7.0-7.11 (wheezy) ** |
|----------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------|-----------------------|-----------------------|-----------------------|
| **可用性**                                                                                                                             |                                             | 内置              | 内置              | 内置              | 内置 (注释 5)      |
| **[核心](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#core)**                                                   | 2019、2016、2012 R2          | &#10004;              | &#10004;              | &#10004;              | &#10004;              |
| Windows Server 2016 准确时间                                                                                                            | 2019、2016                                  | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| **[网络](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#networking)**                                       |                                             |                       |                       |                       |                       |
| Jumbo 帧                                                                                                                                 | 2019、2016、2012 R2          | &#10004;              | &#10004;              | &#10004;              | &#10004;              |
| VLAN 标记和中继                                                                                                                    | 2019、2016、2012 R2          | &#10004;              | &#10004;              | &#10004;              | &#10004;              |
| 实时迁移                                                                                                                               | 2019、2016、2012 R2          | &#10004;              | &#10004;              | &#10004;              | &#10004;              |
| 静态 IP 注入                                                                                                                          | 2019、2016、2012 R2                   |                       |                       |                       |                       |
| vRSS                                                                                                                                         | 2019、2016、2012 R2                         | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| TCP 分段和校验和卸载                                                                                                       | 2019、2016、2012 R2          | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| SR-IOV                                                                                                                                       | 2019、2016                                  | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| **[存储](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#storage)**                                             |                                             |                       |                       |                       |                       |
| VHDX 调整大小                                                                                                                                  | 2019、2016、2012 R2                         | &#10004; 注释1       | &#10004; 注释1       | &#10004; 注释1       | &#10004; 注释1       |
| 虚拟光纤通道                                                                                                                        | 2019、2016、2012 R2                         |                       |                       |                       |                       |
| 实时虚拟机备份                                                                                                                  | 2019、2016、2012 R2                         | &#10004; Note2 | &#10004; Note2 | &#10004; Note2 | &#10004; Note2 |
| 剪裁支持                                                                                                                                 | 2019、2016、2012 R2                         | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| SCSI WWN                                                                                                                                     | 2019、2016、2012 R2                         | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| **[记忆](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#memory)**                                               |                                             |                       |                       |                       |                       |
| PAE 内核支持                                                                                                                           | 2019、2016、2012 R2          | &#10004;              | &#10004;              | &#10004;              | &#10004;              |
| MMIO 间隙的配置                                                                                                                    | 2019、2016、2012 R2                         | &#10004;              | &#10004;              | &#10004;              | &#10004;              |
| 动态内存-热添加                                                                                                                     | 2019、2016、2012 R2                   | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| 动态内存-膨胀                                                                                                                  | 2019、2016、2012 R2                   | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| 运行时内存大小调整                                                                                                                        | 2019、2016                                  | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| **[显示](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#video)**                                                 |                                             |                       |                       |                       |                       |
| Hyper-v 特定视频设备                                                                                                                | 2019、2016、2012 R2          | &#10004;              | &#10004;              | &#10004;              |                       |
| **[杂项](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#miscellaneous)**                                 |                                             |                       |                       |                       |                       |
| 键值对                                                                                                                               | 2019、2016、2012 R2          | &#10004; 备注2       | &#10004; 备注2       | &#10004; 备注2       |                       |
| 不可屏蔽中断                                                                                                                       | 2019、2016、2012 R2                         | &#10004;              | &#10004;              | &#10004;              |                       |
| 从主机到来宾的文件复制                                                                                                                 | 2019、2016、2012 R2                         | &#10004; 备注2       | &#10004; 备注2       | &#10004; 备注2       |                       |
| lsvmbus 命令                                                                                                                              | 2019、2016、2012 R2          |                       |                       |                       |                       |
| Hyper-v 套接字                                                                                                                              | 2019、2016                                  | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| PCI 传递/DDA                                                                                                                          | 2019、2016                                  | &#10004; 备注4       | &#10004; 备注4       |                       |                       |
| **[第 2 代虚拟机](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#generation-2-virtual-machines)** |                                             |                       |                       |                       |                       |
| 使用 UEFI 启动                                                                                                                              | 2019、2016、2012 R2                         | &#10004; 备注3       | &#10004; 备注3       | &#10004; 备注3       |                       |
| 安全启动                                                                                                                                  | 2019、2016                                  | &#10004;              |                       |                       |                       |


## <a name="notes"></a>备注

1. 不支持在大于2TB 的 Vhd 上创建文件系统。

2. 从 Debian 8.3 开始，手动安装的 Debian 包 "hyperv-守护程序" 包含键/值对、fcopy 和 VSS 守护程序。 在 Debian 1.x 和 8.0-8.2 上，hyperv 守护程序包必须来自 [Debian precise-backports](https://wiki.debian.org/Backports)。

3. 在 Windows Server 2012 R2 第2代虚拟机上，默认情况下已启用安全启动，某些 Linux 虚拟机将无法启动，除非禁用了安全启动选项。 你可以在**Hyper-v 管理器**中虚拟机设置的 "**固件**" 部分禁用安全启动，也可以使用 Powershell 禁用它：

   ```Powershell
   Set-VMFirmware -VMName "VMname" -EnableSecureBoot Off
   ```
4. 最新的上游内核功能只能通过使用内核包含的 [Debian precise-backports](https://wiki.debian.org/Backports)提供。

5. 尽管 Debian 7、windows 不支持并使用较旧的内核，但 Debian precise-backports for Debian 7、windows 中包含的内核已改进了 Hyper-v 功能。

另请参阅

* [Hyper-v 上支持的 CentOS 和 Red Hat Enterprise Linux 虚拟机](Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 Oracle Linux 虚拟机](Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 SUSE 虚拟机](Supported-SUSE-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 Ubuntu 虚拟机](Supported-Ubuntu-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 FreeBSD 虚拟机](Supported-FreeBSD-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上的 Linux 和 FreeBSD 虚拟机的功能说明](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md)

* [在 Hyper-v 上运行 Linux 的最佳实践](Best-Practices-for-running-Linux-on-Hyper-V.md)
