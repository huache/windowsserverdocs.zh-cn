---
title: Windows Server 中 SDN 的新增功能
description: 本主题提供有关 Windows Server 1709 的全新软件定义网络功能的信息
manager: grcusanz
ms.prod: windows-server
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: efad919b-e9e7-4a0c-b373-e68a092f93b5
ms.author: anpaul
author: AnirbanPaul
ms.date: 10/02/2018
ms.openlocfilehash: 5c6e90b590af9292b1749acdbdbc143752a1e30a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854390"
---
# <a name="whats-new-in-sdn-for-windows-server-2019"></a>Windows Server 2019 中 SDN 的新增功能

>适用于： Windows Server （半年频道）


|                         **具有**                          |                                                                                                                                                                                         **描述**                                                                                                                                                                                         | **新增/更新** |
|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| [加密网络](vnet-encryption/sdn-vnet-encryption.md) | 虚拟网络加密允许加密虚拟机之间的虚拟网络流量，这些虚拟机在标记为 "已启用加密" 的子网中相互通信。 它还利用虚拟子网上的数据报传输层安全性 (DTLS) 来加密数据包。 DTLS 可以防止能够访问物理网络的任何人进行窃听、篡改和伪造。 |       新建       |
|    [防火墙审核](security/sdn-firewall-auditing.md)    |                                                                                            防火墙审核是 Windows Server 2019 中 SDN 防火墙的新功能。 启用 SDN 防火墙时，将记录已启用日志记录的 SDN 防火墙规则（Acl）处理的任何流。                                                                                            |       新建       |
| [虚拟网络对等](vnet-peering/sdn-vnet-peering.md)  |                                                                                                                      利用虚拟网络对等互连，无缝连接两个虚拟网络。 对等互连后，出于连接目的，虚拟网络显示为一。                                                                                                                      |       新建       |
|           [出口计数](manage/sdn-egress.md)            |                  Windows Server 2019 中的这一新功能使 SDN 能够为出站数据传输提供用量计量。 添加此功能后，网络控制器会按虚拟网络为 SDN 中使用的所有 IP 范围保留一个允许列表，并考虑将未包含在其中一个范围内的目标的任何包绑定到要进行计费的出站数据传输。                   |       新建       |

---



