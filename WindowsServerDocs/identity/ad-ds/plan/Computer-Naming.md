---
ms.assetid: f7002265-60fa-40b8-9dd7-4bf131d9320a
title: 计算机命名
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 37f877b3165f5de31c8a26ae4000b8064362fa17
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87947845"
---
# <a name="computer-naming"></a>计算机命名

> 适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

当运行 Windows 2000、Windows XP、Windows Server 2003、Windows Server 2008 或 Windows Vista 操作系统的计算机加入域时，默认情况下，计算机会为自己分配一个名称。 它自己分配的名称由计算机的主机名组成 (即，"系统属性" 中的 "计算机名称") 和 "域名系统" (DNS) 计算机加入的 Active Directory 域的名称 (即 "系统属性") 中的 "主 DNS 后缀"。 主机名和域名的 DNS 名称的串联称为完全限定域名 (FQDN) 。 例如，如果主机名为 Server1 的计算机加入域 corp.contoso.com，则计算机的 FQDN 为 server1.corp.contoso.com。

如果计算机已有一个静态输入到 DNS 区域或通过集成 DNS/动态主机配置协议注册 (DHCP) 服务器服务，则计算机的 FQDN 与先前注册的名称不同。 计算机可以通过任一名称引用。

有关 Active Directory 域服务 (AD DS) 中的命名约定的详细信息，请参阅[Active Directory 中的计算机、域、站点和 ou 的命名约定](https://support.microsoft.com/help/909264/)。
