---
title: 为 HTTPS 通信配置 HGS
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 4e708b61bd629b5b784926338b1aee122e2ecbee
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87966154"
---
# <a name="configure-hgs-for-https-communications"></a>为 HTTPS 通信配置 HGS

>适用于： Windows Server 2019、Windows Server (半年频道) 、Windows Server 2016

默认情况下，初始化 HGS 服务器时，它会将 IIS 网站配置为仅限 HTTP 通信。
所有与 HGS 传输的敏感材料始终使用消息级加密进行加密，但是，如果你需要更高的安全级别，则还可以通过使用 SSL 证书配置 HGS 来启用 HTTPS。

[!INCLUDE [Configure HTTPS](../../../includes/configure-hgs-for-https.md)]

