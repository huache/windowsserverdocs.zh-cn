---
title: 使用受 TPM 信任的证明初始化 HGS
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: b8ceebe63a586ec95b502dfea12f99d174549448
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856610"
---
# <a name="initialize-hgs-using-tpm-trusted-attestation"></a>使用受 TPM 信任的证明初始化 HGS

>适用于： Windows Server 2019、Windows Server （半年频道）、Windows Server 2016

这些步骤取决于你是在新林中还是在现有堡垒林中初始化 HGS：

1. [在新林中初始化 HGS 群集（默认值）](guarded-fabric-initialize-hgs-tpm-mode-default.md)

   -或者-

   [初始化现有堡垒林中的 HGS 群集](guarded-fabric-initialize-hgs-tpm-mode-bastion.md)

2. [安装受信任的 TPM 根证书](guarded-fabric-install-trusted-tpm-root-certificates.md)   
3. [配置构造 DNS](guarded-fabric-configuring-fabric-dns.md)

