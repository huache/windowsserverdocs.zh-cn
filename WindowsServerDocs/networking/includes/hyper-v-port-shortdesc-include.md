---
author: eross-msft
ms.author: lizross
ms.date: 10/02/2018
ms.prod: windows-server
ms:topic: include
ms.openlocfilehash: 47a91c86ac75aedf532289055c94b34899fa01df
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80316495"
---
通过 Hyper-v 端口，Hyper-v 主机上配置的 NIC 团队为 Vm 提供独立 MAC 地址。  Vm MAC 地址或连接到 Hyper-v 交换机的 VM 端口可用于划分 NIC 组成员之间的网络流量。 你不能在具有 Hyper-v 端口负载平衡模式的 Vm 中配置创建的 NIC 组。 请改用地址哈希模式。 