---
ms.assetid: 8e7015bc-c489-4ec7-8b6e-3ece90f72317
title: 配置身份验证策略
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: ef38b0280a5753b0995e85d0809de6b632fa3afc
ms.sourcegitcommit: 06ae7c34c648538e15c4d9fe330668e7df32fbba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78371255"
---
# <a name="configure-authentication-policies"></a>配置身份验证策略

在 AD FS 中，在 Windows Server 2012 R2 中，访问控制和身份验证机制都具有多个因素，包括用户、设备、位置和身份验证数据。 利用这些增强功能，你可以通过用户界面或通过 Windows PowerShell，通过多\-因素访问控制和\-多个基于用户标识或组成员身份、网络位置、已加入工作区\-的设备数据，以及当执行多重\-因素身份验证 \(MFA\) 时，通过多个基于用户标识或组成员身份、网络位置和身份验证状态 AD FS\-安全的应用程序  

有关在 Windows Server 2012 R2 中 Active Directory 联合身份验证服务 \(AD FS\) 中的 MFA 和多个\-因素访问控制的详细信息，请参阅以下主题：  


-   [跨公司应用程序从任一设备加入工作区以实现 SSO 和无缝第二重身份验证](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)

-   [使用条件访问控制管理风险](../../ad-fs/operations/Manage-Risk-with-Conditional-Access-Control.md)

-   [使用适用于敏感应用程序的附加多重身份验证管理风险](../../ad-fs/operations/Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)

