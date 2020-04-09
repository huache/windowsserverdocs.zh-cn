---
title: 为 HTTPS 通信配置 HGS
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: de57a4026a33561760ad36fd78d732352b3aa340
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856840"
---
# <a name="configure-hgs-for-https-communications"></a>为 HTTPS 通信配置 HGS

>适用于： Windows Server 2019、Windows Server （半年频道）、Windows Server 2016

默认情况下，初始化 HGS 服务器时，它会将 IIS 网站配置为仅限 HTTP 通信。
所有与 HGS 传输的敏感材料始终使用消息级加密进行加密，但是，如果你需要更高的安全级别，则还可以通过使用 SSL 证书配置 HGS 来启用 HTTPS。

[!INCLUDE [Configure HTTPS](../../../includes/configure-hgs-for-https.md)] 

