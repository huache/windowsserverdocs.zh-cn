---
ms.assetid: aa892a85-f95a-4bf1-acbb-e3c36ef02b0d
title: Windows Server 2016 的 Active Directory 联合身份验证服务的新增功能
description: ''
author: billmath
ms.author: billmath
manager: daveba
ms.date: 01/22/2020
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: adce37d8d06399d3a00221a12f3449244720ade7
ms.sourcegitcommit: 840d1d8851f68936db3934c80796fb8722d3c64a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76519479"
---
# <a name="whats-new-in-active-directory-federation-services"></a>Active Directory 联合身份验证服务的新增功能


## <a name="whats-new-in-active-directory-federation-services-for-windows-server-2019"></a>Windows Server 2019 的 Active Directory 联合身份验证服务的新增功能

### <a name="protected-logins"></a>受保护登录
下面简要概述了 AD FS 2019 中提供的受保护登录的更新：
- **外部身份验证提供程序作为主要身份验证手段** - 客户现在可以使用第三方身份验证产品作为首要因素，而无需公开密码作为首要因素。 在外部身份验证提供程序可以证明 2 个因素的情况下，其可以声明 MFA。 
- **密码身份验证作为附加身份验证手段** - 客户具有完全受支持的收件箱选项，在使用“无密码”选项作为首要因素后，仅使用密码作为附加因素。 与 ADFS 2016 相比，这改善了客户体（在 ADFS 2016 中，客户必须按原样下载受支持的 github 适配器）。 
- **可插入风险评估模块** - 客户现在可以生成自己的插件模块，以在预身份验证阶段阻止特定类型的请求。 这样，客户就可以更轻松地使用云智能（如身份保护）来阻止风险用户的登录或风险事务。  有关详细信息，请参阅[使用 AD FS 2019 风险评估模型生成插件](../../ad-fs/development/ad-fs-risk-assessment-model.md) 
- **ESL 改进** - 通过添加以下功能，对 2016 中的 ESL QFE 进行了改进
    - 自 ADFS 2012R2 起，允许客户处于审核模式，同时受“经典”Extranet 锁定功能保护。 目前，2016 客户在审核模式下不受任何保护。 
    - 为熟悉位置启用独立锁定阈值。 这使得使用公共服务帐户运行的多个应用实例可以在最小的影响下滚动密码。 

### <a name="additional-security-improvements"></a>附加安全改进
AD FS 2019 中提供了以下附加安全改进：
- **使用智能卡登录的远程 PSH** - 客户现在可以使用智能卡通过 PSH 远程连接到 ADFS，并使用它来管理所有 PSH 功能，包括多节点 PSH cmdlet。
- **HTTP 标头自定义** - 客户现在可以自定义在 ADFS 响应期间发出的 HTTP 标头。 这包括以下标头
     - HSTS：这表明 ADFS 终结点只能在 HTTPS 终结点上使用，以使兼容浏览器强制执行
     - x-frame-options：使 ADFS 管理员可允许特定信赖方为 ADFS 交互式登录页面嵌入 iFrame。 请谨慎使用此标头并且只能在 HTTPS 主机上使用。 
     - 未来的标头：还可以配置其他未来的标头。 

有关详细信息，请参阅[使用 AD FS 2019 自定义 HTTP 安全响应标头](../../ad-fs/operations/customize-http-security-headers-ad-fs.md) 

### <a name="authenticationpolicy-capabilities"></a>身份验证/策略功能
AD FS 2019 中包含以下身份验证/策略功能：
- **为每个 RP 指定用于附加身份验证的身份验证方法** - 客户现在可以使用声明规则来决定要为附加身份验证提供程序调用的附加身份验证提供程序。 这在 2 个用例上很有帮助
    - 客户从一个附加身份验证提供程序转换到另一个。 这样，当他们将用户加入到较新的身份验证提供程序时，他们可以使用组来控制调用哪个附加身份验证提供程序。
    - 对于某些应用程序，客户需要使用特定的附加身份验证提供程序（例如证书）。 
- **将基于 TLS 的设备身份验证仅限制于需要它的应用程序** - 客户现在可以将基于客户端 TLS 的设备身份验证仅限制于执行基于设备的条件访问的应用程序。 对于不需要基于 TLS 的设备身份验证的应用程序，这可以阻止任何不必要的设备身份验证提示（或者在客户端应用程序无法处理时失败）。
- **MFA 新鲜度支持** - AD FS 现在支持根据第二个因素凭据的新鲜度重新执行第二个因素凭据的功能。 这样，客户就可以使用 2 个因素执行初始事务，并且仅定期提示输入第二个因素。 这仅适用于可以在请求中提供附加参数并且在 ADFS 中不属于可配置设置的应用程序。 如果配置了“在 X 天内记住我的 MFA”且“supportsMFA”标志在 Azure AD 中的联合域信任设置上设置为 true，则 Azure AD 支持此参数。 

