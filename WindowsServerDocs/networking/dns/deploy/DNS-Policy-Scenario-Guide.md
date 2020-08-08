---
title: DNS 策略方案指南
description: 本主题是 Windows Server 2016 DNS 策略方案指南的一部分
manager: brianlic
ms.topic: article
ms.assetid: 50fdb08a-bbd8-4107-954a-6699672110ff
ms.author: lizross
author: eross-msft
ms.openlocfilehash: ed28fe6dd472b505d2a39ac55c74c399ef63e068
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87966654"
---
# <a name="dns-policy-scenario-guide"></a>DNS 策略方案指南

>适用于：Windows Server（半年频道）、Windows Server 2016

本指南旨在供 DNS、网络和系统管理员使用。

DNS 策略是 Windows Server 2016 中的 DNS 的一项新功能 &reg; 。 您可以使用本指南了解如何使用 DNS 策略来控制 DNS 服务器如何根据您在策略中定义的不同参数处理名称解析查询。

本指南包含 DNS 策略概述信息，以及特定的 DNS 策略方案，这些方案为你提供了有关如何配置 DNS 服务器行为以实现你的目标的说明，包括针对主要和辅助 DNS 服务器的基于地理位置的流量管理、应用程序高可用性、裂脑 DNS 等。

本指南包含下列各节。

- [DNS 策略概述](DNS-Policies-Overview.md)
- [使用针对基于地理位置的流量管理和主服务器的 DNS 策略](primary-geo-location.md)
- [使用针对基于地理位置的流量管理和主要-辅助部署的 DNS 策略](primary-secondary-geo-location.md)
- [使用针对基于时间的智能 DNS 响应的 DNS 策略](dns-tod-intelligent.md)
- [基于当天使用 Azure 云应用服务器的时间的 DNS 响应](dns-tod-azure-cloud-app-server.md)
- [将 DNS 策略用于裂脑 DNS 部署](split-brain-DNS-deployment.md)
- [在 Active Directory 中对裂脑 DNS 使用 DNS 策略](dns-sb-with-ad.md)
- [使用 DNS 策略对 DNS 查询应用筛选器](apply-filters-on-dns-queries.md)
- [使用 DNS 策略执行应用程序负载平衡](app-lb.md)
- [使用 DNS 策略通过地理位置感知执行应用程序负载平衡](app-lb-geo.md)

