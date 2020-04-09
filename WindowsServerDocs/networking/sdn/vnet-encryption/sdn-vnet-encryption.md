---
title: 虚拟网络加密
description: 虚拟网络加密允许加密虚拟机之间的虚拟网络流量，这些虚拟机在标记为 "已启用加密" 的子网中相互通信。
manager: grcusanz
ms.prod: windows-server
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: 7da0f509-7b02-4a0f-90fb-d97c83a2bc4e
ms.author: anpaul
author: AnirbanPaul
ms.date: 08/08/2018
ms.openlocfilehash: 63daea02ec00593504383ce071d3f9454a37956b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853570"
---
# <a name="virtual-network-encryption"></a>虚拟网络加密

>适用于： Windows Server

虚拟网络加密允许加密虚拟机之间的虚拟网络流量，这些虚拟机在标记为 "已启用加密" 的子网中相互通信。 它还利用虚拟子网上的数据报传输层安全性 (DTLS) 来加密数据包。 DTLS 可以防止能够访问物理网络的任何人进行窃听、篡改和伪造。

虚拟网络加密要求：
- 在每个启用了 SDN 的 Hyper-v 主机上安装的加密证书。
- 网络控制器中引用该证书的指纹的凭据对象。
- 每个虚拟网络上的配置都包含需要加密的子网。

在子网中启用加密后，该子网中的所有网络流量都将自动进行加密，以及任何可能发生的应用程序级加密。  跨子网的流量（即使标记为已加密）将自动以未加密的方式发送。 跨虚拟网络边界的任何流量也会以未加密状态发送。

>[!TIP]
>如果你必须将应用程序限制为仅在加密的子网上进行通信，则只能使用访问控制列表（Acl）来允许当前子网中的通信。 有关详细信息，请参阅[使用访问控制列表（acl）管理数据中心网络流量流](https://docs.microsoft.com/windows-server/networking/sdn/manage/use-acls-for-traffic-flow)。

### <a name="next-steps"></a>后续步骤

[为虚拟网络配置加密](https://docs.microsoft.com/windows-server/networking/sdn/vnet-encryption/sdn-config-vnet-encryption)