### <a name="sign-in-sso-improvements"></a>登录 SSO 改进
AD FS 2019 中进行了以下登录 SSO 改进：

- [使用居中主题对 UX 进行分页](../operations/AD-FS-paginated-sign-in.md) - ADFS 现在已移动到分页的 UX 流，使 ADFS 能够进行验证并提供更流畅的登录体验。 ADFS 现在使用居中 UI（而不是屏幕右侧）。 你可能需要较新的徽标和背景图像以使其符合此体验。 这也反映了 Azure AD 中提供的功能。
- **Bug 修复：执行 PRT 身份验证时 Win10 设备的持久 SSO 状态** - 这解决了在对 Windows 10 设备使用 PRT 身份验证时 MFA 状态无法保持持久的问题。 此问题导致的结果是，最终用户会经常收到输入第二个因素凭据 (MFA) 的提示。 通过客户端 TLS 和 PRT 机制成功执行设备身份验证时，此修复还可使体验保持一致。 


### <a name="suppport-for-building-modern-line-of-business-apps"></a>对生成新式业务线应用的支持
AD FS 2019 中添加了对生成新式 LOB 应用的以下支持：

 - **OAuth 设备流/配置文件** - AD FS 现在支持 OAuth 设备流配置文件，以在没有 UI 外围应用支持丰富登录体验的设备上执行登录。 这允许用户在不同的设备上完成登录体验。 Azure Stack 中的 Azure CLI 体验需要此功能，且其可以在其他情况下使用。 
 - **删除了资源参数** - AD FS 现在删除了指定符合当前 OAuth 规范的资源参数的要求。 除请求的权限外，客户现在可以提供信赖方信任标识符作为范围参数。 
 - **AD FS 响应中的 CORS 标头** - 客户现在可以生成单页应用程序，其允许客户端 JS 库通过从 AD FS 上的 OIDC 发现文档中查询签名密钥来验证 id_token 的签名。 
 - **PKCE 支持** - AD FS 添加了 PKCE 支持，以在 OAuth 内提供安全的身份验证代码流。 这会为此流添加一个额外的安全层，以防止代码劫持并从其他客户端重播。 
 - **Bug 修复：发送 x5t 和儿童声明** - 这是一个次要 bug 修复。 AD FS 现在额外发送“儿童”声明，以表示用于验证签名的密钥 ID 提示。 以前 AD FS 仅将其作为“x5t”声明发送。

### <a name="supportability-improvements"></a>可支持性改进
以下可支持性改进不属于 AD FS 2019：
- **向 AD FS 管理员发送错误详细信息** - 允许管理员配置最终用户以发送与最终用户身份验证失败相关的调试日志，并将其存储为压缩文件以方便使用。 管理员还可以配置 SMTP 连接，以将压缩文件自动邮寄到分类电子邮件帐户，或根据电子邮件自动创建票证。 

### <a name="deployment-updates"></a>部署更新
AD FS 2019 中现已包含以下部署更新：
- **场行为级别 2019** - 与 AD FS 2016 相同，需要新场行为级别版本才能启用上述新功能。 这允许进行以下升级：
    - 2012 R2 -> 2019
    - 2016 -> 2019   

### <a name="saml-updates"></a>SAML 更新
AD FS 2019 中包含以下 SAML 更新：
- **Bug 修复：修复聚合联合身份验证中的 bug** - 围绕聚合联合身份验证支持进行了大量 bug 修复（如 InCommon）。 围绕以下方面进行修复： 
  - 改善了聚合联合身份验证元数据文档中大量实体的缩放。以前，此缩放会失败并显示“ADMIN0017”错误。 
  - 使用“ScopeGroupID”参数通过 Get-AdfsRelyingPartyTrustsGroup PSH cmdlet 进行查询。 
  - 处理有关重复 entityID 的错误条件


### <a name="azure-ad-style-resource-specification-in-scope-parameter"></a>范围参数中的 Azure AD 样式资源规范 
之前，AD FS 要求所需的资源和范围在任何身份验证请求中都位于单独参数中。 例如，典型的 OAuth 请求如下所示：7 **https:&#47;&#47;fs.contoso.com/adfs/oauth2/authorize?</br>response_type=code&client_id=claimsxrayclient&resource=urn:microsoft:</br>adfs:claimsxray&scope=oauth&redirect_uri=https:&#47;&#47;adfshelp.microsoft.com/</br> ClaimsXray/TokenResponse&prompt=login**
 
