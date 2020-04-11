---
title: Hyper-V 的第 2 代虚拟机安全设置
description: 描述 Hyper-V 管理器中可用于第 2 代虚拟机的安全设置
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: 06ab4f5f-6b8e-4058-8108-76785aa93d4c
author: larsiwer
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: 7eb867529d38ab21ee21c19f92c89ed4128b0ea4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860800"
---
# <a name="generation-2-virtual-machine-security-settings-for-hyper-v"></a>Hyper-V 的第 2 代虚拟机安全设置

>适用于：Windows Server 2016、Microsoft Hyper-V Server 2016、Windows Server 2019、Microsoft Hyper-V Server 2019

使用 Hyper-V 管理器中的虚拟机安全设置来帮助保护虚拟机的数据和状态。 可以保护虚拟机免受可能在主机上运行的恶意软件以及数据中心管理员的查看、盗窃和篡改。 获得的安全级别取决于所运行的主机硬件、虚拟机代系以及是否设置了用于授权主机启动受防护的虚拟机的服务（该服务称为主机保护者服务）。  

主机保护者服务是 Windows Server 2016 中的新角色， 可识别合法的 Hyper-V 主机，并允许它们运行给定的虚拟机。 通常会为数据中心设置主机保护者服务。 但可以创建受防护的虚拟机以在本地运行，而无需设置主机保护者服务。 稍后可将受防护的虚拟机分配给主机保护者结构。  

如果尚未设置主机保护者服务或在 Hyper-V 主机上以本地模式运行它，且该主机具有虚拟机所有者的保护者密钥，则可以更改本主题中描述的设置。   保护者密钥的所有者是创建并共享私有或公共密钥以拥有使用该密钥创建的所有虚拟机的组织。  

若要了解如何使用主机保护者服务使虚拟机更加安全，请参阅以下资源。  

- [增强构造：保护 Hyper-V 中的租户密钥（Ignite 视频）](https://go.microsoft.com/fwlink/?LinkId=746379)
- [受保护的结构和受防护的 VM](https://go.microsoft.com/fwlink/?LinkId=746381)

## <a name="secure-boot-setting-in-hyper-v-manager"></a>Hyper-V 管理器中的安全启动设置  

安全启动是第 2 代虚拟机提供的一项功能，可帮助防止在启动时运行未经授权的固件、操作系统或统一可扩展固件接口 (UEFI) 驱动程序（也称为选项 ROM）。 默认情况下，安全启动处于启用状态。 可以对运行 Windows 或 Linux 分发操作系统的第 2 代虚拟机使用安全启动。  

下表中所述的模板涉及验证启动过程的完整性所需的证书。  

|模板名称|说明|  
|-----------------|---------------|  
|Microsoft Windows|选择此项以安全启动适用于 Windows 操作系统的虚拟机。|  
|Microsoft UEFI 证书颁发机构|选择此项以安全启动适用于 Linux 分发操作系统的虚拟机。|  
|开放源受防护的 VM|此模板可用于[基于 Linux 的受防护的 VM](https://docs.microsoft.com/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-create-a-linux-shielded-vm-template) 的安全启动。|

有关详细信息，请参阅以下主题。  

- [Windows 10 安全概述](https://docs.microsoft.com/windows/security/threat-protection/overview-of-threat-mitigations-in-windows-10)  
- [是否应在 Hyper-V 中创建第 1 代或第 2 代虚拟机？](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md)  
- [Hyper-V 上的 Linux 和 FreeBSD 虚拟机](../Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)  

## <a name="encryption-support-settings-in-hyper-v-manager"></a>Hyper-V 管理器中的加密支持设置

可以通过选择以下加密支持选项来帮助保护虚拟机的数据和状态。  

- **启用受信任的平台模块** - 此设置使虚拟化的受信任平台模块 (TPM) 芯片可用于虚拟机。 这使来宾可使用 BitLocker 对虚拟机磁盘进行加密。
  - 如果 Hyper-V 主机运行的是 Windows 10 1511，则必须启用隔离用户模式。 
- **加密状态和 VM 迁移流量** - 对虚拟机已保存状态和实时迁移流量进行加密。

### <a name="enable-isolated-user-mode"></a>启用隔离用户模式

如果在运行早于 Windows 10 周年更新的 Windows 版本的 Hyper-V 主机上选择“启用受信任的平台模块”，则必须启用隔离用户模式  。 对于运行 Windows Server 2016 或 Windows 10 周年更新或更高版本的 Hyper-V 主机，无需执行此操作。

隔离用户模式是在 Hyper-V 主机上的虚拟安全模式内托管安全应用程序的运行时环境。 虚拟安全模式用于保护虚拟 TPM 芯片的状态。  

若要在运行早期版本的 Windows 10 的 Hyper-V 主机上启用隔离用户模式，  

1.  以管理员身份打开 Windows PowerShell。  

2.  运行以下命令：  

    ```  
    Enable-WindowsOptionalFeature -Feature IsolatedUserMode -Online  
    New-Item -Path HKLM:\SYSTEM\CurrentControlSet\Control\DeviceGuard -Force  
    New-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Control\DeviceGuard -Name EnableVirtualizationBasedSecurity -Value 1 -PropertyType DWord -Force  

    ```  

可以将启用了虚拟 TPM 的虚拟机迁移到运行 Windows Server 2016、Windows 10 内部版本 10586 或更高版本的任何主机。 但如果将其迁移到另一台主机，则可能无法启动它。 必须更新该虚拟机的密钥保护程序，才能授权新主机运行该虚拟机。 有关详细信息，请参阅[受保护的结构和受防护的 VM](https://go.microsoft.com/fwlink/?LinkId=746381) 和 [Windows Server 上的 Hyper-V 的系统要求](../System-requirements-for-Hyper-V-on-Windows.md)。  

## <a name="security-policy-in-hyper-v-manager"></a>Hyper-V 管理器中的安全策略  
为了提高虚拟机的安全性，请使用“启用防护”选项来禁用管理功能，例如控制台连接、PowerShell Direct 和某些集成组件  。 如果选择此选项，则会选择并强制执行“安全启动”、“启用受信任的平台模块”以及“加密状态和 VM 迁移流量”选项    。   

可以在本地运行受防护的虚拟机，而无需设置主机保护者服务。 但如果将其迁移到另一台主机，则可能无法启动它。 必须更新该虚拟机的密钥保护程序，才能授权新主机运行该虚拟机。 有关详细信息，请参阅[受保护的结构和受防护的 VM](https://go.microsoft.com/fwlink/?LinkId=746381)。  

有关 Windows Server 中安全性的详细信息，请参阅[安全和保障](../../../security/Security-and-Assurance.md)。  
