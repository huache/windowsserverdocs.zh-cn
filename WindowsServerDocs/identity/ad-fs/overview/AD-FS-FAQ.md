---
ms.assetid: acc9101b-841c-4540-8b3c-62a53869ef7a
title: AD FS 常见问题解答
description: AD FS 的常见问题解答
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 04/29/2020
ms.topic: article
ms.openlocfilehash: 50767d5b1941e397583f6c2bfa1d6b2ae3f253cf
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87949681"
---
# <a name="ad-fs-frequently-asked-questions-faq"></a>AD FS 的常见问题解答 (FAQ)

以下文档是与 Active Directory 联合身份验证服务有关的常见问题解答的主页。  该文档已根据问题类型分为几组。

## <a name="deployment"></a>部署

### <a name="how-can-i-upgrademigrate-from-previous-versions-of-ad-fs"></a>如何从 AD FS 的早期版本升级/迁移

可以使用以下某项操作升级 AD FS：

- Windows Server 2012 R2 AD FS 升级到 Windows Server 2016 AD FS 或更高版本。 请注意，如果要从 Windows Server 2016 AD FS 升级到 Windows Server 2019 AD FS，则方法相同。
    - [使用 WID 数据库升级到 Windows Server 2016 中的 AD FS](../deployment/upgrading-to-ad-fs-in-windows-server.md)
    - [使用 SQL 数据库升级到 Windows Server 2016 中的 AD FS](../deployment/upgrading-to-ad-fs-in-windows-server-sql.md)
- Windows Server 2012 AD FS 迁移到 Windows Server 2012 R2 AD FS
    - [迁移到 Windows Server 2012 R2 上的 AD FS](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn486815(v=ws.11))
- AD FS 2.0 迁移到 Windows Server 2012 AD FS
    - [迁移到 Windows Server 2012 上的 AD FS](../deployment/migrate-ad-fs-role-services-to-windows-server-2012.md)
- AD FS 1.x 升级到 AD FS 2.0
    - [从 AD FS 1.x 升级到 AD FS 2.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff678035(v=ws.10))

如果需要从 AD FS 2.0 或2.1（Windows Server 2008 R2 或 Windows Server 2012）升级，则必须使用（位于 C:\Windows\ADFS 中）的内置脚本。

### <a name="why-does-ad-fs-installation-require-a-reboot-of-the-server"></a>为什么安装 AD FS 需要重启服务器？

Windows Server 2016 中添加了 HTTP/2 支持，但 HTTP/2 不能用于客户端证书身份验证。  由于许多 AD FS 方案都使用客户端证书身份验证，因此，大多数客户端都不支持使用 HTTP/1.1 重试请求，AD FS 场配置将本地服务器的 HTTP 设置重新配置为 HTTP/1.1。  这需要重启服务器。

### <a name="is-using-windows-2016-wap-servers-to-publish-the-ad-fs-farm-to-the-internet-without-upgrading-the-back-end-ad-fs-farm-supported"></a>是否可以在不升级受支持的后端 AD FS 的情况下使用 Windows 2016 WAP 服务器将 AD FS 场发布到 Internet？
是的，支持此配置，但此配置不支持新的 AD FS 2016 功能。  此配置是从 AD FS 2012 R2 到 AD FS 2016 的迁移阶段的临时配置，不应用于长期部署。

### <a name="is-it-possible-to-deploy-ad-fs-for-office-365-without-publishing-a-proxy-to-office-365"></a>是否可以在不将代理发布到 Office 365 的情况下为 Office 365 部署 AD FS？
是的，支持此操作。 但是，另一方面，

1. 你将需要手动管理更新令牌签名证书，因为 Azure AD 将无法访问联合元数据。 有关手动更新令牌签名证书的详细信息，请参阅[续订 Office 365 和 Azure Active Directory 的联合身份验证证书](/azure/active-directory/connect/active-directory-aadconnect-o365-certs)
2. 你将无法使用旧的身份验证流（例如 ExO 代理身份验证流）

### <a name="what-are-load-balancing-requirements-for-ad-fs-and-wap-servers"></a>AD FS 和 WAP 服务器的负载均衡要求有哪些？

AD FS 是无状态系统。 因此，负载均衡对于登录而言相当简单。 下面是关于负载均衡系统的重要建议。


