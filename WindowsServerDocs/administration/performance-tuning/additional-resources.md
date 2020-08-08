---
title: 其他服务器性能优化资源
description: 其他服务器性能优化资源
ms.topic: article
ms.author: phstee
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 8659a836d3ad3bd3e5e61f2849e2327e57536c76
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87992357"
---
# <a name="additional-performance-tuning-resources"></a>其他性能优化资源

使用本主题中的链接来了解有关此优化指南中讨论的概念的详细信息。

## <a name="microsoft-windows-server-websites"></a>Microsoft Windows Server 网站
-   [Windows Server 编录](https://www.windowsservercatalog.com/)

-   [Windows Sysinternals](/sysinternals/)

-   [事务处理性能委员会](http://www.tpc.org/)

-   [Windows 评估和部署工具包](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)

## <a name="power-management-tuning-resources"></a>电源管理优化资源

-   [Windows 中的电源策略配置和部署](/windows-hardware/customize/power-settings/configure-processor-power-management-options)

-   [使用 PowerCfg 评估系统能效](/previous-versions/windows/it-pro/windows-vista/cc748940(v=ws.10))

-   [中断-关联策略工具](https://support.microsoft.com/kb/252867)

## <a name="networking-subsystem-tuning-resources"></a>网络子系统优化资源

-   [可缩放的网络：消除接收处理瓶颈— RSS 简介](https://download.microsoft.com/download/5/D/6/5D6EAF2B-7DDF-476B-93DC-7CF0072878E6/NDIS_RSS.doc)

-   [Windows 筛选平台](/windows-hardware/drivers/network/porting-packet-processing-drivers-and-apps-to-wfp)

-   [网络部署指南：部署高速网络功能](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg162681(v=ws.10))

## <a name="storage-subsystem-tuning-resources"></a>存储子系统优化资源

-   此文档的 Windows (部分的[磁盘子系统性能分析](https://download.microsoft.com/download/e/b/a/eba1050f-a31d-436b-9281-92cdfeae4b45/subsys_perf.doc)已过期，但所捕获的许多一般观测和指导原则仍然准确且相关。 ) 

## <a name="file-server-tuning-resources"></a>文件服务器优化资源

-   [适用于 Microsoft 网络文件系统服务的性能优化指南](/previous-versions/tn-archive/bb463205(v=technet.10))

-   [\[FSSO \] ：文件访问服务系统概述](https://download.microsoft.com/download/5/0/1/501ED102-E53F-4CE0-AA6B-B0F93629DDC6/Windows/%5bMS-FSSO%5d.pdf)

-   [如何禁用 TCP 自动调谐诊断工具](https://support.microsoft.com/kb/967475)

## <a name="active-directory-server-tuning-resources"></a>Active Directory Server 优化资源
-   [Active Directory 性能](/previous-versions/dn567654(v=vs.85))
-   [如何在 Windows Server 2003 和 Windows 2000 Server 中配置 Active Directory 诊断事件日志记录](https://support.microsoft.com/kb/314980)

## <a name="virtualization-server-tuning-resources"></a>虚拟化服务器优化资源

-   [Windows Server 2016 中 Hyper-v 的新增功能](../../virtualization/hyper-v/what-s-new-in-hyper-v-on-windows.md)

-   [Hyper-V 动态内存配置指南](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff817651(v=ws.10))

-   [NUMA 节点均衡](/archive/blogs/winserverperformance/numa-node-balancing)

-   [Hyper-v WMI 提供程序](/previous-versions/windows/desktop/virtual/windows-virtualization-portal)

-   [Hyper-v WMI 类](/previous-versions/windows/desktop/virtual/virtualization-wmi-classes)

-   [关于虚拟机和来宾操作系统](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794868(v=ws.10))

-   [优化 Hyper-v 存储并对其进行故障排除](/archive/blogs/microsoft_press/new-book-optimizing-and-troubleshooting-hyper-v-storage)

-   [对 Hyper-v 网络进行优化和故障排除](https://blogs.msdn.com/b/microsoft_press/archive/2013/07/12/rtm-d-today-optimizing-and-troubleshooting-hyper-v-networking.aspx)

## <a name="print-server-tuning-resources"></a>打印服务器优化资源

-   [Print Server Scalability and Capacity Planning](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn554243(v=ws.11))

## <a name="server-workload-tuning-resources"></a>服务器工作负荷优化资源

-   [NTttcp 性能优化](/previous-versions/dn567663(v=vs.85))

-   [Ttcp](http://en.wikipedia.org/wiki/Ttcp)

-   [如何使用 NTttcp 测试网络性能](https://msdn.microsoft.com/windows/hardware/gg463264.aspx)

-   [使用文件服务器 Capactiy 工具](/previous-versions/dn567658(v=vs.85))

-   [使用 SPECsfs2008 文件服务器](/previous-versions/dn567653(v=vs.85))

-   [销售和分发工作负载的性能优化](/previous-versions/dn567646(v=vs.85))

-   [ (OLTP) 的联机事务处理的性能优化](/previous-versions/dn567642(v=vs.85))

-   [如何：将 SQL Server 配置为使用软件 NUMA](https://go.microsoft.com/fwlink/?LinkId=98292)

-   [如何将 TCP/IP 端口映射到 NUMA 节点](https://go.microsoft.com/fwlink/?LinkId=98293)

-   [ALTER SERVER CONFIGURATION (Transact-SQL)](/sql/t-sql/statements/alter-server-configuration-transact-sql?view=sql-server-ver15)


## <a name="server-tuning-tools"></a>服务器优化工具

-   [Microsoft Server Performance Advisor](/previous-versions/dn481522(v=vs.85))

## <a name="performance-tuning-guidelines-for-previous-versions-of-windows-server"></a>以前版本的 Windows Server 的性能优化指南


使用性能优化指导原则提高 Windows Server 早期版本的性能。

下面是以前版本的 Windows Server 的性能优化指南列表：

-   [Windows Server 2012 R2 性能优化指南](https://www.microsoft.com/download/details.aspx?id=51960)

-   [Windows Server 2012 的性能优化指南](https://download.microsoft.com/download/0/0/B/00BE76AF-D340-4759-8ECD-C80BC53B6231/performance-tuning-guidelines-windows-server-2012.docx)

-   [Windows Server 2008 R2 性能优化指南](https://download.microsoft.com/download/6/B/2/6B2EBD3A-302E-4553-AC00-9885BBF31E21/Perf-tun-srv-R2.docx)

-   [Windows Server 2008 的性能优化指南](https://download.microsoft.com/download/9/c/5/9c5b2167-8017-4bae-9fde-d599bac8184a/Perf-tun-srv.docx)