---
title: QoS 策略的工作方式
description: 本主题概述了服务质量 (QoS) 策略，该策略允许你使用组策略来确定 Windows Server 2016 中特定应用程序和服务的网络流量带宽的优先级。
ms.topic: article
ms.assetid: 25097cb8-b9b1-41c9-b3c7-3610a032e0d8
manager: brianlic
ms.author: lizross
author: eross-msft
ms.openlocfilehash: fe91bba99000be307ed011cb5636dc49d65c389a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87942527"
---
# <a name="how-qos-policy-works"></a>QoS 策略的工作方式

>适用于：Windows Server（半年频道）、Windows Server 2016

启动或获取更新的用户或计算机配置组策略 QoS 的设置时，将发生以下过程。

1. 组策略引擎从 Active Directory 检索用户或计算机配置组策略设置。

2. 组策略引擎通知 QoS 客户端扩展存在 QoS 策略中的更改。

3. QoS 客户端扩展将 QoS 策略事件通知发送到 QoS 检测模块。

4. QoS 检查模块检索用户或计算机 QoS 策略并将其存储。

当创建新的传输层终结点 \( TCP 连接或 UDP 流量时 \) ，将发生以下过程。

1. TCP/IP 堆栈的传输层组件会通知 QoS 检测模块。

2. QoS 检查模块将传输层终结点的参数与存储的 QoS 策略进行比较。

3. 如果找到匹配项，则 QoS 检查模块会联系 Pacer.sys 来创建流，这是一个包含 DSCP 值的数据结构和匹配的 QoS 策略的流量限制设置。 如果有多个 QoS 策略与传输层终结点的参数匹配，则使用最具体的 QoS 策略。

4. Pacer.sys 存储流，并将与该流相对应的流编号返回到 QoS 检测模块。

5. QoS 检查模块将流编号返回到传输层。

6. 传输层将流编号与传输层终结点一起存储。

如果发送了与使用流号码标记的传输层终结点相对应的数据包，则会发生以下过程。

1. 传输层在内部用流编号来标记数据包。

2. 网络层查询 Pacer.sys 的 DSCP 值对应于数据包的流号。

3. Pacer.sys 返回网络层的 DSCP 值。

4. 网络层将 "IPv4 TOS 字段" 或 "IPv6 通信类" 字段更改为 Pacer.sys 指定的 DSCP 值，对于 IPv4 数据包，将计算最终的 IPv4 标头校验和。

5. 网络层将数据包交给组帧层。

6. 由于数据包已使用流号码进行标记，因此组帧层通过 NDIS 1.x 将数据包交给 Pacer.sys。

7. Pacer.sys 使用数据包的流号来确定是否需要对数据包进行限制，如果是，则将数据包安排为发送。

8. 如果不存在流量限制，则 Pacer.sys 直接对数据包进行操作， \( \) \( 如果 \) 要通过相应的网络适配器传输流量，请立即将流量阻止到 NDIS 1.x。

基于策略的 QoS 的这些过程具有以下优势。

- 检查流量以确定是否应用 QoS 策略是针对每个传输层终结点执行的，而不是按数据包进行。

- 不符合 QoS 策略的流量不会对性能产生任何影响。

- 不需要对应用程序进行修改即可利用基于 DSCP 的差异服务或流量限制。

- QoS 策略可应用到使用 IPsec 保护的流量。

有关本指南的下一个主题，请参阅[QoS 策略体系结构](qos-policy-architecture.md)。

有关本指南的第一个主题，请参阅[Service Quality (QoS) 策略](qos-policy-top.md)。
