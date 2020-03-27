---
title: 增加由 NPS 处理的并发身份验证
description: 本主题提供有关在 Windows Server 2016 中配置网络策略服务器并发身份验证的说明。
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 2d9cdada-0625-41c8-8248-a32259b03e47
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 5397a1de41717dfc65ee0b0582c1289c6a53b33a
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80316298"
---
# <a name="increase-concurrent-authentications-processed-by-nps"></a>增加由 NPS 处理的并发身份验证

>适用于：Windows Server（半年频道）、Windows Server 2016

您可以使用本主题获取有关配置网络策略服务器并发身份验证的说明。

如果在域控制器之外的计算机上安装了网络策略服务器 \(NPS\)，并且 NPS 每秒接收了大量的身份验证请求，则可以通过增加 NPS 和域控制器之间允许的并发身份验证次数，提高 NPS 性能。

为此，必须编辑以下注册表项： 

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters`

添加一个名为 " **MaxConcurrentApi** " 的新值，并为其分配一个介于2到5之间的值。 

>[!CAUTION]
>如果向**MaxConcurrentApi**分配的值过高，则 NPS 可能会在域控制器上施加过量负载。

有关管理 NPS 的详细信息，请参阅[管理网络策略服务器](nps-manage-top.md)。

有关 NPS 的详细信息，请参阅[网络策略服务器（NPS）](nps-top.md)。