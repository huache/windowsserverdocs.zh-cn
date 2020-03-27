---
title: Windows Internet 名称服务 (WINS)
description: 本主题提供有关使 WINS 退役并在网络上使用 DNS 进行名称解析服务的信息。
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 32eabe7d-1130-4001-a79a-8ddb31993e5b
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 54e3f69500ccb3dbf6b2dfe47f6dd035e0a20511
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315167"
---
#  <a name="windows-internet-name-service-wins"></a>Windows Internet 名称服务 (WINS)

>适用于：Windows Server（半年频道）、Windows Server 2016

Windows Internet 名称服务 (WINS) 是传统的计算机名称注册和解析访问服务，该服务将计算机 NetBIOS 名称映射到 IP 地址。

如果你的网络上还没有部署 WINS，请不要部署 WINS，而是部署域名系统 \(DNS\)。 DNS 还提供计算机名称注册和解析服务，并在 WINS 上包含许多其他权益，如与 Active Directory 域服务的集成。

有关详细信息，请参阅[域名系统（DNS）](https://docs.microsoft.com/windows-server/networking/dns/dns-top)

如果已在网络上部署了 WINS，则建议部署 DNS，并使 WINS 停止。
