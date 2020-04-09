---
title: 为受保护的主机配置构造 DNS （AD）
ms.prod: windows-server
ms.topic: article
ms.assetid: 074b6d09-f16e-49bf-b88a-377139d35067
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 5b7deafb49083ad55d5a49d1ad3c5e063e91483f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856820"
---
# <a name="configure-the-fabric-dns-for-guarded-hosts"></a>为受保护的主机配置构造 DNS

>适用于：Windows Server 2016


>[!IMPORTANT]
>从 Windows Server 2019 开始，AD 模式已弃用。 对于不可能进行 TPM 证明的环境，请配置[主机密钥证明](guarded-fabric-initialize-hgs-key-mode.md)。 主机密钥证明向 AD 模式提供类似的保障，并更易于设置。 

构造管理员需要配置构造 DNS 所采用的结构，以允许受保护的主机解析 HGS 群集。 Hgs 管理员必须已[设置](/WindowsServerDocs/virtualization/guarded-fabric-shielded-vm/guarded-fabric-setting-up-the-host-guardian-service-hgs.md)hgs 群集。



[!INCLUDE [Configure fabric DNS](../../../includes/guarded-fabric-configure-fabric-dns.md)] 


## <a name="next-step"></a>下一步

> [!div class="nextstepaction"]
> [配置 HGS DNS 和单向信任](guarded-fabric-configure-dns-forwarding-and-trust.md)