- 不应为负载均衡器配置 IP 相关性。 在某些 Exchange Online 方案中，这可能会使一些服务器上的负载过多。
- 负载均衡器不得终止 HTTPS 连接并重启与 ADFS 服务器建立的新连接。
- 负载均衡器应确保在将连接 IP 地址发送到 ADFS 时，应将其转换为 HTTP 数据包中的源 IP。 如果负载均衡器无法发送 HTTP 数据包中的源 IP，则负载均衡器必须向 x-forwarded-for 标头添加（或在现有情况下附加）IP 地址。 这是正确处理某些 IP 相关功能（禁止的 IP、Extranet 智能锁定等）所必需的，如果配置不当，可能会导致安全性降低。
- 负载均衡器应支持 SNI。 如果不支持，请确保将 AD FS 配置为创建 HTTPS 绑定以处理不支持 SNI 的客户端。
- 负载均衡器应使用 AD FS HTTP 运行状况探测终结点来检测 AD FS 或 WAP 服务器是否已启动且正常运行，如果未返回 200 OK，则排除这些服务器。

### <a name="what-multi-forest-configurations-are-supported-by-ad-fs"></a>AD FS 支持哪些多林配置？

AD FS 支持多个多林配置，并依赖基础 AD DS 信任网络以在多个受信任领域上对用户进行身份验证。 强烈建议使用双向林信任，因为这是一种更为简单的设置，可确保信任子系统正常运行而不会出现问题。 另外，

- 如果采用单向林信任（例如包含合作伙伴标识的 DMZ 林），则建议在 corp 林中部署 ADFS，并将 DMZ 林视为通过 LDAP 连接的其他本地声明提供程序信任。 在这种情况下，Windows 集成身份验证不适用于 DMZ 林用户，并且将要求他们执行密码身份验证，因为这是 LDAP 唯一受支持的机制。 如果无法采用此选项，则需要在 DMZ 林中设置另一个 ADFS，并将其添加为 corp 林中 ADFS 中的声明提供程序信任。 用户将需要进行主页领域发现，但 Windows 集成身份验证和密码身份验证都会运行。 请对 DMZ 林中 ADFS 的颁发规则进行适当的更改，因为 corp 林中的 ADFS 无法从 DMZ 林获取有关用户的额外用户信息。
- 尽管支持域级别信任并且可以运行，但我们强烈建议你迁移到林级别信任模型。 此外，还需要确保名称的 UPN 路由和 NETBIOS 名称解析可以正常运行。

>[!NOTE]
>如果将选择性身份验证与双向信任配置一起使用，请确保为调用方用户授予目标服务帐户的“允许身份验证”权限。

### <a name="does-ad-fs-extranet-smart-lockout-support-ipv6"></a>AD FS Extranet 智能锁定是否支持 IPv6？
支持，会对熟悉/未知的位置考虑 IPv6 地址。


## <a name="design"></a>设计

### <a name="what-third-party-multi-factor-authentication-providers-are-available-for-ad-fs"></a>哪些第三方多重身份验证提供程序可用于 AD FS？
AD FS 为第三方 MFA 提供程序提供了可扩展的集成机制。 没有适用于此的固定证书计划。 假设供应商已在发布前执行了必要的验证。

在 [AD FS 的 MFA 提供程序](../operations/Configure-Additional-Authentication-Methods-for-AD-FS.md)上发布了已通知 Microsoft 的供应商列表。  可能始终存在我们不了解的提供程序，我们将在了解这些提供程序的同时更新列表。

### <a name="are-third-party-proxies-supported-with-ad-fs"></a>AD FS 是否支持第三方代理？
是的，第三方代理可以放在 AD FS 的前面，但任何第三方代理都必须支持用于替代 Web 应用程序代理的 [MS-ADFSPIP 协议](/openspecs/windows_protocols/ms-adfspip/76deccb1-1429-4c80-8349-d38e61da5cbb)。

以下是我们了解的第三方提供程序的列表。  可能始终存在我们不了解的提供程序，我们将在了解这些提供程序的同时更新列表。

