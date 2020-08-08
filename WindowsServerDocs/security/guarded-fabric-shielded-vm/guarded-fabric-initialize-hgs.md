---
title: 初始化 HGS
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: e36451c90fd543ea49989e51832ab3104d4137c0
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939588"
---
# <a name="initialize-the-host-guardian-service-hgs"></a> (HGS) 初始化主机保护者服务

>适用于： Windows Server 2019、Windows Server (半年频道) 、Windows Server 2016

初始化 HGS 时，将指定 HGS 用于测量受保护主机的运行状况的模式。 有两个互相排斥的选项。 有关所选模式的背景信息，请参阅[托管商的受保护的构造和受防护的 VM 规划指南](guarded-fabric-planning-for-hosters.md)。

以下主题介绍了每种模式的部署步骤：

- [Tpm 可信证明 (TPM 模式) ](guarded-fabric-initialize-hgs-tpm-mode.md)
- [主机密钥证明 (密钥模式) ](guarded-fabric-initialize-hgs-key-mode.md)
- [管理员信任的证明 (AD 模式) ](guarded-fabric-initialize-hgs-ad-mode.md)

应在物理服务器上执行这些步骤。