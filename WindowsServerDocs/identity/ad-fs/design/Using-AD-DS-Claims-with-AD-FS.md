---
ms.assetid: 460792e4-9f1d-4e7b-b6b2-53e057f839df
title: AD FS 部署拓扑注意事项
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3086de9dc34f555d5f6056716ab9572b980f1962
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858750"
---
# <a name="using-ad-ds-claims-with-ad-fs"></a>将 AD DS 声明用于 AD FS
  
  
可以通过使用 Active Directory 域服务 \(AD DS\)\-颁发的用户和设备声明与 Active Directory 联合身份验证服务 \(AD FS\)，为联合应用程序启用更丰富的访问控制。  
  
## <a name="about-dynamic-access-control"></a>关于动态访问控制  
在 Windows Server&reg; 2012 中，动态访问控制功能使组织能够根据用户声明 \(提供对文件的访问权限，这些声明由用户帐户属性提供，\) 和设备声明 \(，它们源自\) Active Directory 域服务 \(AD DS\)颁发的计算机帐户属性。 AD DS 颁发的声明通过 Kerberos 身份验证协议集成到 Windows 集成身份验证。  
  
有关动态访问控制的详细信息，请参阅[动态访问控制内容路线图](../../solution-guides/Dynamic-Access-Control--Scenario-Overview.md#BKMK_APP)。  
  
### <a name="whats-new-in-ad-fs"></a>AD FS 中有哪些新功能？  
作为动态访问控制方案的扩展，现在可以在 Windows Server 2012 中 AD FS：  
  
-   除了 AD DS 中的用户帐户属性以外，还可以访问计算机帐户属性。 在以前版本的 AD FS 中，联合身份验证服务根本无法从 AD DS 访问计算机帐户属性。  
  
-   使用驻留在 Kerberos 身份验证票证中 AD DS 颁发的用户或设备声明。 在以前版本的 AD FS 中，声明引擎能够从 Kerberos\) \(Sid，但无法读取 Kerberos 票证中包含的任何声明信息。  
  
-   将 AD DS 颁发的用户或设备声明转换为 SAML 令牌，这些令牌依赖于应用程序可用于执行更丰富的访问控制。  
  
## <a name="benefits-of-using-ad-ds-claims-with-ad-fs"></a>将 AD DS 声明与 AD FS 结合使用的好处  
这些 AD DS 颁发的声明可以插入 Kerberos 身份验证票证并与 AD FS 一起使用，以提供以下优势：  
  
-   如果组织需要更丰富的访问控制策略，则可以通过使用基于为给定用户或计算机帐户 AD DS 中存储的属性值 AD DS 颁发的声明，来\-对应用程序和资源的支持。 这可以帮助管理员减少与创建和管理相关的额外开销：  
  
    -   AD DS 安全组，该安全组将用于控制对可通过 Windows 集成身份验证访问的应用程序和资源的访问。  
  
    -   否则，林信任将用于控制对业务\-的访问，以\-Business \(B2B\) \/ 可访问 Internet 的应用程序和资源。  
  
-   组织现在可以根据存储在 AD DS 中的特定计算机帐户属性值，阻止客户端计算机对网络资源进行未经授权的访问 \(例如，计算机的 DNS 名称是否\) 与资源的访问控制策略匹配 \(例如，已使用声明\) 的文件服务器或信赖方策略 \(例如，声明\-感知 Web 应用程序\)。 这可以帮助管理员为以下资源或应用程序设置更精细的访问控制策略：  
  
    -   仅可通过 Windows 集成身份验证访问。  
  
    -   通过 AD FS 身份验证机制可访问 Internet。 AD FS 可用于将 AD DS 颁发的设备声明转换为可以封装到 SAML 令牌中的 AD FS 声明，可供可通过 Internet 访问的资源或信赖方应用程序使用。  
  
## <a name="differences-between-ad-ds-and-ad-fs-issued-claims"></a>AD DS 和 AD FS 颁发的声明之间的差异  
有两个不同的因素需要了解 AD DS 与 AD FS 颁发的声明。 这些差异包括：  
  
-   AD DS 只能发出在 Kerberos 票证中封装的声明，而不是 SAML 令牌。 有关 AD DS 如何发出声明的详细信息，请参阅[动态访问控制内容路线图](../../solution-guides/Dynamic-Access-Control--Scenario-Overview.md#BKMK_APP)。  
  
-   AD FS 只能发出封装在 SAML 令牌中的声明，而不是 Kerberos 票证。 有关 AD FS 如何发出声明的详细信息，请参阅[声明引擎的角色](../../ad-fs/technical-reference/The-Role-of-the-Claims-Engine.md)。  
  
## <a name="how-ad-ds-issued-claims-work-with-ad-fs"></a>AD DS 颁发的声明与 AD FS 工作的方式  
AD DS 颁发的声明可以与 AD FS 一起使用，以便直接从用户的身份验证上下文访问用户和设备声明，而不是对 Active Directory 进行单独的 LDAP 调用。 下图和相应的步骤讨论了此过程的工作原理，以便为动态访问控制方案启用基于声明\-的访问控制。  
  
![使用声明](media/UsingADDSClaimswithADFS.gif)  
  
1.  AD DS 管理员使用 Active Directory 管理中心控制台或 PowerShell cmdlet 来启用 AD DS 架构中的特定声明类型对象。  
  
2.  AD FS 管理员使用 AD FS 管理控制台来创建和配置声明提供者和信赖方信任，并通过 "通过" 或\-"转换声明规则"。  
  
3.  Windows 客户端尝试访问网络。 在 Kerberos 身份验证过程中，客户端会提供其用户和计算机票证\-向域控制器授予票证 \(TGT\) 并不包含任何声明。 然后，域控制器会在 AD DS 中查找已启用的声明类型，并在返回的 Kerberos 票证中包含任何生成的声明。  
  
4.  当用户\/客户端尝试访问已纳入 acl 需要声明的文件资源时，他们可以访问该资源，因为从 Kerberos 呈现的复合 ID 具有这些声明。  
  
5.  当相同的客户端尝试访问为 AD FS 身份验证配置的网站或 Web 应用程序时，会将用户重定向到配置为使用 Windows 集成身份验证的 AD FS 联合服务器。 客户端使用 Kerberos 将请求发送到域控制器。 域控制器颁发包含请求的声明的 Kerberos 票证，客户端可以向联合服务器提供该票证。  
  
6.  根据在管理员以前配置的声明提供程序和信赖方信任上配置声明规则的方式，AD FS 从 Kerberos 票证中读取声明，并将其包含在它为客户端颁发的 SAML 令牌中。  
  
7.  客户端接收包含正确声明的 SAML 令牌，然后重定向到该网站。  
  
有关如何创建 AD DS 颁发的声明来处理 AD FS 所需的声明规则的详细信息，请参阅[创建转换传入声明的规则](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)。  
  
## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
