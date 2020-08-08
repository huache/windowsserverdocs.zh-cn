---
title: Hyper-v 上的 Linux 和 FreeBSD 虚拟机的功能说明
description: 描述在虚拟机上使用 Linux 和 FreeBSD 时影响核心组件（如网络、存储、内存）的功能
manager: dongill
ms.topic: article
ms.assetid: a9ee931d-91fc-40cf-9a15-ed6fa6965cb6
author: shirgall
ms.author: kathydav
ms.date: 10/03/2016
ms.openlocfilehash: b5ffb10feaa32b7dce2c491d2e7bdd1d467818fa
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87989095"
---
# <a name="feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v"></a>Hyper-v 上的 Linux 和 FreeBSD 虚拟机的功能说明

>适用于： Windows Server 2016，Hyper-v Server 2016，Windows Server 2012 R2，Hyper-v Server 2012 R2，Windows Server 2012，Hyper-v Server 2012，Windows Server 2008 R2，Windows 10，Windows 8.1，Windows 8，Windows 7.1，Windows 7

本文介绍在虚拟机上使用 Linux 和 FreeBSD 时组件中的可用功能，如核心、网络、存储和内存。

## <a name="core"></a>核心

|**功能**|**说明**|
|-|-|
|集成关闭|使用此功能，管理员可以从 Hyper-v 管理器关闭虚拟机。 有关详细信息，请参阅[操作系统关闭](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn798297(v=ws.11)#BKMK_Shutdown)。|
|时间同步|此功能可确保虚拟机内的维护时间与主机上的维护时间保持同步。 有关详细信息，请参阅[时间同步](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn798297(v=ws.11)#BKMK_time)。|
|Windows Server 2016 准确时间|此功能允许来宾使用 Windows Server 2016 准确的时间功能，这会缩短与主机之间的时间同步以1ms 准确性。 有关详细信息，请参阅[Windows Server 2016 准确时间](../../networking/windows-time-service/accurate-time.md)|
|多处理支持|利用此功能，虚拟机可以通过配置多个虚拟 Cpu 在主机上使用多个处理器。|
|检测信号|利用此功能，主机可以跟踪虚拟机的状态。 有关详细信息，请参阅[检测信号](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn798297(v=ws.11)#BKMK_heartbeat)。|
|集成鼠标支持|利用此功能，你可以在虚拟机桌面上使用鼠标，还可以在 Windows Server 桌面和虚拟机的 Hyper-v 控制台之间无缝使用鼠标。|
|Hyper-v 特定存储设备|此功能为连接到虚拟机的存储设备授予高性能访问权限。|
|Hyper-v 特定网络设备|此功能为连接到虚拟机的网络适配器授予高性能访问权限。|

## <a name="networking"></a>网络

|**功能**|**说明**|
|-|-|
|Jumbo 帧|使用此功能，管理员可以增加超过1500个字节的网络帧大小，这将导致网络性能大幅提高。|
|VLAN 标记和中继|此功能允许你为虚拟机配置虚拟 LAN (VLAN) 通信。|
|实时迁移|利用此功能，可以将虚拟机从一台主机迁移到另一台主机。 有关详细信息，请参阅[虚拟机实时迁移概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831435(v=ws.11))。|
|静态 IP 注入|利用此功能，可以在虚拟机故障转移到另一台主机上的副本后复制该虚拟机的静态 IP 地址。 此类 IP 复制确保在发生故障转移事件后，网络工作负载可以继续顺利运行。|
|vRSS (虚拟接收方缩放) |跨虚拟机中的多个虚拟处理器跨虚拟网络适配器的负载。有关详细信息，请参阅[Windows Server 2012 R2 中的虚拟接收方缩放](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383582(v=ws.11))。|
|TCP 分段和校验和卸载|在网络数据传输过程中，将分段和校验和从来宾 CPU 传输到主机虚拟交换机或网络适配器。|
|大型接收卸载 (LRO) |通过将多个数据包聚合到更大的缓冲区中来增加高带宽连接的入站吞吐量，从而降低 CPU 开销。|
|SR-IOV|单个根 i/o 设备使用 DDA 允许来宾访问特定 NIC 卡的某些部分，从而降低延迟并提高吞吐量。 SR-IOV 需要最新的物理功能 (PF) 主机上的驱动程序和虚函数上的驱动程序 (虚拟机上的虚拟机) 驱动程序。|

## <a name="storage"></a>存储

|**功能**|**说明**|
|-|-|
|VHDX 调整大小|使用此功能，管理员可以调整附加到虚拟机的固定大小的 .vhdx 文件的大小。 有关详细信息，请参阅[联机虚拟硬盘大小调整概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282286(v=ws.11))。|
|虚拟光纤通道|利用此功能，虚拟机可以识别光纤通道设备并以本机方式装载它。 有关详细信息，请参阅 [Hyper-V 虚拟光纤通道概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831413(v=ws.11))。|
|实时虚拟机备份|此功能便于零停机实时虚拟机的备份。<p>请注意，如果虚拟机的虚拟硬盘 (Vhd) （如服务器消息块 (SMB) 共享或 iSCSI 卷），则备份操作不会成功。 此外，请确保备份目标不与备份的卷位于同一卷上。|
|剪裁支持|TRIM 提示通知驱动器，应用程序不再需要以前分配的某些扇区，并且可以将其清除。 当应用通过文件进行大空间分配，然后自行管理对文件（例如虚拟硬盘文件）的分配时，通常使用此过程。|
|SCSI WWN|Storvsc 驱动程序从连接到虚拟机的设备的端口和节点提取全球通用名称 (WWN) 信息，并创建相应的 sysfs 文件。 |

## <a name="memory"></a>内存

|**功能**|**说明**|
|-|-|
|PAE 内核支持|物理地址扩展 (PAE) 技术允许32位内核访问大于4GB 的物理地址空间。 旧版 Linux 分发（如 RHEL 1.x）用于发送启用了 PAE 的单独内核。 新分发（如 RHEL 1.x）具有预生成的 PAE 支持。|
|MMIO 间隙的配置|利用此功能，设备制造商可以配置内存映射 i/o (MMIO) 间隔的位置。 MMIO 间隙通常用于将设备上的可用物理内存划分 (JeOS) 和设备支持的实际软件基础结构之间。|
|动态内存-热添加|当虚拟机正在运行时，主机可以动态增加或减少可用于虚拟机的内存量。 预配之前，管理员在 "虚拟机设置" 面板中启用动态内存，并指定虚拟机的启动内存、最小内存和最大内存。 如果虚拟机处于操作状态动态内存则无法禁用，只能更改最小值和最大值设置。  (最好的做法是将这些内存大小指定为128MB 的倍数。 ) <p>虚拟机首次启动时，可用内存等于**启动内存**。 由于应用程序工作负载的原因，Hyper-v 可能会通过热添加机制将更多内存动态分配给虚拟机，前提是该版本的内核支持。 分配的最大内存量受**最大内存**参数值的限制。<p>Hyper-v 管理器的 "内存" 选项卡将显示分配给虚拟机的内存量，但虚拟机中的内存统计信息将显示分配的最大内存量。<p>有关详细信息，请参阅[hyper-v 动态内存概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831766(v=ws.11))。<p>|
|动态内存-膨胀|当虚拟机正在运行时，主机可以动态增加或减少可用于虚拟机的内存量。 预配之前，管理员在 "虚拟机设置" 面板中启用动态内存，并指定虚拟机的启动内存、最小内存和最大内存。 如果虚拟机处于操作状态动态内存则无法禁用，只能更改最小值和最大值设置。  (最好的做法是将这些内存大小指定为128MB 的倍数。 ) <p>虚拟机首次启动时，可用内存等于**启动内存**。 由于应用程序工作负载的原因，Hyper-v 可能会通过) 上方 (的热添加机制动态分配更多内存给虚拟机。 随着内存需求的增加，Hyper-v 可能会通过气球机制从虚拟机自动取消预配内存。 Hyper-v 将不会在**最小内存**参数下取消预配内存。<p>Hyper-v 管理器的 "内存" 选项卡将显示分配给虚拟机的内存量，但虚拟机中的内存统计信息将显示分配的最大内存量。<p>有关详细信息，请参阅[hyper-v 动态内存概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831766(v=ws.11))。<p>|
|运行时内存大小调整|管理员可以设置虚拟机在运行时可用的内存量，增加内存 ( "热添加" ) 或降低 ( "热删除" ) 。 内存通过气球驱动程序返回到 Hyper-v (参阅 "动态内存-膨胀" ) 。 气球驱动程序在膨胀之后维护最少的可用内存（称为 "楼层"），因此，在当前需求和此楼层量之后，分配的内存不能减少。 Hyper-v 管理器的 "内存" 选项卡将显示分配给虚拟机的内存量，但虚拟机中的内存统计信息将显示分配的最大内存量。  (最好的做法是将内存值指定为128MB 的倍数。 ) |

## <a name="video"></a>视频

|**功能**|**说明**|
|-|-|
|Hyper-v 特定视频设备|此功能为虚拟机提供高性能的图形和卓越的分辨率。 此设备不提供增强会话模式或 RemoteFX 功能。|

## <a name="miscellaneous"></a>杂项

|**功能**|**说明**|
|-|-|
|KVP) exchange (键值对|此功能为虚拟机的 KVP) exchange 服务 (提供密钥/值对。 通常，管理员使用 KVP 机制在虚拟机上执行读取和写入自定义数据操作。 有关详细信息，请参阅[数据交换：使用键值对在 hyper-v 上的主机和来宾之间共享信息](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn798287(v=ws.11))。|
|不可屏蔽中断|使用此功能，管理员可以) 虚拟机 (NMI 发出不可屏蔽的中断。 在获取因应用程序错误而变得无响应的操作系统崩溃转储时，NMIs 非常有用。 重新启动后，可以诊断这些故障转储。|
|从主机到来宾的文件复制|此功能允许在不使用网络适配器的情况下将文件从主机物理计算机复制到来宾虚拟机。 有关详细信息，请参阅 "[来宾服务](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn798297(v=ws.11)#BKMK_guest)"。|
|lsvmbus 命令|此命令获取有关 Hyper-v 虚拟机总线上的设备的信息 (VMBus) 类似于 lspci 之类的信息命令。|
|Hyper-v 套接字|这是主机和来宾操作系统之间的附加信道。 若要加载和使用 Hyper-v 套接字内核模块，请参阅[创建自己的 integration services](/virtualization/hyper-v-on-windows/user-guide/make-integration-service)。|
|PCI 传递/DDA|使用 Windows Server 2016，管理员可以通过离散设备分配机制传递 PCI Express 设备。 常见设备为网卡、图形卡和特殊存储设备。 虚拟机将需要适当的驱动程序才能使用公开的硬件。 必须为虚拟机分配硬件，才能使用该硬件。<p>有关详细信息，请参阅[离散设备分配说明和背景](https://blogs.technet.microsoft.com/virtualization/2015/11/19/discrete-device-assignment-description-and-background/)。<p>DDA 是 SR-IOV 网络的先决条件。 需要将虚拟端口分配给虚拟机，并且虚拟机必须使用正确的虚拟功能 (VF) 驱动程序以进行设备多路复用。|

## <a name="generation-2-virtual-machines"></a>第 2 代虚拟机

|**功能**|**说明**|
|-|-|
|使用 UEFI 启动|此功能允许虚拟机使用统一可扩展固件接口 (UEFI) 启动。<p>有关详细信息，请参阅[第 2 代虚拟机概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282285(v=ws.11))。|
|安全启动|此功能允许虚拟机使用基于 UEFI 的安全启动模式。 在安全模式下启动虚拟机时，将使用 UEFI 数据存储中存在的签名来验证各种操作系统组件。<p>有关详细信息，请参阅[安全启动](/previous-versions/windows/it-pro/windows-8.1-and-8/dn486875(v=ws.11))。|

## <a name="see-also"></a>另请参阅

* [Hyper-v 上支持的 CentOS 和 Red Hat Enterprise Linux 虚拟机](Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md)

* [Hyper-V 上支持的 Debian 虚拟机](Supported-Debian-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 Oracle Linux 虚拟机](Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 SUSE 虚拟机](Supported-SUSE-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 Ubuntu 虚拟机](Supported-Ubuntu-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 FreeBSD 虚拟机](Supported-FreeBSD-virtual-machines-on-Hyper-V.md)

* [在 Hyper-v 上运行 Linux 的最佳实践](Best-Practices-for-running-Linux-on-Hyper-V.md)

* [在 Hyper-v 上运行 FreeBSD 的最佳做法](Best-practices-for-running-FreeBSD-on-Hyper-V.md)