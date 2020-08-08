---
author: eross-msft
ms.author: lizross
ms.date: 10/02/2018
ms:topic: include
ms.openlocfilehash: 43a4149d44bd24a7d8b3d68ed9e3c2b68c99e285
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87952815"
---
通过 Hyper-v 端口，Hyper-v 主机上配置的 NIC 团队为 Vm 提供独立 MAC 地址。  Vm MAC 地址或连接到 Hyper-v 交换机的 VM 端口可用于划分 NIC 组成员之间的网络流量。 你不能在具有 Hyper-v 端口负载平衡模式的 Vm 中配置创建的 NIC 组。 请改用地址哈希模式。