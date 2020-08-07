---
ms.assetid: c32606b4-2ee2-4df3-a704-8ac6723e188f
title: DNS 和 AD DS
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/08/2018
ms.topic: article
ms.openlocfilehash: f531ffc8226fae9f515882e99da4620badc08611
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87947706"
---
# <a name="dns-and-ad-ds"></a>DNS 和 AD DS

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Active Directory 域服务 (AD DS) 使用域名系统 (DNS) 名称解析服务，使客户端能够查找域控制器和托管目录服务以相互通信的域控制器。

AD DS 可以轻松地将 Active Directory 命名空间集成到现有的 DNS 命名空间中。 Active Directory 集成的 DNS 区域等功能使你可以更轻松地部署 DNS，因为无需设置辅助区域，然后配置区域传输。

有关 DNS 如何支持 AD DS 的信息，请参阅[Active Directory 技术参考的 Dns 支持](/previous-versions/windows/it-pro/windows-server-2003/cc781627(v=ws.10))部分。

> [!NOTE]
> 如果实现了一个不连续的命名空间，其中 AD DS 域名不同于客户端使用的主 DNS 后缀，则与 DNS 的 AD DS 集成更为复杂。 有关详细信息，请参阅非[连续命名空间](Disjoint-Namespace.md)。

## <a name="in-this-section"></a>本节内容

- [域控制器位置](Domain-Controller-Location.md)
- [Active Directory 集成 DNS 区域](Active-Directory-Integrated-DNS-Zones.md)
- [计算机命名](Computer-Naming.md)
- [不连续的命名空间](Disjoint-Namespace.md)
