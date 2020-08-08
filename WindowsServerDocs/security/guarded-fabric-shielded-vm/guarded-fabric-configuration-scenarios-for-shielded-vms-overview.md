---
title: 部署受防护的虚拟机
ms.topic: article
ms.assetid: 5d1a06c9-24e1-4e14-9c9a-efb2adbfeddd
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 0eed5d3166410cd006469eaac97ff152dfc8304e
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87971344"
---
# <a name="deploy-shielded-vms"></a>部署受防护的虚拟机


>适用于： Windows Server 2019、Windows Server (半年频道) 、Windows Server 2016

以下主题介绍了租户如何使用受防护的 Vm。

1.  (可选) [创建 Windows 模板磁盘](guarded-fabric-create-a-shielded-vm-template.md)或[创建 Linux 模板磁盘](guarded-fabric-create-a-linux-shielded-vm-template.md)。 模板磁盘可由租户或托管服务提供商创建。

2.  (可选) [将现有 WINDOWS VM 转换为受防护的 vm](guarded-fabric-vm-shielding-helper-vhd.md)。

3. [创建屏蔽数据来定义受防护的 VM](guarded-fabric-tenant-creates-shielding-data.md)。

    有关防护数据文件的说明和关系图，请参阅[什么是防护数据？什么是必需的？](guarded-fabric-and-shielded-vms.md#what-is-shielding-data-and-why-is-it-necessary)

    有关创建要包含在受防护数据文件中的应答文件的信息，请参阅[受防护的 vm-通过使用 ShieldingDataAnswerFile 函数生成答案文件](guarded-fabric-sample-unattend-xml-file.md)。

4. 创建受防护的 VM：

    - 使用**Windows Azure Pack**：[使用 Windows Azure Pack 部署受防护的 VM](guarded-fabric-shielded-vm-windows-azure-pack.md)

    - 使用**Virtual Machine Manager**：[使用 Virtual Machine Manager 部署受防护的 VM](guarded-fabric-tenant-deploys-shielded-vm-using-vmm.md)

## <a name="next-step"></a>后续步骤

> [!div class="nextstepaction"]
> [创建受防护的 VM 模板](guarded-fabric-create-a-shielded-vm-template.md)

## <a name="additional-references"></a>其他参考

- [受保护的结构和受防护的 VM](guarded-fabric-and-shielded-vms-top-node.md)