## <a name="configure-authentication-policies-via-the-ad-fs-management-snap-in"></a>通过中的 AD FS 管理 "管理单元\-配置身份验证策略  
本地计算机上的 **Administrators** 中的成员身份或等效身份是完成这些过程所需的最低要求。  可在[本地默认组和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中查看有关使用适合的帐户和组成员身份的详细信息。   

在 AD FS 中，在 Windows Server 2012 R2 中，可以在适用于所有由 AD FS 保护的应用程序和服务的全局范围内指定一个身份验证策略。 你还可以为依赖于参与方信任并受 AD FS 保护的特定应用程序和服务设置身份验证策略。 为每个信赖方信任的特定应用程序指定身份验证策略不会覆盖全局身份验证策略。 如果全局或按信赖方信任身份验证策略需要 MFA，则当用户尝试向此信赖方信任进行身份验证时，将触发 MFA。 全局身份验证策略是针对没有特定配置的身份验证策略的应用程序和服务的信赖方信任的回退。 

## <a name="to-configure-primary-authentication-globally-in-windows-server-2012-r2"></a>在 Windows Server 2012 R2 中全局配置主要身份验证 

1.  在服务器管理器中，单击 "**工具**"，然后选择 " **AD FS 管理**"。  

2.  在 AD FS snap\-中，单击 "**身份验证策略**"。  

3.  在 "**主要身份验证**" 部分中，单击 "**全局设置**" 旁边的 "**编辑**"。 你还可以右键\-单击 "**身份验证策略**"，然后选择 "**编辑全局主要身份验证**"，或在 "**操作**" 窗格下，选择 "**编辑全局主要身份验证**"。  
![身份验证策略](media/Configure-Authentication-Policies/authpolicy1.png)

4.  在 "**编辑全局身份验证策略**" 窗口中的 "**主要**" 选项卡上，可以将以下设置配置为全局身份验证策略的一部分：  

    -   要用于主要身份验证的身份验证方法。 可以在**Extranet**和**Intranet**下选择可用的身份验证方法。  

    -   通过 "**启用设备身份验证**" 复选框进行设备身份验证。 有关详细信息，请参阅 [Join to Workplace from Any Device for SSO and Seamless Second Factor Authentication Across Company Applications](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)。  
![身份验证策略](media/Configure-Authentication-Policies/authpolicy2.png)  

## <a name="to-configure-primary-authentication-per-relying-party-trust"></a>配置按信赖方信任的主要身份验证  

1.  在服务器管理器中，单击 "**工具**"，然后选择 " **AD FS 管理**"。  

2.  在 AD FS snap\-中，单击 "**按信赖方信任**\\**身份验证策略**"，然后单击要为其配置身份验证策略的信赖方信任。  

3.  无论是右键\-单击要为其配置身份验证策略的信赖方信任，然后选择 "**编辑自定义主要身份验证**"，或在 "**操作**" 窗格下，选择 "**编辑自定义主要身份验证**"。  
![身份验证策略](media/Configure-Authentication-Policies/authpolicy5.png)   

4.  在 "**编辑身份验证策略" < 信赖方\_参与方\_信任\_名称 >** "窗口的"**主要**"选项卡下，可将以下设置配置为**按信赖方信任**身份验证策略的一部分：  

    -   每次通过用户在每次登录时都需要提供其凭据的用户在**每次登录时都需要提供其凭据\-** 复选框中的\-。  
![身份验证策略](media/Configure-Authentication-Policies/authpolicy6.png) 

## <a name="to-configure-multi-factor-authentication-globally"></a>全局配置多重身份验证  

1.  在服务器管理器中，单击 "**工具**"，然后选择 " **AD FS 管理**"。  

2.  在 AD FS snap\-中，单击 "**身份验证策略**"。  

3.  在 "**多\-因素身份验证**" 部分中，单击 "**全局设置**" 旁边的 "**编辑**"。 你还可以右键\-单击 "**身份验证策略**"，然后选择 "**编辑全局多\-因素身份验证**"，或在 "**操作**" 窗格下，选择 "**编辑全局多\-因素身份验证**"。  
![身份验证策略](media/Configure-Authentication-Policies/authpolicy8.png)   

4.  在 "**编辑全局身份验证策略**" 窗口中的 "**多\-系数**" 选项卡下，可将以下设置配置为全局多重\-因素身份验证策略的一部分：  

    -   通过 "**用户\/组**"、"**设备**" 和 "**位置**" 部分下的可用选项进行 MFA 的设置或条件。  

    -   若要为这些设置启用 MFA，必须至少选择一个附加身份验证方法。 **证书身份验证**是默认的可用选项。 你还可以配置其他自定义附加身份验证方法，例如 Windows Azure Active Authentication。 有关详细信息，请参阅[演练指南：利用适用于敏感应用程序的附加多重身份验证管理风险](../../ad-fs/operations/Walkthrough-Guide--Manage-Risk-with-Additional-Multi-Factor-Authentication-for-Sensitive-Applications.md)。  

> [!WARNING]  
> 你只能在全局范围内配置其他身份验证方法。  
![身份验证策略](media/Configure-Authentication-Policies/authpolicy9.png)  

## <a name="to-configure-multi-factor-authentication-per-relying-party-trust"></a>配置每个信赖方信任的多\-因素身份验证  

1.  在服务器管理器中，单击 "**工具**"，然后选择 " **AD FS 管理**"。  

2.  在 AD FS snap\-中，单击 "**按信赖方信任**\\**身份验证策略**"，然后单击要为其配置 MFA 的信赖方信任。  

3.  右键\-单击要为其配置 MFA 的信赖方信任，然后选择 "**编辑自定义多\-因素身份验证**"，或在 "**操作**" 窗格下，选择 "**编辑自定义多\-因素身份验证**"。  

4.  在 " **< 信赖\_方的编辑身份验证策略\_信任\_名称 >** " 窗口中的 "**多\-因素**" 选项卡下，可将以下设置配置为 "每\-信赖方信任身份验证策略" 的一部分：  

    -   通过 "**用户\/组**"、"**设备**" 和 "**位置**" 部分下的可用选项进行 MFA 的设置或条件。  

## <a name="configure-authentication-policies-via-windows-powershell"></a>通过 Windows PowerShell 配置身份验证策略  
Windows PowerShell 能够更灵活地使用 Windows Server 2012 R2 中 AD FS 的访问控制和身份验证机制的各种因素来配置身份验证策略和授权规则，这些规则是为你的 AD FS \-安全资源实现真正的条件性访问所必需的。  

本地计算机上的 Administrators 中的成员身份或等效身份是完成这些过程所需的最低要求。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)\(http：\/\/go.microsoft.com\/fwlink\/？LinkId\=83477\)。   

### <a name="to-configure-an-additional-authentication-method-via-windows-powershell"></a>通过 Windows PowerShell 配置其他身份验证方法  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
`Set-AdfsGlobalAuthenticationPolicy –AdditionalAuthenticationProvider CertificateAuthentication  `
~~~


> [!WARNING]  
> 若要验证是否已成功运行此命令，可以运行 `Get-AdfsGlobalAuthenticationPolicy` 命令。  

### <a name="to-configure-mfa-per-relying-party-trust-that-is-based-on-a-users-group-membership-data"></a>基于用户的组成员身份数据配置每\-信赖方信任的 MFA  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令：  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  
~~~


