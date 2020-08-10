---
title: 远程桌面服务 VDI 支持的 Windows 10 安全配置
description: 提供有关 Windows Server 2016 中 RDS 支持的 Windows 10 VDI 配置的信息。
ms.author: elizapo
ms.date: 10/27/2016
ms.topic: article
ms.assetid: 8f164f5d-a498-4f91-a12f-3e01d554f810
author: lizap
manager: dongill
ms.openlocfilehash: 7fd8de56d02dfe83add67b740405265a232747d9
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87946340"
---
# <a name="supported-windows-10-security-configurations-for-remote-desktop-services-vdi"></a>远程桌面服务 VDI 支持的 Windows 10 安全配置

> 适用于：Windows Server 2016

Windows 10 和 Windows Server 2016 提供操作系统中内置的保护层来进一步防止出现安全漏洞，帮助阻止恶意攻击并提高虚拟机、应用程序和数据的安全性。

> [!NOTE]
> 请务必查看[远程桌面服务支持的配置信息](rds-supported-config.md)。

下表概述了使用 RDS 的 VDI 部署支持其中的哪些新功能。

|  VDI 集合类型               |  托管共用 |  托管个人 |  非托管共用                                     |  非托管个人                                    |
|-------------------------------------|------------------|--------------------|--------------------------------------------------------|--------------------------------------------------------|
| [Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard)                    | 是              | 是                | 是                                                    | 是                                                    |
| [Device Guard](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)                        | 是              | 是                | 是                                                    | 是                                                    |
| [Remote Credential Guard](/windows/security/identity-protection/remote-credential-guard)             | 否               | 否                 | 否                                                     | 否                                                     |
| [受防护的 VM 和加密支持的 VM](../../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms.md) | 否               | 否                 | 加密支持的采用其他配置的 VM | 加密支持的采用其他配置的 VM |

## <a name="remote-credential-guard"></a>Remote Credential Guard：

仅支持直接将 Remote Credential Guard 连接到目标计算机，而不支持通过远程桌面连接代理和远程桌面网关进行连接。
> [!NOTE]
> 如果在单实例环境中使用连接代理，并且 DNS 名称与计算机名称相匹配，则你也许可以使用 Remote Credential Guard，不过它不受支持。

## <a name="shielded-vms-and-encryption-supported-vms"></a>受防护的 VM 和加密支持的 VM：

- 远程桌面服务 VDI 不支持受防护的 VM

若要利用加密支持的 VM：
- 请在远程桌面服务集合创建过程以外使用非托管集合和预配技术来预配虚拟机。
- 不支持用户配置文件磁盘，因为它们依赖于差异磁盘
