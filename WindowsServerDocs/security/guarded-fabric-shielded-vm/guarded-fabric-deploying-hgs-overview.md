---
title: 部署主机保护者服务
ms.prod: windows-server
ms.topic: article
ms.assetid: 310b63d9-5ac7-4961-98ef-103af45d706a
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 01/14/2020
ms.openlocfilehash: c1eea8c7f6da1140480d0a8deaafb2edb73528de
ms.sourcegitcommit: acfdb7b2ad283d74f526972b47c371de903d2a3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87769145"
---
# <a name="deploying-the-host-guardian-service"></a>部署主机保护者服务

>适用于： Windows Server 2019、Windows Server (半年频道) 、Windows Server 2016

提供托管环境的最重要目标之一是保证在环境中运行的虚拟机的安全性。 作为云服务商或企业私有云管理员，你可以使用受保护的构造为 VM 提供更安全的环境。 受保护的结构包括一项主机保护者服务 (HGS)（通常是由三个节点组成的群集）、一个或多个受保护的主机以及一组受防护的虚拟机 (VM)。

## <a name="video-deploying-a-guarded-fabric"></a>视频：部署受保护的构造

> [!VIDEO https://www.microsoft.com/videoplayer/embed/dcd8e99f-36f1-4bc8-b3d2-9576da38d9f1?autoplay=false]

## <a name="deployment-tasks-for-guarded-fabrics-and-shielded-vms"></a>受保护的构造和受防护的 Vm 的部署任务

下表分解了一些任务来部署受保护的构造，并根据不同的管理员角色创建受防护的 Vm。 请注意，当 HGS 管理员将 HGS 与授权的 Hyper-v 主机一起配置时，结构管理会同时收集和提供有关主机的标识信息。

| 步骤并链接到内容 | 映像 |
|--|--|--|
| 1-[验证 HGS 先决条件](guarded-fabric-prepare-for-hgs.md) | ![步骤1，验证先决条件](../media/Guarded-Fabric-Shielded-VM/guarded-host-verify.png) |
| 2-[配置第一个 HGS 节点](guarded-fabric-choose-where-to-install-hgs.md) | ![步骤2，配置第一个 HGS 节点](../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-first-hgs-node.png) |
| 3-[配置其他 HGS 节点](guarded-fabric-configure-additional-hgs-nodes.md) | ![步骤3，配置其他 HGS 节点](../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-secondary-hgs-nodes.png) |
| 4-[配置构造 DNS](guarded-fabric-configuring-fabric-dns.md) | ![步骤4，配置 fabric DNS](../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-fabric-dns.png) |
| 5-[验证主机必备项 (密钥) ](guarded-fabric-guarded-host-prerequisites.md#host-key-attestation)并[验证主机必备组件 (TPM) ](guarded-fabric-guarded-host-prerequisites.md#tpm-trusted-attestation) | ![步骤5，验证主机必备项密钥和主机必备组件 TPM](../media/Guarded-Fabric-Shielded-VM/guarded-host-verify.png) |
| 6-[创建主机密钥 (密钥) ](guarded-fabric-create-host-key.md)并[收集主机信息 (TPM) ](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md) | ![步骤6，创建主机密钥并收集主机信息](../media/Guarded-Fabric-Shielded-VM/guarded-host-collect-info-from-hosts.png) |
| 7-[将 HGS 配置为主机信息](guarded-fabric-add-host-information-to-hgs.md) | ![步骤7，将主机信息添加到 HGS](../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-hgs-with-host-info.png) |
| 8-[确认主机可以证明](guarded-fabric-confirm-hosts-can-attest-successfully.md) | ![步骤8，确认主机可以证明](../media/Guarded-Fabric-Shielded-VM/guarded-host-confirm-hosts-attest.png) |
| 9-[配置 VMM (可选) ](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-overview) | ![步骤9，配置 VMM (可选) ](../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-vmm.png) |
| 10-[创建模板磁盘](guarded-fabric-create-a-shielded-vm-template.md) | ![步骤10，创建模板磁盘](../media/Guarded-Fabric-Shielded-VM/guarded-host-create-template-disk.png) |
| 11-[为 VMM 创建 VM 防护帮助程序磁盘 (可选) ](guarded-fabric-vm-shielding-helper-vhd.md) | ![步骤11，为 VMM 创建 VM 防护帮助磁盘](../media/Guarded-Fabric-Shielded-VM/guarded-host-create-helper-disk.png) |
| 12-[设置 Windows Azure Pack (可选) ](guarded-fabric-shielded-vm-windows-azure-pack.md) | ![步骤12，将 Windows Azure Pack (设置) ](../media/Guarded-Fabric-Shielded-VM/guarded-host-windows-azure-pack.png) |
| 13-[创建防护数据文件](guarded-fabric-tenant-creates-shielding-data.md) | ![步骤13，创建防护数据文件](../media/Guarded-Fabric-Shielded-VM/guarded-host-shielding-data-file.png) |
| 14-[使用 Windows Azure Pack 创建受防护的 vm](guarded-fabric-shielded-vm-windows-azure-pack.md) | ![步骤14，使用 Windows Azure Pack 创建受防护的 Vm](../media/Guarded-Fabric-Shielded-VM/guarded-host-shielded-vms.png) |
| 15-[使用 VMM 创建受防护的 vm](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-vms) | ![步骤15，使用 VMM 创建受防护的 Vm](../media/Guarded-Fabric-Shielded-VM/guarded-host-shielded-vms.png) |

## <a name="additional-references"></a>其他参考

- [受保护的结构和受防护的 VM](guarded-fabric-and-shielded-vms-top-node.md)
