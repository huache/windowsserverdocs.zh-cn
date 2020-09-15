---
title: DHCP 故障排除通用指南
description: 此 artilce 介绍了排除 DHCP 故障的一般指导。
manager: dcscontentpm
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: e5550654beb0f303be946358c171f3a1b197ea40
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078644"
---
# <a name="general-guidance-to-troubleshoot-dhcp"></a>DHCP 故障排除通用指南

在开始进行故障排除之前，请检查以下各项。 这可以帮助你找到问题的根本原因。

## <a name="checklist"></a>清单

  - 何时开始出现问题？

  - 是否有任何错误消息？

  - DHCP 服务器先前是否正常工作，或者它是否永不工作？
    如果先前工作正常，则在问题开始之前会发生任何更改。 例如，是否安装了更新？ 对基础结构进行了更改？

  - 问题是否持久？ 如果它是间歇性的，那么最后一次发生的时间是什么？

  - 对于所有客户端，还是仅针对特定客户端（例如单范围子网）发生了地址租约故障？

  - 是否存在与 DHCP 服务器位于同一网络子网上的任何客户端？

  - 如果客户端位于同一网络子网中，是否可以获得 IP 地址？

  - 如果客户端不在同一网络子网上，路由器或 VLAN 交换机是否已正确配置为具有 DHCP 中继代理 (也称为 IP 帮助程序) ？

  - DHCP 服务器是独立的还是已配置为实现高可用性，如拆分作用域或 DHCP 故障转移？

  - 在中间设备上检查是否存在可能导致问题的功能，如 VRRP/HSRP、动态 ARP 检查或 DHCP 侦听。
