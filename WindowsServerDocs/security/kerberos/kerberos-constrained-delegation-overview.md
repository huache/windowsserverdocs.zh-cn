---
title: Kerberos Constrained Delegation Overview
description: Windows Server 安全
ms.topic: article
ms.assetid: 51923b0a-0c1a-47b2-93a0-d36f8e295589
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: 2cc0a18b3b6de66f5992eb4584c95696e297e858
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641090"
---
# <a name="kerberos-constrained-delegation-overview"></a>Kerberos Constrained Delegation Overview

>适用于：Windows Server（半年频道）、Windows Server 2016

本概述主题面向 IT 专业人员，介绍了 Windows Server 2012 R2 和 Windows Server 2012 中的 Kerberos 约束委派的新功能。

**功能说明**

在 Windows Server 2003 中引入的 Kerberos 约束委派，为服务所使用的委派提供了一种更安全的形式。 配置了 Kerberos 约束委派后，它限制了指定服务器可代表用户执行的服务。 这需要域管理员权限来为服务配置一个域账户，并把该账户限制到单个域。 在如今的企业中，前端服务的设计并不局限于仅与域中的服务进行集成。

在域管理员配置了服务的早期操作系统中，服务管理员没有有效途径来了解哪些前端服务委派给了其拥有的资源服务。 并且可委派给资源服务的任何前端服务都代表了一个潜在的攻击点。 如果托管前端服务的服务器受到安全威胁，并且它已配置为委派给资源服务，则资源服务也会受到安全威胁。

在 Windows Server 2012 R2 和 Windows Server 2012 中，为服务配置约束委派的能力已从域管理员转移给服务管理员。 这样，后端服务管理员可以允许或拒绝前端服务。

有关 Windows Server 2003 中引入的约束委派的详细信息，请参阅 [Kerberos 协议转换和约束委派](/previous-versions/windows/it-pro/windows-server-2003/cc739587(v=ws.10))。

Kerberos 协议的 Windows Server 2012 R2 和 Windows Server 2012 实现包括专门针对约束委派的扩展。  Service for User to Proxy (S4U2Proxy) 允许服务使用其用户 Kerberos 服务票证从密钥发行中心 (KDC) 获得服务票证，以用于后端服务。 这些扩展允许在可位于另一个域中的后端服务帐户上配置约束委派。 有关这些扩展的详细信息，请参阅 MSDN Library 中的[ \[ MS-SFU \] ： Kerberos 协议扩展：用户服务和约束委派协议规范](https://msdn.microsoft.com/library/cc246071(PROT.13).aspx)。

**实际的应用程序**

约束委派让服务管理员能够通过限制应用程序服务可以代表用户的范围来指定和强制应用程序信任边界。 服务管理员可以配置哪些前端服务账户能委派到其后端服务。

通过支持 Windows Server 2012 R2 和 Windows Server 2012 中跨域的约束委派，可以将前端服务（例如 Microsoft Internet 安全和加速 (ISA) Server、Microsoft Forefront 威胁管理网关、Microsoft Exchange Outlook Web 访问 (OWA) 和 Microsoft SharePoint Server）配置为使用约束委派对其他域中的服务器进行身份验证。 这将通过使用现有的 Kerberos 基础结构来支持跨域的服务解决方案。 域管理员或服务管理员可以管理 Kerberos 约束委派。

## <a name="resource-based-constrained-delegation-across-domains"></a>跨域的基于资源的约束委派

Kerberos 约束委派可以在前端服务与资源服务不在同一域中时用于提供约束委派。 服务管理员能通过指定可以在资源服务账户对象上代表用户的前端服务域账户来配置新委派。

**这一更改增添了什么价值？**

通过支持跨域约束委派，可以将服务配置为使用约束委派（而不是非约束委派）来对其他域中的服务器进行身份验证。 这将通过使用现有的 Kerberos 基础结构来支持跨域的服务解决方案身份验证，而不需要信任委派到任何服务的前端服务。

这还决定了服务器是否应该信任委派的标识的源，从委派的域管理员到资源所有者。

**工作原理的不同之处是什么？**

基础协议中的更改允许跨域约束委派。 Kerberos 协议的 Windows Server 2012 R2 和 Windows Server 2012 实现包括为用户提供服务的扩展，以便 (S4U2Proxy) 协议。 这组 Kerberos 协议扩展允许服务使用其用户 Kerberos 服务票证从密钥发行中心 (KDC) 获得服务票证，以用于后端服务。

有关这些扩展的实现信息，请参阅 MSDN 中的[ \[ MS-SFU \] ： Kerberos 协议扩展：用户服务和约束委派协议规范](https://msdn.microsoft.com/library/cc246071(PROT.10).aspx)。

有关使用与 Service for User (S4U) 扩展相比提早的票证授予票证 (TGT) 的 Kerberos 委派的基础消息队列的详细信息，请参阅 [1.3.3 协议概述](/openspecs/windows_protocols/ms-sfu/1fb9caca-449f-4183-8f7a-1a5fc7e7290a) 部分（“[MS-SFU]：Kerberos 协议扩展：用户服务和约束委派协议规范”）。

**基于资源的约束委派的安全含义**

基于资源的约束委派会将委派控制置于拥有所访问资源的管理员。 它依赖于资源服务的属性，而不是受信任的服务委托。 因此，基于资源的约束委派不能使用以前控制的协议转换的受信任身份验证委托位。 当执行基于资源的约束委派时，KDC 始终允许协议转换，就像设置了位一样。

因为 KDC 不会限制协议转换，所以引入了两个新的已知 Sid，以将此控件授予资源管理员。  这些 Sid 确定是否发生了协议转换，并可与标准访问控制列表结合使用来根据需要授予或限制访问权限。

|SID|说明|
|-------|--------|
|AUTHENTICATION_AUTHORITY_ASSERTED_IDENTITY<br />S-1-18-1|一个 SID，表示根据客户端凭据所有权验证，身份验证颁发机构对客户端的标识进行断言。|
|SERVICE_ASSERTED_IDENTITY<br />S-1-18-2|一个 SID，表示服务对客户端的标识进行断言。|

后端服务可以使用标准 ACL 表达式来确定如何对用户进行身份验证。

**如何配置基于资源的约束委派？**

若要配置资源服务以允许代表用户的前端服务访问，则需要使用 Windows PowerShell cmdlet。

-   若要检索主体列表，请使用 **get-adcomputer**、 **uninstall-adserviceaccount**和 **new-aduser** cmdlet 以及 **Properties PrincipalsAllowedToDelegateToAccount** 参数。

-   若要配置资源服务，请使用**get-adcomputer**、 **uninstall-adserviceaccount**、 **new-aduser**、 **get-adcomputer**、uninstall-adserviceaccount**和**new-aduser **cmdlet，其中**包含**PrincipalsAllowedToDelegateToAccount**参数。

## <a name="software-requirements"></a><a name="BKMK_SOFT"></a>软件要求
基于资源的约束委派只能在运行 Windows Server 2012 R2 和 Windows Server 2012 的域控制器上配置，但可以在混合模式林中应用。

必须将以下修补程序应用到所有运行 windows server 2012 的域控制器，这些域控制器在运行早于 Windows Server 的操作系统的前端域和后端域之间的引用路径上：基于资源的约束委派 KDC_ERR_POLICY 在 (基于 Windows Server 2008 R2 的域控制器的环境中失败 https://support.microsoft.com/en-gb/help/2665790/resource-based-constrained-delegation-kdc-err-policy-failure-in-enviro) 。