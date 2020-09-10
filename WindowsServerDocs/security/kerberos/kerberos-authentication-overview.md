---
title: Kerberos Authentication Overview
description: Windows Server 安全
ms.topic: article
ms.assetid: 646c6309-e865-4be2-b415-44dd125af5c2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: e01085558750b601186e8134cd81c09a3e644414
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639784"
---
# <a name="kerberos-authentication-overview"></a>Kerberos Authentication Overview

>适用于：Windows Server（半年频道）、Windows Server 2016

Kerberos 是一种身份验证协议，用于验证用户或主机的标识。 本主题包含有关 Windows Server 2012 和 Windows 8 中的 Kerberos 身份验证的信息。

## <a name="feature-description"></a><a name="BKMK_OVER"></a>功能说明
Windows Server 操作系统可实现 Kerberos 版本 5 身份验证协议和对公钥身份验证的扩展，用于传输授权数据和委派。 Kerberos 身份验证客户端作为安全支持提供程序 \( SSP 实现 \) ，并且可通过安全支持提供程序接口 SSPI 进行访问 \( \) 。 初始用户身份验证与 Winlogon 单一登录 \- 体系结构集成。

Kerberos 密钥发行中心 \( KDC \) 与域控制器上运行的其他 Windows Server 安全服务相集成。 KDC 使用域的 Active Directory 域服务数据库作为其安全帐户数据库。 Active Directory 域服务是域或林中的默认 Kerberos 实现所必需的。

## <a name="practical-applications"></a><a name="kerb_tr_Kerb_Benefits"></a>实际的应用程序
使用 Kerberos 进行基于域的 \- 身份验证的好处包括：

-   **委托身份验证。**

    在代表客户端访问资源时，在 Windows 操作系统上运行的服务可以模拟客户端计算机。 通常，服务通过访问本地计算机上的资源为客户端完成工作。 当客户端计算机向服务进行身份验证时，NTLM 和 Kerberos 协议都可以提供服务在本地模拟客户端计算机所需的授权信息。 但是，某些分布式应用程序的设计使前端 \- 服务在连接到其他计算机上的后端服务时，必须使用客户端计算机的标识 \- 。 Kerberos 身份验证支持一种委派机制，使服务在连接到其他服务时可以代表其客户端进行操作。

-   **单一登录。**

    在域或林中使用 Kerberos 身份验证将允许用户或服务访问管理员允许访问的资源，而无需多次请求凭据。 在通过 Winlogon 第一次登录域之后，Kerberos 将在每次尝试访问资源时管理整个林中的凭据。

-   **互操作性。**

    Microsoft 对 Kerberos V5 协议的实现基于标准 \- 跟踪规范，建议使用 Internet 工程任务组 \( IETF \) 。 因此，在 Windows 操作系统中，Kerberos 协议有助于实现与使用 Kerberos 协议进行身份验证的其他网络之间的互操作性。 此外，Microsoft 发布了有关实现 Kerberos 协议的 Windows 协议文档。 该文档包含 Microsoft 实现 Kerberos 协议的技术要求、限制、依赖项和 \- 特定于 Windows 的协议行为。

-   **对服务器更高效的身份验证。**

    在 Kerberos 出现之前，可以使用 NTLM 身份验证，它要求应用程序服务器必须连接到域控制器，以便验证每个客户端计算机或服务的身份。 使用 Kerberos 协议时，可续订会话票证会替代 pass \- 通过身份验证。 服务器不需要使用域控制器， \( 除非它需要验证特权属性证书 \( PAC \) \) 。 服务器可以通过检查客户端出示的凭据来验证客户端计算机的身份。 客户端计算机在获得一次特定服务器的凭据后，即可在整个网络登录会话期间重复使用这些凭据。

-   **相互身份验证。**

    通过使用 Kerberos 协议，网络连接两端的每一方可验证另一方所宣称的身份。 NTLM 不允许客户端验证服务器的身份，也不允许一个服务器验证另一个服务器的身份。 NTLM 身份验证旨在用于服务器假定为真的网络环境。 Kerberos 协议不进行此假设。

## <a name="see-also"></a>另请参阅
[Windows 身份验证概述](../windows-authentication/windows-authentication-overview.md)


