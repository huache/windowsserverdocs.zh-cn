---
title: 受防护的用于租户的 Vm-通过使用 Windows Azure Pack 部署受防护的 VM
ms.topic: article
ms.assetid: 095315e4-c4a7-4b80-91d8-528119b62c4c
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 613082bcc5cfefa0c7abb0011762c3d283ea98aa
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87989993"
---
# <a name="shielded-vms--for-tenants---deploying-a-shielded-vm-by-using-windows-azure-pack"></a>受防护的用于租户的 Vm-通过使用 Windows Azure Pack 部署受防护的 VM

>适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016

如果托管服务提供商支持，则可以使用 Windows Azure Pack 来部署受防护的 VM。

请完成下列步骤：

1. 订阅 Windows Azure Pack 中提供的一个或多个计划。

2. 使用 Windows Azure Pack 创建受防护的 VM。

    [使用受防护的虚拟机](/previous-versions/azure/windows-server-azure-pack/mt720674(v=technet.10))，如以下主题中所述：

   - [ (和](/previous-versions/azure/windows-server-azure-pack/mt720672(v=technet.10))上传防护数据文件，请参阅主题) 中的第二个过程中所述。

     > [!NOTE]
     > 在创建防护数据的过程中，你将下载监护人密钥文件，该文件将是 UTF-8 格式的 XML 文件。 不要将文件更改为 UTF-16。

   - [创建受防护的虚拟机](/previous-versions/azure/windows-server-azure-pack/mt720673(v=technet.10))-通过使用 "**快速创建**"、通过受防护的模板或通过常规模板。

       > [!WARNING]
       > 如果[使用常规模板创建受防护的虚拟机](/previous-versions/azure/windows-server-azure-pack/mt720673(v=technet.10)#Anchor_2)，请务必注意，VM 是以非*屏蔽*方式进行设置的。 这意味着不会对照防护数据文件中的受信任磁盘列表来验证模板磁盘，也不会对用于预配 VM 的防护数据文件中的机密进行验证。 如果防护的模板可用，则最好使用受防护的模板部署受防护的 VM，以便为机密提供端到端保护。

   - [将第2代虚拟机转换为受防护的虚拟机](/previous-versions/azure/windows-server-azure-pack/mt720670(v=technet.10))

       > [!NOTE]
       > 如果将虚拟机转换为受防护的虚拟机，则不会加密现有的检查点和备份。 应尽可能删除旧的检查点，以防止对旧的已解密数据的访问。

## <a name="additional-references"></a>其他参考

- [用于受保护的主机和受防护的 VM 的主机托管服务提供商配置步骤](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
- [受保护的结构和受防护的 VM](guarded-fabric-and-shielded-vms-top-node.md)