- [F5 Access Policy Manager](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-third-party-integration-13-1-0/12.html#guid-1ee8fbb3-1b33-4982-8bb3-05ae6868d9ee)


### <a name="where-is-the-capacity-planning-sizing-spreadsheet-for-ad-fs-2016"></a>AD FS 2016 的容量规划大小调整电子表格位于何处？
可在[此处](https://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx)下载 AD FS 2016 版电子表格。
这也可用于 Windows Server 2012 R2 中的 AD FS。

### <a name="how-can-i-ensure-my-ad-fs-and-wap-servers-support-apples-atp-requirements"></a>如何确保 AD FS 和 WAP 服务器支持 Apple 的 ATP 要求？

Apple 已发布了一组名为“应用传输安全性 (ATS)”的要求，该要求可能会影响对 AD FS 进行身份验证的 iOS 应用的调用。  确认 AD FS 和 WAP 服务器是否支持[使用 ATS 进行连接的要求](https://developer.apple.com/library/prerelease/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW57)来确保其符合要求。
尤其应该验证 AD FS 和 WAP 服务器是否支持 TLS 1.2，并且 TLS 连接的协商密码套件将支持完美的前向保密性。

可以使用[在 AD FS 中管理 SSL 协议](../operations/Manage-SSL-Protocols-in-AD-FS.md)启用和禁用 SSL 2.0 和 3.0 以及 TLS 版本 1.0、1.1 和 1.2。

若要确保 AD FS 和 WAP 服务器仅协商支持 ATP 的 TLS 密码套件，可以禁用不属于 [ATP 兼容密码套件列表](https://developer.apple.com/library/prerelease/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW57)中的所有密码套件。  为此，请使用 [Windows TLS PowerShell cmdlet](/powershell/module/tls/?view=win10-ps)。

## <a name="developer"></a>开发人员

### <a name="when-generating-an-id_token-with-adfs-for-a-user-authenticated-against-ad-how-is-the-sub-claim-generated-in-the-id_token"></a>通过 AD 验证的用户使用 ADFS 生成 id_token 时，如何在 id_token 中生成“sub”声明？
“sub”声明的值是客户端 ID 和定位声明值的哈希。

### <a name="what-is-the-lifetime-of-the-refresh-tokenaccess-token-when-the-user-logs-in-via-a-remote-claims-provider-trust-over-ws-fedsaml-p"></a>用户通过 WS-Fed/SAML-P 经远程声明提供程序信任登录时，刷新令牌/访问令牌的生存期是多长？
刷新令牌的生存期将是 ADFS 从远程声明提供程序信任中获得的令牌的生存期。 访问令牌的生存期将是为信赖方颁发访问令牌的信赖方令牌生存期。

### <a name="i-need-to-return-profile-and-email-scopes-as-well-in-addition-to-the-openid-scope-can-i-obtain-additional-information-using-scopes-how-to-do-it-in-ad-fs"></a>除了 OpenId 作用域外，我还需要返回 profile 和 email 作用域。 是否可以使用作用域获取其他信息？ 如何在 AD FS 中执行此操作？
可以使用自定义的 id_token 在 id_token 本身中添加相关信息。 有关详细信息，请参阅文章[自定义要在 id_token 中发出的声明](../development/Custom-Id-Tokens-in-AD-FS.md)。

### <a name="how-to-issue-json-blobs-inside-jwt-tokens"></a>如何在 JWT 令牌中发布 json blob？
为此，在 AD FS 2016 中添加了特殊的 ValueType（“<http://www.w3.org/2001/XMLSchema#json>”）和转义字符 (\x22)。 若要了解颁发规则以及访问令牌的最终输出，请参阅下面的示例。

示例颁发规则：

```
=> issue(Type = "array_in_json", ValueType = "http://www.w3.org/2001/XMLSchema#json", Value = "{\x22Items\x22:[{\x22Name\x22:\x22Apple\x22,\x22Price\x22:12.3},{\x22Name\x22:\x22Grape\x22,\x22Price\x22:3.21}],\x22Date\x22:\x2221/11/2010\x22}");
```

在访问令牌中颁发的声明：

```
"array_in_json":{"Items":[{"Name":"Apple","Price":12.3},{"Name":"Grape","Price":3.21}],"Date":"21/11/2010"}
```

### <a name="can-i-pass-resource-value-as-part-of-the-scope-value-like-how-requests-are-done-against-azure-ad"></a>是否可以像在 Azure AD 中完成请求那样将资源值作为作用域值的一部分进行传递？
借助 Server 2019 上的 AD FS，你现在可以传递嵌入在 scope 参数中的资源值。 现在可以将 scope 参数组织成一个用空格分隔的列表，其中每个条目的结构都作为资源/范围。 例如 <创建有效的示例请求>

### <a name="does-ad-fs-support-pkce-extension"></a>AD FS 是否支持 PKCE 扩展？
Server 2019 中的 AD FS 支持适用于 OAuth 授权代码授予流的代码交换证明密钥 (PKCE)

### <a name="what-permitted-scopes-are-supported-by-ad-fs"></a>AD FS 支持哪些允许的作用域？
- aza - 如果[对代理客户端使用 OAuth 2.0 协议扩展](/openspecs/windows_protocols/ms-oapxbc/2f7d8875-0383-4058-956d-2fb216b44706)，并且 scope 参数包含作用域“aza”，则服务器将发布新的主刷新令牌并在响应的 refresh_token 字段中设置该令牌，以及将 refresh_token_expires_in 字段设置为新的主刷新令牌的生存期（如果强制执行的话）。
- openid - 允许应用程序请求使用 OpenID Connect 授权协议。
- logon_cert - logon_cert 作用域允许应用程序请求登录证书，这些证书可用于以交互方式登录通过身份验证的用户。 AD FS 服务器忽略响应中的 access_token 参数，改为提供 base64 编码的 CMS 证书链或 CMC 完整 PKI 响应。 [此处](/openspecs/windows_protocols/ms-oapx/32ce8878-7d33-4c02-818b-6c9164cc731e)提供更多详细信息。
- user_impersonation - user_impersonation 作用域是成功从 AD FS 请求代表访问令牌的必要条件。 有关如何使用此作用域的详细信息，请参阅[结合使用 OAuth 与 AD FS 2016 通过 On-Behalf-Off (OBO) 构建多层应用程序](../../ad-fs/development/ad-fs-on-behalf-of-authentication-in-windows-server.md)。
- vpn_cert - vpn_cert 作用域允许应用程序请求 VPN 证书，该证书可用于使用 EAP-TLS 身份验证建立 VPN 连接。 不再支持此作用域。
- email - 允许应用程序请求登录用户的电子邮件声明。 不再支持此作用域。
- profile - 允许应用程序请求登录用户的个人资料相关声明。 不再支持此作用域。


## <a name="operations"></a>操作

### <a name="how-do-i-replace-the-ssl-certificate-for-ad-fs"></a>如何替换 AD FS 的 SSL 证书？
AD FS SSL 证书与 AD FS 管理管理单元中的 AD FS 服务通信证书不同。  若要更改 AD FS SSL 证书，需要使用 PowerShell。 按照下面文章中的指南进行操作：

[管理 AD FS 和 WAP 2016 中的 SSL 证书](../operations/manage-ssl-certificates-ad-fs-wap.md)

### <a name="how-can-i-enable-or-disable-tlsssl-settings-for-ad-fs"></a>如何启用或禁用 AD FS 的 TLS/SSL 设置
若要禁用或启用 SSL 协议和密码套件，请使用以下文章：

[管理 AD FS 中的 SSL 协议](../operations/Manage-SSL-Protocols-in-AD-FS.md)

### <a name="does-the-proxy-ssl-certificate-have-to-be-the-same-as-the-ad-fs-ssl-certificate"></a>代理 SSL 证书是否必须与 AD FS SSL 证书相同？
对于代理 SSL 证书和 AD FS SSL 证书，请使用以下指南：


- 如果代理用于代理使用 Windows 集成身份验证的 AD FS 请求，则代理 SSL 证书必须与联合服务器 SSL 证书相同（使用相同的密钥）
- 如果启用了 AD FS 属性“ExtendedProtectionTokenCheck”（AD FS 中的默认设置），则代理 SSL 证书必须与联合服务器 SSL 证书相同（使用相同的密钥）
- 否则，代理 SSL 证书可以使用与 AD FS SSL 证书不同的密钥，但必须满足相同的[要求](./ad-fs-requirements.md)

### <a name="why-do-i-only-see-a-password-login-on-ad-fs-and-not-my-other-authentication-methods-that-i-have-configured"></a>为什么只能在 AD FS 上看到密码登录，而看不到已配置的其他身份验证方法？
应用程序明确要求映射到已配置且已启用的身份验证方法的特定身份验证 URI 时，AD FS 仅在登录屏幕中显示一种身份验证方法。 这会在 WS 联合身份验证请求的“wauth”参数和 SAML 协议请求的“RequestedAuthnCtxRef”参数中进行传达。 因此，只显示请求的身份验证方法（例如密码登录）。

将 AD FS 用于 Azure AD 时，应用程序通常会将 prompt=login 参数发送到 Azure AD。 Azure AD 默认将此转换为请求基于新密码的 AD FS 登录。 这是在网络内部的 AD FS 上看到密码登录或看不到使用证书登录的选项的最常见原因。 更改 Azure AD 中的联合域设置可轻松地解决此问题。

有关如何配置此设置的信息，请参阅 [Active Directory 联合身份验证服务 prompt=login 参数支持](../operations/AD-FS-Prompt-Login.md)。

### <a name="how-can-i-change-the-ad-fs-service-account"></a>如何更改 AD FS 服务帐户？
若要更改 AD FS 服务帐户，请使用 AD FS 工具箱[服务帐户 Powershell 模块](https://github.com/Microsoft/adfsToolbox/tree/master/serviceAccountModule)按照说明进行操作。

### <a name="how-can-i-configure-browsers-to-use-windows-integrated-authentication-wia-with-ad-fs"></a>如何配置浏览器以将 Windows 集成身份验证 (WIA) 与 AD FS 结合使用？

有关如何配置浏览器的信息，请参阅[配置浏览器以将 Windows 集成身份验证 (WIA) 与 AD FS 结合使用](../operations/Configure-AD-FS-Browser-WIA.md)。

### <a name="can-i-turn-off-browserssoenabled"></a>能否关闭 BrowserSsoEnabled？
如果你在 ADFS 上没有基于设备的访问控制策略，也没有使用 ADFS 进行 Windows Hello 企业版证书注册，则可以关闭 BrowserSsoEnabled。 BrowserSsoEnabled 允许 ADFS 从包含设备信息的客户端收集 PRT（主刷新令牌）。 否则，ADFS 的身份验证将无法在 Windows 10 设备上运行。

### <a name="how-long-are-ad-fs-tokens-valid"></a>AD FS 令牌的有效期有多长？

这个问题通常表示“用户无需输入新凭据即可获得单一登录 (SSO) 的时间是多长，以及我作为管理员如何对此进行控制？”  文章 [AD FS 单一登录设置](../operations/ad-fs-single-sign-on-settings.md)中介绍了此行为和控制该行为的配置设置。

下面列出了各种 Cookie 和令牌的默认生存期（以及管理生存期的许多参数）：

**注册的设备**

- PRT 和 SSO Cookie：最长时间为 90 天，由 PSSOLifeTimeMins 管理。 （提供的设备至少每 14 天使用一次，由 DeviceUsageWindow 控制）

- Refresh token：根据上述计算得出一致的行为

- access_token：默认值为 1 小时，具体取决于信赖方

- id_token：与访问令牌相同

**未注册的设备**

- SSO Cookie：默认值为 8 小时，由 SSOLifetimeMins 管理。  启用“使我保持登录状态 (KMSI)”后，默认值为 24 小时，可通过 KMSILifetimeMins 进行配置。


- Refresh token：默认值为 8 小时。 启用 KMSI 后为 24 小时

- access_token：默认值为 1 小时，具体取决于信赖方

- id_token：与访问令牌相同

### <a name="does-ad-fs-support-http-strict-transport-security-hsts"></a>AD FS 是否支持 HTTP 严格传输安全性 (HSTS)？

HTTP 严格传输安全性 (HSTS) 是一种 Web 安全策略机制，有助于减少具有 HTTP 和 HTTPS 终结点的服务的协议降级攻击和 Cookie 劫持。 它允许 Web 服务器声明 Web 浏览器（或其他符合要求的用户代理）应仅使用 HTTPS 与其进行交互，而并不通过 HTTP 协议进行交互。

Web 身份验证流量的所有 AD FS 终结点都通过 HTTPS 专门打开。  因此，AD FS 可以有效地缓解 HTTP 严格传输安全策略机制引发的威胁（由于 HTTP 中没有侦听器，因此不会根据设计降级到 HTTP）。 此外，AD FS 使用安全标志标记所有 Cookie 来阻止将 Cookie 发送到具有 HTTP 协议终结点的其他服务器。

因此，不需要在 AD FS 服务器上实现 HSTS，因为它永远不会降级。  出于符合性目的，AD FS 服务器满足这些要求，因为它们从不使用 HTTP，并且所有 Cookie 都标记为安全。

此外，AD FS 2016（具有最新修补程序）和 AD FS 2019 支持发出 HSTS 标头。 若要对此进行配置，请参阅[使用 AD FS 自定义 HTTP 安全响应标头](../operations/customize-http-security-headers-ad-fs.md)

### <a name="x-ms-forwarded-client-ip-does-not-contain-the-ip-of-the-client-but-contains-ip-of-the-firewall-in-front-of-the-proxy-where-can-i-get-the-right-ip-of-the-client"></a>X-ms-forwarded-client-ip 不包含客户端的 IP，但包含代理前面的防火墙的 IP。 在哪里可以获得正确的客户端 IP？
不建议在 WAP 之前终止 SSL。 如果 SSL 终止在 WAP 之前完成，则 X-ms-forwarded-client-ip 将包含 WAP 之前的网络设备的 IP。 下面是 AD FS 支持的各种与 IP 相关的声明的简要说明：
 - x-ms-client-ip：连接到 STS 的设备网络 IP。  对于 Extranet 请求，此项始终包含 WAP 的 IP。
 - x-ms-forwarded-client-ip：多值声明，其中包含通过 Exchange Online 转发给 ADFS 的所有值以及连接到 WAP 的设备 IP 地址。
 - Userip：对于 Extranet 请求，此声明将包含 x-ms-forwarded-client-ip 的值。  对于 Intranet 请求，此声明将包含与 x-ms-client-ip 相同的值。

 此外，在 AD FS 2016（具有最新修补程序）和更高版本中，还支持捕获 x-forwarded-for 标头。 任何未在第 3 层转发的负载均衡器或网络设备（保留 IP）都应将传入客户端 IP 添加到行业标准 x-forwarded-for 标头中。

### <a name="i-am-trying-to-get-additional-claims-on-the-user-info-endpoint-but-its-only-returning-subject-how-can-i-get-additional-claims"></a>我尝试在用户信息终结点上获取其他声明，但它仅返回使用者。 如何获取其他声明？
AD FS 的 userinfo 终结点始终返回 OpenID 标准中指定的使用者声明。 AD FS 不提供通过 UserInfo 终结点请求的其他声明。 如果需要 ID 令牌中的其他声明，请参阅 [AD FS 中的自定义 ID 令牌](../development/custom-id-tokens-in-ad-fs.md)。

### <a name="why-do-i-see-a-lot-of-1021-errors-on-my-ad-fs-servers"></a>为什么我在 AD FS 服务器上看到了很多 1021 错误？
对于资源 00000003-0000-0000-c000-000000000000，AD FS 上的无效资源访问权限，系统通常会记录此事件。 此错误是由于客户端尝试获取 Azure AD Graph 服务的访问令牌而导致的错误行为造成的。 由于 AD FS 上没有资源，这会导致 AD FS 服务器上出现事件 ID 1021。 可以忽略 AD FS 上的资源 00000003-0000-0000-c000-000000000000 的任何警告或错误。

### <a name="why-am-i-seeing-a-warning-for-failure-to-add-the-ad-fs-service-account-to-the-enterprise-key-admins-group"></a>为什么我会看到关于将 AD FS 服务帐户添加到企业密钥管理员组失败的警告？
仅当域中存在具有 FSMO PDC 角色的 Windows 2016 域控制器时，才创建此组。 若要解决此错误，可以手动创建组，并在将服务帐户添加为组成员之后，按照以下步骤提供所需的权限。
1.    打开“Active Directory 用户和计算机” 。
2.    在导航窗格中，右键单击你的域名，然后单击“属性” 。
3.    单击“安全性”（如果没有“安全性”选项卡，请从“视图”菜单中打开“高级功能”）。
4.    单击“高级”。 单击“添加”。 单击“选择主体”。
5.    此时将出现“选择用户、计算机、服务帐户或组”对话框。  在“输入要选择的对象名称”文本框中，键入“密钥管理组”。  单击“确定”。
6.    在“应用于”列表框中，选择“子级用户对象”。
7.    使用滚动条滚动到页面底部，然后单击“全部清除”。
8.    在“属性”部分中，选择“读取 msDS-KeyCredentialLink”和“写入 msDS-KeyCredentialLink”  。

### <a name="why-does-modern-authentication-from-android-devices-fail-if-the-server-does-not-send-all-the-intermediate-certificates-in-the-chain-with-the-ssl-cert"></a>如果服务器未发送与 SSL 证书链中的所有中间证书，Android 设备的新式验证为何会失败？

对于使用 Android ADAL 库失败的应用，联合用户可能会遇到 Azure AD 身份验证。 应用尝试显示登录页面时，会收到 AuthenticationException。 在 Chrome 中，AD FS 登录页面可能被称为“不安全”。

Android（适用于所有版本和所有设备）不支持从证书的 authorityInformationAccess 字段中下载其他证书。 Chrome 浏览器也是如此。 如果未从 AD FS 传递整个证书链，任何缺少中间证书的服务器身份验证证书都将导致此错误。

解决此问题的一种恰当解决方案是将 AD FS 和 WAP 服务器配置为发送必要的中间证书以及 SSL 证书。

从一台计算机导出 SSL 证书，并将其导入到 AD FS 和 WAP 服务器的计算机个人存储中时，请确保导出私钥，并选择“个人信息交换 - PKCS #12”。

重要的是，应选中“在证书路径中包含所有证书(如果可能)”和“导出所有扩展属性”复选框 。

在 Windows 服务器上运行 certlm.msc，然后将 *.PFX 导入到计算机的个人证书存储中。 这将导致服务器将整个证书链传递到 ADAL 库。

>[!NOTE]
> 还应更新网络负载均衡器的证书存储，使其包含整个证书链（如果存在）

### <a name="does-ad-fs-support-head-requests"></a>AD FS 是否支持 HEAD 请求？
AD FS 不支持 HEAD 请求。  应用程序不应对 AD FS 终结点使用 HEAD 请求。  这可能会导致意外和/或延迟的 HTTP 错误响应。  此外，你可能会在 AD FS 事件日志中看到意外错误事件。

### <a name="why-am-i-not-seeing-a-refresh-token-when-i-am-logging-in-with-a-remote-idp"></a>为什么在使用远程 IdP 登录时看不到刷新令牌？
如果 IdP 颁发的令牌的有效时间少于 1 小时，则不会颁发刷新令牌。 若要确保颁发刷新令牌，请将 IdP 颁发的令牌的有效时间提高到 1 小时以上。

### <a name="do-we-have-any-way-to-change-rp-token-encryption-algorithm"></a>是否可以通过一些方法更改 RP 令牌加密算法？
默认情况下，RP 令牌加密设置为 AES256，并且你无法将其更改为其他任何值。

### <a name="on-a-mixed-mode-farm-i-get-error-when-trying-to-set-the-new-ssl-certificate-using-set-adfssslcertificate--thumbprint-how-can-i-update-the-ssl-certificate-in-a-mixed-mode-ad-fs-farm"></a>在混合模式场中，尝试使用 Set-AdfsSslCertificate -Thumbprint 设置新的 SSL 证书时出现错误。 如何在混合模式 AD FS 场中更新 SSL 证书？
混合模式 AD FS 场应为过渡状态。 建议在计划期间，要么在升级过程之前滚动 SSL 证书，要么在更新 SSL 证书之前完成过程并提高器场行为级别。 如果未完成此操作，则以下说明提供了更新 SSL 证书的功能。

在 WAP 服务器上，仍可以使用 Set-WebApplicationProxySslCertificate。 在 ADFS 服务器上，需要使用 netsh。 按照下面提供的步骤操作：

1. 选择用于维护的 ADFS 2016 服务器子集（例如从负载均衡器中删除）
2. 在 #1 中选择的服务器上，通过 MMC 导入新证书
3. 删除现有证书

    a. netsh http delete sslcert hostnameport=fs.contoso.com:443 b. netsh http delete sslcert hostnameport=localhost:443 c. netsh http delete sslcert hostnameport=fs.contoso.com:49443

4.  添加新证书

    a. netsh http add sslcert hostnameport=fs.contoso.com:443 certhash=CERTTHUMBPRINT appid={5d89a20c-beab-4389-9447-324788eb944a} certstorename=MY sslctlstorename=AdfsTrustedDevices

    b. netsh http add sslcert hostnameport=localhost:443 certhash=CERTTHUMBPRINT appid={5d89a20c-beab-4389-9447-324788eb944a} certstorename=MY sslctlstorename=AdfsTrustedDevices

    c. netsh http add sslcert hostnameport=fs.contoso.com:49443 certhash=CERTTHUMBPRINT appid={5d89a20c-beab-4389-9447-324788eb944a} certstorename=MY sslctlstorename=AdfsTrustedDevices

5. 在所选的服务器上重启 ADFS 服务
6. 删除用于维护的 WAP 服务器子集
7. 在所选的 WAP 服务器上，通过 MMC 导入新证书
8. 使用 cmdlet 在 WAP 上设置新证书

    a. Set-WebApplicationProxySslCertificate -Thumbprint " CERTTHUMBPRINT"

9. 在所选的 WAP 服务器上重启服务
10. 将所选的 WAP 和 AD FS 服务器放回到生产环境中。

以类似的方式在其余 AD FS 和 WAP 服务器上执行更新。

### <a name="is-adfs-supported-when-web-application-proxy-wap-servers-are-behind-azure-web-application-firewallwaf"></a>当 Web 应用程序代理 (WAP) 服务器位于 Azure Web 应用程序防火墙 (WAF) 之后时，是否支持 ADFS？
ADFS 和 Web 应用程序服务器支持不在终结点上执行 SSL 终止的任何防火墙。 此外，ADFS/WAP 服务器使用内置机制来防止常见的 Web 攻击（例如跨站点脚本、ADFS 代理），并满足 [MS-ADFSPIP 协议](/openspecs/windows_protocols/ms-adfspip/76deccb1-1429-4c80-8349-d38e61da5cbb)定义的所有要求。

### <a name="i-am-seeing-an-event-441-a-token-with-a-bad-token-binding-key-was-found-what-should-i-do-to-resolve-this"></a>我看到了“事件 441: 找到了具有错误令牌绑定密钥的令牌。” 我应该怎么做才能解决这个问题？
在 AD FS 2016 中，令牌绑定会自动启用，并引发代理和联合身份验证方案的多个已知问题，从而导致此错误。 若要解决此问题，请运行以下 Powershell 命令，并删除令牌绑定支持。

`Set-AdfsProperties -IgnoreTokenBinding $true`

### <a name="i-have-upgraded-my-farm-from-ad-fs-in-windows-server-2016-to-ad-fs-in-windows-server-2019-the-farm-behavior-level-for-the-ad-fs-farm-has-been-successfully-raised-to-2019-but-the-web-application-proxy-configuration-is-still-displayed-as-windows-server-2016"></a>我已将场从 Windows Server 2016 中的 AD FS 升级到 Windows Server 2019 中的 AD FS。 AD FS 场的场行为级别已成功升级到 2019，但 Web 应用程序代理配置仍显示为 Windows Server 2016？
升级到 Windows Server 2019 后，Web 应用程序代理的配置版本将继续显示为 Windows Server 2016。 Web 应用程序代理没有适用于 Windows Server 2019 的新版本特定功能，如果在 AD FS 上成功升级了场行为级别，则 Web 应用程序代理将继续根据设计显示为 Windows Server 2016。

### <a name="can-i-estimate-the-size-of-the-adfsartifactstore-before-enabling-esl"></a>在启用 ESL 之前，是否可以估算 ADFSArtifactStore 的大小？
启用 ESL 后，AD FS 会跟踪 ADFSArtifactStore 数据库中用户的帐户活动和已知位置。 此数据库相对于所跟踪的用户数和已知位置进行缩放。 当计划启用 ESL 时，你可以估算 ADFSArtifactStore 数据库的大小，以每 100,000 个用户最多 1GB 的速率增长。 如果 AD FS 场使用 Windows 内部数据库 (WID)，则数据库文件的默认位置为 C:\Windows\WID\Data。 若要防止填充此驱动器，请在启用 ESL 之前确保至少有 5GB 的可用存储空间。 除了磁盘存储，还应在启用 ESL 后为 500,000 及以下的用户群体增加最多 1GB 的RAM，从而计划增加总进程内存。

### <a name="i-am-seeing-event-570-active-directory-trust-enumeration-was-unable-to-enumerate-one-of-more-domains-due-to-the-following-error-enumeration-will-continue-but-the-active-directory-identifier-list-may-not-be-correct-validate-that-all-expected-active-directory-identifiers-are-present-by-running-get-adfsdirectoryproperties-on-ad-fs-2019-what-is-the-mitigation-for-this-event"></a>我在 AD FS 2019 上看到事件 570（Active Directory 信任枚举由于以下错误而无法枚举一个或多个域。 枚举将继续，但 Active Directory 标识符列表可能不正确。 通过运行 Get-ADFSDirectoryProperties，验证所有预期的 Active Directory 标识符是否都存在）。 此事件的缓解措施是什么？
当 AD FS 尝试枚举受信任林链中的所有林并跨所有林连接时，如果林不受信任，就会发生此事件。 例如，如果 AD FS 林 A 和林 B 受信任，且林 B 和林 C 受信任，那么 AD FS 会枚举所有这三个林，并尝试查找林 A 和 C 之间的信任。如果出现故障的林中的用户应通过 AD FS 进行身份验证，请在 AD FS 林和出现故障的林之间建立信任。 如果出现故障的林中的用户不得通过 AD FS 进行身份验证，应忽略此错误。

### <a name="i-am-seeing-an-event-id-364-microsoftidentityserverauthenticationfailedexception-msis5015-authentication-of-the-presented-token-failed-token-binding-claim-in-token-must-match-the-binding-provided-by-the-channel-what-should-i-do-to-resolve-this"></a>我看到“事件 ID 364:Microsoft.IdentityServer.AuthenticationFailedException:MSIS5015:当前令牌的身份验证失败。 令牌中的令牌绑定声明必须与通道提供的绑定一致。” 我应该怎么做才能解决这个问题？
在 AD FS 2016 中，令牌绑定会自动启用，并引发代理和联合身份验证方案的多个已知问题，从而导致此错误。 若要解决此问题，请运行以下 Powershell 命令，并删除令牌绑定支持。

`Set-AdfsProperties -IgnoreTokenBinding $true`
