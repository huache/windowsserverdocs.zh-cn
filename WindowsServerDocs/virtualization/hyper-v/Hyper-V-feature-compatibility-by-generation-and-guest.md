---
title: Hyper-v 功能按代和来宾的兼容性
description: 列出与注册表项 Hyper-v 功能兼容的生成和操作系统
ms.topic: article
ms.assetid: 81c1f32d-7814-4992-8a66-dd4b77c939b4
ms.author: benarm
author: BenjaminArmstrong
ms.date: 12/05/2016
ms.openlocfilehash: e2c66cc95513cce54696f785d5016a380bc9fe98
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745892"
---
# <a name="hyper-v-feature-compatibility-by-generation-and-guest"></a>Hyper-v 功能按代和来宾的兼容性

>适用于：Windows Server 2016

本文中的表介绍与一些 Hyper-v 功能兼容的生成和操作系统，这些功能按类别分组。 通常，可以使用第2代虚拟机运行最新操作系统的功能，从而获得最佳可用性。

请记住，一些功能依赖于硬件或其他基础结构。 有关硬件的详细信息，请参阅 [Windows Server 2016 上的 Hyper-v 系统要求](System-requirements-for-Hyper-V-on-Windows.md)。 在某些情况下，功能可用于任何受支持的来宾操作系统。 有关支持的操作系统的详细信息，请参阅：

* [支持的 Linux 和 FreeBSD 虚拟机](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)
* [受支持的 Windows 来宾操作系统](Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md)

## <a name="availability-and-backup"></a>可用性和备份

Feature  | Generation | 来宾操作系统
------------- | ------------- | -----------
检查点 | 1和2 | 任何受支持的来宾
来宾群集 | 1和2 | 运行群集感知应用程序并已安装 iSCSI 目标软件的来宾
复制 | 1和2 | 任何受支持的来宾
域控制器 | 1和2 | 任何受支持的 Windows Server 来宾，只使用生产检查点。 请参阅 [支持的 Windows Server 来宾操作系统](./supported-windows-guest-operating-systems-for-hyper-v-on-windows.md#supported-windows-server-guest-operating-systems)

## <a name="compute"></a>计算

Feature  | Generation | 来宾操作系统
------------- | ------------- | -----------
动态内存 | 1和2 | 支持的来宾的特定版本。 请参阅 [hyper-v 动态内存概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831766(v=ws.11)) 版本低于 windows Server 2016 和 windows 10 的版本。
热添加/删除内存 | 1和2 | Windows Server 2016、Windows 10
虚拟 NUMA | 1和2 | 任何受支持的来宾

## <a name="development-and-test"></a>开发和测试
Feature  | Generation | 来宾操作系统
------------- | ------------- | -----------
COM/串行端口 | 1和2 <br>**注意：** 对于第2代，使用 Windows PowerShell 进行配置。 有关详细信息，请参阅为 [内核调试添加 COM 端口](./plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v.md#add-a-com-port-for-kernel-debugging)。 | 任何受支持的来宾

## <a name="mobility"></a>活动能力

Feature  | Generation | 来宾操作系统
------------- | ------------- | -----------
实时迁移  | 1和2 |  任何受支持的来宾
导入/导出 | 1和2 |  任何受支持的来宾

## <a name="networking"></a>网络

功能  | Generation | 来宾操作系统
------------- | ------------- | -----------
热添加/删除虚拟网络适配器 | 2 | 任何受支持的来宾
旧版虚拟网络适配器 | 1 | 任何受支持的来宾
单个根输入/输出虚拟化 (SR-IOV)  | 1和2 | 64位 Windows 来宾，从 Windows Server 2012 和 Windows 8 开始。
虚拟机多队列 (VMMQ)  | 1和2  | 任何受支持的来宾

## <a name="remote-connection-experience"></a>远程连接体验

Feature  | Generation | 来宾操作系统
------------- | ------------- | -----------
离散设备分配 (DDA)  | 1和2 | Windows Server 2016、windows Server 2012 R2 （仅安装了更新3133690）、Windows 10 <br> **注意：** 有关更新3133690的详细信息，请参阅 [此](https://support.microsoft.com/kb/3133690) 支持文章。
增强会话模式 | 1和2 | Windows Server 2016、Windows Server 2012 R2、Windows 10 和 Windows 8.1，并启用远程桌面服务 <br>**注意**：你可能还需要配置主机。 有关详细信息，请参阅 [使用 VMConnect 上的 hyper-v 虚拟机上的本地资源](./learn-more/Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md)。
RemoteFx | 1和2 | 从 Windows 8 开始，32位和64位 Windows 版本上的第1代。 <br> 64位 Windows 10 版本上的第2代

## <a name="security"></a>安全性

Feature  | Generation | 来宾操作系统
------------- | ------------- | -----------
安全启动 | 2 | **Linux**： Ubuntu 14.04 及更高版本、SUSE Linux Enterprise Server 12 及更高版本、Red Hat Enterprise Linux 7.0 及更高版本以及 CentOS 7.0 及更高版本<br>**Windows**：可在第2代虚拟机上运行的所有支持的版本
受防护的虚拟机 | 2 | **Windows**：可在第2代虚拟机上运行的所有支持的版本

## <a name="storage"></a>存储

功能  | Generation | 来宾操作系统
------------- | ------------- | -----------
共享虚拟硬盘 (VHDX 仅)  | 1和2  | Windows Server 2016、Windows Server 2012 R2、Windows Server 2012
SMB3 | 1和2 | 所有支持 SMB3 的
存储空间直通 | 2 | Windows Server 2016
虚拟光纤通道 | 1和2 | Windows Server 2016、Windows Server 2012 R2、Windows Server 2012
VHDX 格式 | 1和2 | 任何受支持的来宾