借助 Server 2019 上的 AD FS，你现在可以传递嵌入在 scope 参数中的资源值。 这与可以对 Azure AD 进行身份验证的方式一致。 

现在可以将 scope 参数组织成一个用空格分隔的列表，其中每个条目的结构都作为资源/范围。 

> [!NOTE]
> 身份验证请求中只能指定一个资源。 如果请求中包含多个资源，则 AD FS 将返回错误，且身份验证将失败。 

### <a name="proof-key-for-code-exchange-pkce-support-for-oauth"></a>适用于 OAuth 的代码交换证明密钥 (PKCE) 支持 
使用授权代码授予的 OAuth 公共客户端容易受到授权代码拦截攻击。  RFC 7636 中详细介绍了这种攻击。 要缓解这种攻击，Server 2019 中的 AD FS 支持适用于 OAuth 授权代码授予流的代码交换证明密钥 (PKCE)。 
 
为利用 PKCE 支持，此规范将向 OAuth 2.0 授权和访问令牌请求添加其他参数。

![Proofkey](media/whats-new-in-active-directory-federation-services-for-windows-server-2016/adfs2019.png)

A. 客户端创建并记录名为“code_verifier”的机密，并导出转换后的版本“t(code_verifier)”（称为“code_challenge”），该版本与转换方法“t_m”一起在 OAuth 2.0 授权请求中发送。 

B. 授权终结点照常响应，但记录“t(code_verifier)”和转换方法。 

C. 然后，客户端照常在访问令牌请求中发送授权代码，但包含在 (A) 生成的“code_verifier”机密。 

D. AD FS 转换“code_verifier”，并将其与 (B) 中的“t(code_verifier)”进行比较。  如果它们不相等，则拒绝访问。 

#### <a name="faq"></a>FAQ 
**Q.** 是否可以像在 Azure AD 中完成请求那样将资源值作为作用域值的一部分进行传递？ 
</br>**A.** 借助 Server 2019 上的 AD FS，你现在可以传递嵌入在 scope 参数中的资源值。 现在可以将 scope 参数组织成一个用空格分隔的列表，其中每个条目的结构都作为资源/范围。 例如  
**< create a valid sample request>**

**Q.** AD FS 是否支持 PKCE 扩展？
</br>**A.** Server 2019 中的 AD FS 支持适用于 OAuth 授权代码授予流的代码交换证明密钥 (PKCE) 

