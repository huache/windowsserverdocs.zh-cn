---
author: eross-msft
ms.author: lizross
ms.date: 10/02/2018
ms.prod: windows-server
ms:topic: include
ms.openlocfilehash: f2065acb89af4bed4dc525453bb5a294a4e2c3ef
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80316472"
---
使用动态时，将基于 TCP 端口和 IP 地址的哈希分布出站负载。 动态模式还间重新平衡实时加载，以便给定的出站流可以在团队成员之间来回移动。 另一方面，入站负载以与 Hyper-v 端口相同的方式进行分配。 简而言之，动态模式使用地址哈希和 Hyper-v 端口的最佳特性，并且是性能最高的负载平衡模式。 

