---
ms.assetid: f052dfcd-dace-4485-8d0a-cc7df5cf3751
title: Active Directory 域服务概述
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 8087a6c7698952793546d6266a6a112bb810ac70
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88940327"
---
# <a name="active-directory-domain-services-overview"></a>Active Directory 域服务概述

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012


目录是存储有关网络上对象的信息的层次结构。 目录服务（例如 Active Directory 域服务 (AD DS) ）提供了存储目录数据以及使此数据可供网络用户和管理员使用的方法。 例如，AD DS 存储有关用户帐户的信息，如名称、密码、电话号码等，并使同一网络上的其他授权用户可以访问此信息。

Active Directory 存储有关网络上对象的信息，并让管理员和用户可以更容易地使用这些信息。 Active Directory 使用结构化数据存储作为目录信息的逻辑层次组织的基础。

此数据存储（也称为目录）包含 Active Directory 对象的相关信息。 这些对象通常包含共享资源，如服务器、卷、打印机、网络用户和计算机帐户。 有关 Active Directory 数据存储的详细信息，请参阅 [目录数据存储](/previous-versions/windows/it-pro/windows-server-2003/cc736627(v=ws.10))。

通过登录身份验证和对目录中对象的访问控制，安全与 Active Directory 集成。 通过单一网络登录，管理员可以管理其整个网络中的目录数据和组织，授权网络用户可以访问网络上任何位置的资源。 基于策略的管理简化了即使最复杂的网络的管理。 有关 Active Directory 安全的详细信息，请参阅 [安全性概述](../../plan/security-best-practices/best-practices-for-securing-active-directory.md)。

Active Directory 还包括：
* 一组规则，即 **架构**，定义目录中包含的对象和属性的类别、这些对象的实例的约束和限制及其名称的格式。 有关架构的详细信息，请参阅架构。


* 包含有关目录中每个对象的信息的 **全局编录** 。 这允许用户和管理员查找目录信息，而不考虑目录中的哪个域实际包含数据。 有关全局编录的详细信息，请参阅全局编录的角色。


* 一 **种查询和索引机制**，以便对象及其属性可由网络用户或应用程序发布和查找。 有关查询目录的详细信息，请参阅查找目录信息。


* 跨网络分发目录数据的 **复制服务** 。 域中的所有域控制器均参与复制，并包含其域的所有目录信息的完整副本。 对目录数据的任何更改均复制到域中的所有域控制器。 有关 Active Directory 复制的详细信息，请参阅复制概述。

## <a name="understanding-active-directory"></a>了解 Active Directory
 本部分提供了指向核心 Active Directory 概念的链接：

* [Active Directory 结构和存储技术](/previous-versions/windows/it-pro/windows-server-2003/cc759186(v=ws.10))
* [域控制器角色](/previous-versions/windows/it-pro/windows-server-2003/cc786438(v=ws.10))
* [Active Directory 架构](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771796(v=ws.10))
* [了解信任](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771568(v=ws.10))
* [Active Directory 复制技术](/previous-versions/windows/it-pro/windows-server-2003/cc776877(v=ws.10))
* [Active Directory 搜索和发布技术](/previous-versions/windows/it-pro/windows-server-2003/cc775686(v=ws.10))
* [与 DNS 和组策略互操作](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd197486(v=ws.10))
* [了解架构](/previous-versions/windows/it-pro/windows-server-2003/cc759402(v=ws.10))

有关 Active Directory 概念的详细列表，请参阅 [了解 Active Directory](/previous-versions/windows/it-pro/windows-server-2003/cc781408(v=ws.10))。