> [!WARNING]  
> 请确保将 *< 信赖\_方\_信任 >* 替换为信赖方信任的名称。  

2. 在同一个 Windows PowerShell 命令窗口中运行以下命令。  


~~~
$MfaClaimRule = “c:[Type == ‘“https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid'”, Value =~ ‘“^(?i) <group_SID>$'”] => issue(Type = ‘“https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'”, Value ‘“https://schemas.microsoft.com/claims/multipleauthn'”);” 

Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –AdditionalAuthenticationRules $MfaClaimRule
~~~


> [!NOTE]  
> 请确保将 < 组\_SID > 替换为\) Active Directory \(组的安全标识符 \(SID\) 的值。  

### <a name="to-configure-mfa-globally-based-on-users-group-membership-data"></a>基于用户的组成员身份数据，全局配置 MFA  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
$MfaClaimRule = “c:[Type == ‘" https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid'", Value == ‘"group_SID'"]  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn'");”  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~


> [!NOTE]  
> 请确保将 *< 组\_sid >* 替换为你的 AD 组的 sid 的值。  

### <a name="to-configure-mfa-globally-based-on-users-location"></a>基于用户的位置全局配置 MFA  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
$MfaClaimRule = “c:[Type == ‘" https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork'", Value == ‘"true_or_false'"]  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn'");”  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~



> [!NOTE]  
> 确保将 *< true\_或\_false >* 替换为 `true` 或 `false`。 此值取决于具体的规则条件，这些条件基于访问请求来自 extranet 还是 intranet。  

### <a name="to-configure-mfa-globally-based-on-users-device-data"></a>基于用户的设备数据全局配置 MFA  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
$MfaClaimRule = "c:[Type == ‘" https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser'", Value == ‘"true_or_false"']  
 => issue(Type = ‘"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value = ‘"https://schemas.microsoft.com/claims/multipleauthn'");"  

Set-AdfsAdditionalAuthenticationRule $MfaClaimRule  
~~~


> [!NOTE]  
> 确保将 *< true\_或\_false >* 替换为 `true` 或 `false`。 此值取决于具体的规则条件，这些条件基于设备是否是工作区\-联接。  

### <a name="to-configure-mfa-globally-if-the-access-request-comes-from-the-extranet-and-from-a-non-workplace-joined-device"></a>如果访问请求来自 extranet 和非\-的工作区\-已加入设备，则全局配置 MFA  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
`Set-AdfsAdditionalAuthenticationRule "c:[Type == '"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser'", Value == '"true_or_false'"] && c2:[Type == '"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork'", Value == '" true_or_false '"] => issue(Type = '"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod'", Value ='"https://schemas.microsoft.com/claims/multipleauthn'");" ` 
~~~


> [!NOTE]  
> 确保将 < true\_的两个实例替换为 `true` 或 `false`的 *\_false >* ，这取决于特定的规则条件。 规则条件基于设备是否\-加入工作区，以及访问请求是来自 extranet 还是 intranet。  

### <a name="to-configure-mfa-globally-if-access-comes-from-an-extranet-user-that-belongs-to-a-certain-group"></a>若要在访问来自属于特定组的 extranet 用户时全局配置 MFA  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
Set-AdfsAdditionalAuthenticationRule "c:[Type == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`", Value == `"group_SID`"] && c2:[Type == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`", Value== `"true_or_false`"] => issue(Type = `"https://schemas.microsoft.com/ws/2008/06/identity/claims/authenticationmethod`", Value =`"https://schemas.microsoft.com/claims/
~~~

> [!NOTE]  
> 请确保将 *< 组\_sid >* 替换为组 SID 的值并 *< true\_或*\_或 > `true` false `false`，这取决于基于特定规则条件的特定规则条件是否来自 extranet 或 intranet。  

### <a name="to-grant-access-to-an-application-based-on-user-data-via-windows-powershell"></a>通过 Windows PowerShell 基于用户数据授予对应用程序的访问权限  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  

    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  

    ```  

> [!NOTE]  
> 请确保将 *< 信赖\_方\_信任 >* 替换为信赖方信任的值。  

2. 在同一个 Windows PowerShell 命令窗口中运行以下命令。  

   ```  

     $GroupAuthzRule = "@RuleTemplate = `“Authorization`” @RuleName = `"Foo`" c:[Type == `"https://schemas.microsoft.com/ws/2008/06/identity/claims/groupsid`", Value =~ `"^(?i)<group_SID>$`"] =>issue(Type = `"https://schemas.microsoft.com/authorization/claims/deny`", Value = `"DenyUsersWithClaim`");"  
   Set-AdfsRelyingPartyTrust –TargetRelyingParty $rp –IssuanceAuthorizationRules $GroupAuthzRule  
   ```  

> [!NOTE]  
> > 请确保将 *< 组\_sid >* 替换为你的 AD 组的 sid 的值。  

### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-this-users-identity-was-validated-with-mfa"></a>仅当此用户的标识已使用 MFA 进行验证时，才能授予对受 AD FS 保护的应用程序的访问权限  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
~~~


> [!NOTE]  
> 请确保将 *< 信赖\_方\_信任 >* 替换为信赖方信任的值。  

2. 在同一个 Windows PowerShell 命令窗口中运行以下命令。  

   ```  
   $GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
   @RuleName = `"PermitAccessWithMFA`"  
   c:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)https://schemas\.microsoft\.com/claims/multipleauthn$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = ‘“PermitUsersWithClaim'");"  

   ```  

### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-the-user"></a>仅当访问请求来自已注册到用户的工作区\-已加入设备时，才能授予对受 AD FS 保护的应用程序的访问权限  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  

    ```  
    $rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust  

    ```  

> [!NOTE]  
> 请确保将 *< 信赖\_方\_信任 >* 替换为信赖方信任的值。  

2. 在同一个 Windows PowerShell 命令窗口中运行以下命令。  


~~~
$GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
@RuleName = `"PermitAccessFromRegisteredWorkplaceJoinedDevice`"  
c:[Type == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`", Value =~ `"^(?i)true$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");  
~~~