## <a name="whats-new-in-active-directory-federation-services-for-windows-server-2016"></a>Windows Server 2016 的 Active Directory 联合身份验证服务的新增功能   
要查找有关 AD FS 早期版本的信息，请参阅以下文章：  
 [Windows Server 2012 或 2012 R2 中的 ADFS](https://technet.microsoft.com/library/hh831502.aspx) 和 [AD FS 2.0](https://technet.microsoft.com/library/adfs2.aspx)  

 Active Directory 联合身份验证服务跨多种应用程序（包括 Office 365、基于云的 SaaS 应用程序以及企业网络上的应用程序）提供访问控制和单一登录。  
* 对于 IT 组织，它使你能够基于同一组凭据和策略在本地和云中为新式和传统应用程序提供登录和访问控制。    
* 对于用户，它使用相同且熟悉的帐户凭据提供无缝登录。  
* 对于开发人员，它提供了一种简单的方法来对其身份位于组织目录中的用户进行身份验证，以便开发人员可以将精力集中于其应用程序，而不是身份验证或身份上。  

本文介绍 Windows Server 2016 (AD FS 2016) 中 AD FS 的新增功能。  

## <a name="eliminate-passwords-from-the-extranet"></a>消除 Extranet 中的密码  
AD FS 2016 启用了三个无需密码即可登录的新选项，使组织能够避免网络危害（网络钓鱼、密码泄露或被盗）所带来的风险。 

### <a name="sign-in-with-azure-multi-factor-authentication"></a>使用 Azure 多重身份验证登录
AD FS 2016 基于 Windows Server 2012 R2 中 AD FS 的多重身份验证 (MFA) 功能生成，允许仅使用 Azure MFA 代码登录，无需首先输入用户名和密码。

* 使用 Azure MFA 作为主要身份验证方法，系统会提示用户通过 Azure Authenticator 应用输入其用户名和 OTP 代码。  
* 使用 Azure MFA 作为辅助或附加身份验证方法，用户可提供主要身份验证凭据（使用 Windows 集成身份验证、用户名和密码、智能卡、用户或设备证书），然后可看到基于文本、语音或 OTP 的 Azure MFA 登录提示。  
* 借助新的内置 Azure MFA 适配器，使用 AD FS 进行 Azure MFA 的设置和配置从未如此简单。
* 组织无需本地 Azure MFA 服务器即可利用 Azure MFA。
* 可为 Intranet 或 Extranet 配置 Azure MFA，或将其作为任何访问控制策略的一部分进行配置。

有关 Azure MFA 与 AD FS 的详细信息，请参阅：
*  [配置 AD FS 2016 和 Azure MFA](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-and-azure-mfa)  

### <a name="password-less-access-from-compliant-devices"></a>符合设备的无密码访问
AD FS 2016 基于以前的设备注册功能生成，可基于设备符合性状态启用登录和访问控制。 用户可以使用设备凭据登录，并在设备属性发生变化时重新评估符合性，使用户始终能够确保策略得到实施。  这样做可以实现以下策略：

* 仅允许从托管和/或符合的设备进行访问  
* 仅允许从托管和/或符合的设备进行 Extranet 访问  
* 对于不受管理或不符合的计算机，需要多重身份验证  

AD FS 在混合方案中提供条件访问策略的本地组件。 向 Azure AD 注册设备以对云资源进行条件访问时，该设备标识也可用于 AD FS 策略。

![新增功能](media/whats-new-in-active-directory-federation-services-for-windows-server-2016/ADFS_ITPRO4.png)  

 有关在云中使用基于设备的条件访问的详细信息，请参阅：   
 *  [Azure Active Directory 条件访问](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access/)

有关将基于设备的条件访问与 AD FS 结合使用的详细信息，请参阅：
*  [基于设备的条件访问与 AD FS 规划](../../ad-fs/deployment/Plan-Device-based-Conditional-Access-on-Premises.md)  
* [AD FS 中的访问控制策略](../../ad-fs/operations/Access-Control-Policies-in-AD-FS.md)  

### <a name="sign-in-with-windows-hello-for-business"></a>通过 Windows Hello 企业版登录  

> [!NOTE]
> 目前，基于浏览器的单一登录 (SSO) 与 Microsoft Windows Hello 企业版不支持 Google Chrome 和[基于 Chromium 构建的新 Microsoft Edge](https://www.microsoft.com/edge?form=MB110A&OCID=MB110A) 开源项目浏览器。 请使用 Internet Explorer 或较早版本的 Microsoft Edge。  

Windows 10 设备引入了 Windows Hello 和 Windows Hello 企业版，将用户密码替换为受用户手势（PIN、指纹等生物识别手势或面部识别）保护的强设备绑定用户凭据。 AD FS 2016 支持这些新增 Windows 10 功能，使用户无需提供密码即可从 Intranet 或 Extranet 登录到 AD FS 应用程序。

有关在组织中使用 Microsoft Windows Hello 企业版的详细信息，请参阅：
*  [在组织中启用 Windows Hello 企业版](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-passport-deployment/)

## <a name="secure-access-to-applications"></a>安全访问应用程序

### <a name="modern-authentication"></a>新式身份验证
AD FS 2016 支持最新的新式协议，可为 Windows 10 以及最新的 iOS 和 Android 设备和应用提供更好的用户体验。  

有关详细信息，请参阅[适用于开发人员的 AD FS 方案](../../ad-fs/overview/ad-fs-openid-connect-oauth-flows-scenarios.md)  


### <a name="configure-access-control-policies-without-having-to-know-claim-rules-language"></a>无需了解声明规则语言即可配置访问控制策略  
以前，AD FS 管理员必须使用 AD FS 声明规则语言配置策略，这使得配置和维护策略变得困难。 借助访问控制策略，管理员可以使用内置模板来应用常见的策略，例如
* 仅允许 Intranet 访问
* 允许所有人，并要求来自 Extranet 的人员进行 MFA
* 允许所有人，并要求来自特定组的人员进行 MFA

使用向导驱动过程可以轻松地自定义模板，以便添加异常或其他策略规则，并可将模板应用到一个或多个应用程序，以实现一致的策略执行。

有关详细信息，请参阅 [AD FS 中的访问控制策略](../../ad-fs/operations/Access-Control-Policies-in-AD-FS.md)。  

### <a name="enable-sign-on-with-non-ad-ldap-directories"></a>启用使用非 AD LDAP 目录进行登录  
许多组织将 Active Directory 和第三方目录结合在一起。 通过添加 AD FS 对存储在符合 LDAP v3 的目录中的用户进行身份验证的支持，AD FS 现在可用于：
* 符合 LDAP v3 的第三方目录中的用户
* 未配置 Active Directory 双向信任 Active Directory 林中的用户
* Active Directory 轻型目录服务 (AD LDS) 中的用户

有关详细信息，请参阅[配置 AD FS 以对存储在 LDAP 目录中的用户进行身份验证](../../ad-fs/operations/Configure-AD-FS-to-authenticate-users-stored-in-LDAP-directories.md)。  

## <a name="better-sign-in-experience"></a>更好的登录体验
### <a name="customize-sign-in-experience-for-ad-fs-applications"></a>自定义 AD FS 应用程序的登录体验  
有用户反馈说，如果能为每个应用程序自定义登录体验，将是一项很好的可用性改进，特别是对于为代表多个不同公司或品牌的应用程序提供登录的组织。  

以前，Windows Server 2012 R2 中的 AD FS 为所有信赖方应用程序提供了一种通用的登录体验，并能够为每个应用程序自定义基于文本的内容子集。 通过 Windows Server 2016，你不仅可为每个应用程序自定义消息，还可以自定义图像、徽标和 Web 主题。 此外，你还可以创建新的自定义 Web 主题，并为每个依赖方应用这些主题。  

有关详细信息，请参阅 [AD FS 用户登录自定义](../../ad-fs/operations/AD-FS-user-sign-in-customization.md)。  



## <a name="manageability-and-operational-enhancements"></a>可管理性和操作增强  
下一节介绍了 Windows Server 2016 中的 Active Directory 联合身份验证服务引入的改进操作方案。  

### <a name="streamlined-auditing-for-easier-administrative-management"></a>简化的审核，以便更轻松地进行行政管理  
在适用于 Windows Server 2012 R2 的 AD FS 中，为单个请求生成了大量审核事件，且有关登录或令牌颁发活动的相关信息或是不存在（在某些版本的 AD FS 中），或是跨多个审核事件分布。 由于其冗长特性，AD FS 审核事件默认处于关闭状态。  
随着 AD FS 2016 的发布，审核变得更加精简且不那么冗长。  

有关详细信息，请参阅 [Windows Server 2016 中 AD FS 的审核增强功能](../../ad-fs/technical-reference/auditing-enhancements-to-ad-fs-in-windows-server.md)。  

### <a name="improved-interoperability-with-saml-20-for-participation-in-confederations"></a>改进了与 SAML 2.0 的互操作性，以参与联合身份验证  
AD FS 2016 包含附加的 SAML 协议支持，包括支持基于包含多个实体的元数据导入信任。 这使你可以将 AD FS 配置为参与联合身份验证，例如 InCommon 联合身份验证和其他符合 eGov 2.0 标准的实现。  

有关详细信息，请参阅 [SAML 2.0 的改进互操作性](../../ad-fs/operations/Improved-interoperability-with-SAML-2.0.md)。  

### <a name="simplified-password-management-for-federated-o365-users"></a>O365 联合身份验证用户的简化密码管理  
你可以将 Active Directory 联合身份验证服务 (AD FS) 配置为向受 AD FS 保护的信赖方信任（应用程序）发送密码过期声明。 如何使用这些声明取决于应用程序。 例如，使用 Office 365 作为你的信赖方时，会将更新实施到 Exchange 和 Outlook，以通知联合身份验证用户其密码即将过期。  

有关详细信息，请参阅[配置 AD FS 以发送密码过期声明](../../ad-fs/operations/Configure-AD-FS-to-Send-Password-Expiry-Claims.md)。  

### <a name="moving-from-ad-fs-in-windows-server-2012-r2-to-ad-fs-in-windows-server-2016-is-easier"></a>从 Windows Server 2012 R2 中的 AD FS 迁移到 Windows Server 2016 中的 AD FS 更简单  
以前，迁移到新版 AD FS 需要从旧的场导出配置，并将其导入到全新的并行场。  

现在，从 Windows Server 2012 R2 上的 AD FS 迁移到 Windows Server 2016 上的 AD FS 已变得更加简单。 只需将新的 Windows Server 2016 服务器添加到 Windows Server 2012 R2 场，该场将作用于 Windows Server 2012 R2 场行为级别，因此其外观和行为类似于 Windows Server 2012 R2 场。  

然后，将新的 Windows Server 2016 服务器添加到场，验证该功能并从负载均衡器中删除旧服务器。 所有场节点都运行 Windows Server 2016 后，便可以将场行为级别升级到 2016，并开始使用新功能。  

有关详细信息，请参阅[升级到 Windows Server 2016 中的 AD FS](../../ad-fs/deployment/Upgrading-to-AD-FS-in-Windows-Server-2016.md)。  
