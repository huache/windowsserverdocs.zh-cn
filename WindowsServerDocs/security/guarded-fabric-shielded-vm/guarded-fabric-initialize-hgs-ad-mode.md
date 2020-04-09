---
title: 使用管理员信任的证明初始化 HGS
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: b7c0b88071a28953ddda8abb57a805ef119511e0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856670"
---
# <a name="initialize-hgs-using-admin-trusted-attestation"></a>使用管理员信任的证明初始化 HGS

>适用于：Windows Server（半年频道）、Windows Server 2016

>[!IMPORTANT]
>从 Windows Server 2019 开始，已弃用管理受信任的证明（AD 模式）。 对于不可能进行 TPM 证明的环境，请配置[主机密钥证明](guarded-fabric-initialize-hgs-key-mode.md)。 主机密钥证明向 AD 模式提供类似的保障，并更易于设置。 


这些步骤取决于你是在新林中还是在现有堡垒林中初始化 HGS：

1. [在新林中初始化 HGS 群集（默认值）](guarded-fabric-initialize-hgs-ad-mode-default.md)

   -或者-

   [初始化现有堡垒林中的 HGS 群集](guarded-fabric-initialize-hgs-ad-mode-bastion.md)

2. [在 fabric 域中配置 DNS 转发](guarded-fabric-configuring-fabric-dns.md)

3. [在 HGS 域中配置 DNS 转发和单向信任](guarded-fabric-configure-dns-forwarding-and-trust.md)