### <a name="to-grant-access-to-an-application-that-is-secured-by-ad-fs-only-if-the-access-request-comes-from-a-workplace-joined-device-that-is-registered-to-a-user-whose-identity-has-been-validated-with-mfa"></a>仅当访问请求来自已注册到其标识已使用 MFA 进行验证的用户的工作区\-已加入的设备时，才能授予对受 AD FS 保护的应用程序的访问权限。  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust ` 
~~~


> [!NOTE]  
> 请确保将 *< 信赖\_方\_信任 >* 替换为信赖方信任的值。  

2. 在同一个 Windows PowerShell 命令窗口中运行以下命令。  

   ```  
   $GroupAuthzRule = ‘@RuleTemplate = “Authorization”  
   @RuleName = “RequireMFAOnRegisteredWorkplaceJoinedDevice”  
   c1:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`"] &&  
   c2:[Type == `"https://schemas.microsoft.com/2012/01/devicecontext/claims/isregistereduser`", Value =~ `"^(?i)true$”] => issue(Type = "https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");"  

   ```  

### <a name="to-grant-extranet-access-to-an-application-secured-by-ad-fs-only-if-the-access-request-comes-from-a-user-whose-identity-has-been-validated-with-mfa"></a>仅当访问请求来自其标识已使用 MFA 进行验证的用户时，才授予对受 AD FS 保护的应用程序的 extranet 访问权限  

1.  在联合服务器上，打开 Windows PowerShell 命令窗口并运行以下命令。  


~~~
`$rp = Get-AdfsRelyingPartyTrust –Name relying_party_trust`  
~~~


> [!NOTE]  
> 请确保将 *< 信赖\_方\_信任 >* 替换为信赖方信任的值。  

2. 在同一个 Windows PowerShell 命令窗口中运行以下命令。  


~~~
$GroupAuthzRule = "@RuleTemplate = `"Authorization`"  
@RuleName = `"RequireMFAForExtranetAccess`"  
c1:[Type == `"https://schemas.microsoft.com/claims/authnmethodsreferences`", Value =~ `"^(?i)http://schemas\.microsoft\.com/claims/multipleauthn$`"] &&  
c2:[Type == `"https://schemas.microsoft.com/ws/2012/01/insidecorporatenetwork`", Value =~ `"^(?i)false$`"] => issue(Type = `"https://schemas.microsoft.com/authorization/claims/permit`", Value = `"PermitUsersWithClaim`");"  
~~~

## <a name="additional-references"></a>其他参考  

[AD FS 操作](../../ad-fs/AD-FS-2016-Operations.md)
